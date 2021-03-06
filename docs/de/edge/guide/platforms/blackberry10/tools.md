---

license: Licensed to the Apache Software Foundation (ASF) under one or more contributor license agreements. See the NOTICE file distributed with this work for additional information regarding copyright ownership. The ASF licenses this file to you under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

           http://www.apache.org/licenses/LICENSE-2.0
    
         Unless required by applicable law or agreed to in writing,
         software distributed under the License is distributed on an
         "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
         KIND, either express or implied.  See the License for the
         specific language governing permissions and limitations
    

   under the License.
---

# BlackBerry 10-Befehlszeilentools

Die `cordova` Befehlszeilen-Dienstprogramm ist ein High-Level Tool, das Ihnen erlaubt, Anwendungen auf mehreren Plattformen gleichzeitig zu erstellen. Eine ältere Version von Cordova Rahmen bietet Gruppen von Befehlszeilentools, die spezifisch für jede Plattform. Wenn sie als Alternative zu den CLI verwenden möchten, müssen Sie diese Version von Cordova von [cordova.apache.org][1]herunterladen. Der Download enthält separate Archiv für jede Plattform. Erweitern Sie die gewünschte Ziel-Plattform. Die hier beschriebenen Tools sind in der Regel in der obersten Ebene `bin` Verzeichnis, sonst finden Sie in die **README** -Datei ausführlichere Wegbeschreibung.

 [1]: http://cordova.apache.org

Wenn Sie Hilfe mit jeder nachfolgenden Befehl benötigen, geben Sie den Befehl zusammen mit der `-h` oder `-help` Argumente, die unterstützt werden, indem alle Befehle und die Beschreibungen für die einzelnen verfügbaren Argumente liefern.

## Erstellen

Der `create` Befehl erstellt ein neues Projekt:

    bin/Erstellen von < Pfad-zu-Projekt >< Projektpaket >< Projekt-Name >
    

wo

*   `<path-to-project>`Gibt das Verzeichnis des Projekts gegründet

*   `<project-package>`Gibt einen reverse Domain-Stil-Bezeichner

*   `<project-name>`Gibt den Anzeigenamen apps

**Hinweis:** die `create` Befehl Bootstrap Abhängigkeit Installation über den `npm install` Befehl. Je nach der Installation Directory und System Berechtigungen kann das Administratorrechte erforderlich. Wenn auf OSX/Linux Problem vorhanden ist, führen Sie `sudo npm install` vor der Verwendung der `create` Befehl. Führen Sie unter Windows `npm install` eröffnet ein Befehlszeilen-Dienstprogramm mit Administratorrechten.

## Ziel

Die `target` mit dem Befehl können Sie verwalten den Emulator oder BlackBerry-Geräte, mit denen Sie Ihre Anwendung testen. Sie können hinzufügen oder entfernen ein Ziel oder ein Ziel gesetzt, als Standardziel.

### Fügen Sie ein Ziel

    < Path-Projekt >/Cordova/Ziel hinzufügen <name> < Ip-Adresse > [-t |--Typ < Gerät | Simulator >] [-p |--Kennwort <password>] [--polig < Gerät-polig >]
    

wo

*   `<name>`Gibt einen eindeutigen Namen für das Ziel.

*   `<ip-address>`Gibt die Ip-Adresse des BlackBerry-Geräts oder Simulator.

*   `-p | --password <password>`Gibt das Kennwort für das Gerät oder den Emulator. Dies ist erforderlich, nur, wenn das Gerät oder den Emulator kennwortgeschützt ist.

*   `--pin <device-pin>`Gibt die PIN für das BlackBerry-Gerät, das dieses Gerät als gültige Host für die Debug-Token identifiziert. Dieses Argument ist erforderlich, nur, wenn Sie ein Debug-Token erstellen.

### Entfernen Sie ein Ziel

    < Path-Projekt >/Cordova/Ziel entfernen <name>
    

### Ein Ziel als Standard festlegen

    < Path-Projekt >/Cordova/target Standard <name>
    

## Build

Der `build` Befehl erstellt das Projekt als ...verlegt Datei. Sie können Ihre app in beiden Release-Modus (der eine signierte ...verlegt Datei erzeugt) oder im Debug-Modus (der eine vorzeichenlose ...verlegt Datei erzeugt) erstellen.

### Erstellen Sie das Projekt im Release-Modus

    < Path-Projekt >/Cordova/Release build [-k |--Keystorepass <password>] [-b |--BuildId <number>] [-p |--Params < Params-JSON-Datei >]
    

wo

*   `-k | --keystorepass <password>`Gibt das Kennwort, die, das Sie definiert, wenn Sie Ihren Computer zum Signieren von Anwendungen konfiguriert.

*   `-b | --buildId <number>`Gibt die Build-Versionsnummer der Anwendung. In der Regel sollte diese Zahl signierte der Vorgängerversion erhöht werden. Dieses Argument ist optional.

*   `-p | --params <params-JSON-file>`gibt eine JSON-Datei, die mit zusätzlichen Parameter zur Übergabe an nachgelagerte Werkzeuge. Dieses Argument ist optional.

### Erstellen Sie das Projekt im Debugmodus

    < Path-Projekt >/Cordova/build Debug [<target>] [-k |--Keystorepass <password>] [-p |--Params < Params-JSON-Datei >] [-ll |--Loglevel <error|warn|verbose>]
    

wo

*   `<target>`Gibt den Namen eines zuvor hinzugefügten Ziels. Wenn `<target>` nicht angegeben ist, das Standardziel wird verwendet, wenn eine erstellt wurde. Dieses Argument ist nur erforderlich, wenn Sie das Skript zum Bereitstellen Ihrer Anwendung auf einem BlackBerry-Gerät oder Emulator, in dem Sie als Standardziel nicht erstellt haben. Zusätzlich, wenn `<target>` ist ein Gerät, dann das Gerät vom USB-Anschluss an den Computer angeschlossen werden oder mit dem gleichen Wi-Fi-Netzwerk wie Ihr Computer angeschlossen werden.

*   `-k | --keystorepass <password>`Gibt das Kennwort, die, das Sie definiert, wenn Sie Ihren Computer zum Signieren von Anwendungen konfiguriert. Dieses Kennwort wird auch verwendet, um das Debug-Token zu erstellen. Dieses Argument ist nur erforderlich, wenn Sie wollen das Skript zum Erstellen und installieren das Debug-Token für Sie.

*   `-p | --params <params-JSON-file>`gibt eine JSON-Datei, die mit zusätzlichen Parameter zur Übergabe an nachgelagerte Werkzeuge.

*   `-ll | --loglevel <level>`Gibt die Protokollebene. Die Protokollebene möglicherweise einer der `error` , `warn` , oder`verbose`.

Wenn Sie zuvor definiert als Standardziel (und zuvor installiert haben ein Debug-Token, wenn das Ziel ein BlackBerry-Gerät ist), führen Sie das Skript ohne Argumente und das Skript wird Ihre app-Paket und auf das Standardziel bereitstellen. Zum Beispiel:

    < Path-Projekt >/Cordova/build debug
    

## Ausführen

Der `run` Befehl stellt die app auf dem BlackBerry-Gerät oder einen Emulator. Bevor Sie Ihre Anwendung bereitstellen, müssen Sie zunächst ein Ziel für das Gerät oder den Emulator Ihre Anwendung bereitgestellt, mit dem Ziel-Skript soll erstellen. Das Bereitstellen-Skript wird das letzte Build Ihrer Anwendung bereitstellen.

    < Path-Projekt >/Cordova/run <target>
    

wo

*   `<target>`Gibt den Namen eines zuvor hinzugefügten Ziels. Wenn `<target>` ist ein Gerät, dann das Gerät vom USB-Anschluss an den Computer angeschlossen werden oder mit dem gleichen Wi-Fi-Netzwerk wie Ihr Computer angeschlossen werden.

## Plugin

Der `target` Befehl können Sie hinzufügen und Entfernen von Plugins

### Eine lokal gehostete Plugin zu holen

    < Path-Projekt >/Cordova/Plugin Fetch < Pfad-zu-Plugin >
    

### Anzeigen einer Liste der installierten plugins

    < Path-Projekt >/Cordova/Plugin ls
    

### Eine Plugin hinzufügen

    < Path-Projekt >/Cordova/Plugin hinzufügen <name>
    

### Eine Plugin zu entfernen

    < Path-Projekt >/Cordova/Plugin Rm <name>