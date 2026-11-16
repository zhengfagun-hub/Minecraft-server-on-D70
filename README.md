# Minecraft-server-on-D70
Ich möchte hier der Aufbau meines Minecraft-Server zeigen.Viele Menschen haben versucht,einen Server in VLAN zu bauen.Der Aufbau des Server ist nicht sehr kompliziert,aber es gibt ein schwer Punkte in der Netzwerksverwaltung.Wie kann man in anderen VLANs der Server erreichen?
Soviel ich weiß,gibt es drei Lösungen.Sie sind VPN,öffentliche Adresse und externer TCP-Port.Ich nutze externer TCP-Port,weil meine Freude VPN kompliziert finden und öffentliche Adresse zusätzliche Kosten entstehen könnte.
Zuerst schauen Sie die Umgebung.Ich habe ein D70-Computer als Proxmox-VE-Host,Debian 13 aks virtuelle Maschine,macOS als Backup-Client.
Wenn ich Debian 13 in einer virtuellen Maschine installiere,gebe ich den virtuellen Maschine 4 Cores,8.00GiB RAM und 32GB SSD.Ich finde es genug,einen kleinen Server zu laufen.
Dann muss ich der IP-Adresse des Server festlegen,weil der DHCP Server jeder IP-Adresse ändern wird.Wenn der externer TCP-Port der innere IP-Adresse eines Server nicht finden kann,wird der Server nicht erreichbar sein.
Ich möchte die neueste Edition spielen,deshalb installiere ich Java 25 in der Server.Danach habe ich das Dienskonto minerraft und das Serververzeichnis /srv/minecraft angelegt.Anschließend habe ich den Eigentümer und die Zugriffsrechte festgelegt, damit der Server unter diesem Konto ausgeführt werden kann.
Das Serververzeichnis enthält paper.jar,server.properties,eula.txt und world folder.Als ich mit lokalem TCP-Port der Server erreichen kann,mache ich den lokalen Port über einen öffentlich zugänglich machen.Zuerst nutze ich playit.gg,aber der Ping war zu hoch,deshalb habe ich mit ChmlFrp einen TCP-Tunnel eingerichtet,der Verbindungen vom öffentlichen Port 39500 an den lokalen Port 25565 weiterleitet.
Für den Testbetrieb habe ich die Whitelist und die Online-Authentifizierung deaktiviert.
Am Ende wechsle ich world Folder ab.
Das ist alles,was ich mit diesem Projekt gemacht habe.Ich hoffe meine Erfahrung bei Ihnen helfen kann.