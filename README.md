# Das neue coole Datenprojekt?

_Made in Germany. Also schreib ich das ganze erst mal auf Deutsch runter :-D_  


# Motivation
Ein Daten-Framework nah an den Rohdaten und flexibel. Die Nummer 1 an die man denkt, wenn man Daten importieren, verarbeiten, speichern oder jederzeit exportieren möchte, die ggf. direkt an das eigene Unternehmen, einem Projekt oder privat personenbezogen sind.

Tatsächlich kommt Microsoft Access am nächsten an meine Vorstellungen ran. Aber Access ist schwierig und starr. Und es hat kein Rechtesystem, oder irre ich mich da? Und heute sollte es eh eine "Responsive Web-App" sein.


# Grundlegende Features

## Daten verwalten in völlig freier Form.
Die Daten liegen in einer graphbasierten Dokumenten-Datenabank. Damit sind viele Relationen ohne Joins direkt möglich. ArangoDB eignet sich dafür. Diese Datenbank wurde in C++ geschrieben und hat eine gute Python-Anbindung. Daten werden als JSON-Objekt bzw. dict übergeben.
Parallel werde ich MongoDB in Betracht ziehen und später mal direkt mit der Performance


## Rechtesystem
Addons in Wordpress reißen gerne Sicherheitslücken auf. Daher ist ein grundlegendes Rechtesystem als Basis eine gute Idee.
Jeder erzeugte oder importierte Datensatz bzw. Datengruppe gehört dem jeweiligen Benutzer und ist nur für ihn sichtbar, sofern er sie nicht freigibt.
Alle Datenebenen sollten in einer Baumstruktur eingeordnet sein. Und jeder Ast sollte per ALLOW/DENY-Ketten bestimmten Usern und Gruppen Zugriff gewähren oder explizit verbieten. In jeder Ansicht sollten die Benutzer und Gruppen angezeigt werden, die die jeweiligen Daten auch sehen können.

Externe Personen können per E-Mail eingeladen werden und einen Gast-Account anlegen. Oder anonym per Link, der ggf. auch abläuft. Der Verwalter ist letztendlich für die Datensicherheit verantwortlich.

## Transaktionen und Locks
Sobald daten zur Bearbeitung geöffnet werden, muss ein Lock auf Dokumentebene stattfinden. Das kann für andere dann ausgegraut angezeigt werden. Auf Wunsch können weitere Personen einen Parallelzugriff anfragen und zusammen bearbeiten. Geänderte Daten werden live an andere Personen verteilt.

## Backups
Daten im Browser sollten automatisch zwischengespeichert werden.

Jede Operation sollte auch in einem Journal erfasst werden und die Datenbank nach einem Crash per "Replay" wiederhergestellt werden können.

## Öffentliche Pakete für neue Funktionen
Vielleicht fängt man mit einem ToDo-System an und später fügt man vielleicht noch Lagerführung hinzu.  
Es sollte vorgefertigte Pakete geben, die man einbinden und aktivieren kann. Ganz modular, mit Konfigurationsmöglichkeiten, auch im Code anpassbar.

Im Grundpaket sind allgemeine Vorlagen vorhanden für einfache Datenanzeige und -manipulation. Z.B. eine tabellarische Eingabemaske. Auf alle Vorlagen sollte man aufbauen können. Erweitern oder verbessern.

Jedes Paket sollte Beispieldaten mitbringen, die sich per Klick importieren lassen.

Simpler Import per "git clone"-URL wäre mega.

## Ideen

CSV-Dump? Einfach per Drag&Drop hochladen und im nächsten Schritt verarbeiten. Dann mit einem Projekt verknüpfen.  

Dateien und Notizen direkt einpflegen und später weiter verarbeiten. Auch Automatisierung per Keywords.

nmap-Scan-Report? Hochladen und IP-Doku damit abgleichen.  

Im hintergrund kann ein Dienst regelmäßig Daten einsammeln gehen (scrapen etc.).

SNMP-Statistiken

Schnittstellen zu RRD und anderen Datenbanken

Automatische E-Mail-Korrespondenz über ein eigenes Postfach mit erkennung von Projekt-IDs im Betreff oder im Mail-Body.

Ansonsten die Klassiker:
- TODO-App
- Lagerhaltung
- Rechnung/Buchhaltung per LaTex in hübsche PDFs exportieren
- Kanban
- Prozesse erfassen und verfolgen
- Arbeitsstundenerfassung
- Vorausgefüllte Formular-PDFs erzeugen für einen Auftrag


## DDL
Datenstrukturen müssen klar und einfach definiert werden können. Einfacher als "CREATE TABLE". Mehrere Zeilen, Variablen, Kommentare, Metadaten. Alles in einfache Textdateien. Optional Python-Module, wenn komplexere Logik erforderlich ist.
Oder alles generell per einfach lesbaren Python-Code?

Datenmigration. Jede Tabelle/Collection hat einen Versionsstand und alte Strukturen können samt Daten aktualisiert werden. Dazu gibt es mehrere nummerierte Schichten in der DDL. Sequenziell können Daten dann auf den neuen Paketstand migriert werden.

Vielleicht sollten die Datenstrukturen auch visuell erzeugt werden können. Access kann das auch mit Tabellen, Feldern und Beziehungen.


## Komponenten
- Python, weil moderner als JavaScript, PHP und co. Viele Module verfügbar.
- ArangoDB und/oder MongoDB, wobei mir die Arango-Syntax schon erheblich besser gefällt. Arango unterstützt simple Dokumente und alle komplexeren Relatione bishin zu Sortierungen per Graphen. Keine Java-basierende DB!!!
- Flask, weil Django schon zu spezialisiert ist in Sachen Datenbanken. Eine Graph-Datenbank lässt sich besser in Flask integrieren.
- Bootstrap für schicke Oberflächen. Responsive, Themes und grundsätzlich zwei Views: Data-Design und Anwendung.


## Aktueller Status
Es muss noch alles weiter sacken, weiter durchgeplant werden und Beispiele konkret durchgespielt werden.  
Ich sehe da grßen Bedarf für so ein Projekt und ähnliche Projekte sind einfach zu starr und zu undurchsichtig, wenn man was anpassen möchte.
