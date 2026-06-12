---
title: "otrs intallation problems"
date: 2010-01-05
forum: General Help
---

### Post by sisqonrw on 2010-01-05
hi,

i wanted to install otrs2 and get this error report:

> sudo apt-get install otrs2
Paketlisten werden gelesen... Fertig                
Abhängigkeitsbaum wird aufgebaut                    
Lese Status-Informationen ein... Fertig             
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libpurple0 libsilc-1.1-2 python-gtksourceview2 gedit-common libgtksourceview2.0-common libgtksourceview2.0-0 python-vte libvte9 apturl
  software-properties-gtk synaptic libvte-common                                                                                        
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.                                                                                
Vorgeschlagene Pakete:                                                                                                                  
  otrs2-doc-en otrs2-doc-de                                                                                                             
Die folgenden NEUEN Pakete werden installiert:                                                                                          
  otrs2                                                                                                                                 
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.                                                             
Es müssen 2.513kB an Archiven heruntergeladen werden.                                                                                   
Nach dieser Operation werden 16,1MB Plattenplatz zusätzlich benutzt.                                                                    
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe otrs2 2.3.4-1 [2.513kB]                                                             
Es wurden 2.513kB in 2s geholt (1.249kB/s)                                                                                              
Vorkonfiguration der Pakete ...                                                                                                         
/tmp/otrs2.config.290481: 50: /usr/share/otrs/bin/otrs.getConfig: not found                                                             
/tmp/otrs2.config.290481: 50: /usr/share/otrs/bin/otrs.getConfig: not found                                                             
/tmp/otrs2.config.290481: 50: /usr/share/otrs/bin/otrs.getConfig: not found                                                             
Wähle vormals abgewähltes Paket otrs2.                                                                                                  
(Lese Datenbank ... 354894 Dateien und Verzeichnisse sind derzeit installiert.)                                                         
Entpacke otrs2 (aus .../archives/otrs2_2.3.4-1_all.deb) ...                                                                             
Warnung: Auf das angegebene Benutzerverzeichnis /usr/share/otrs kann nicht zugegriffen werden: No such file or directory                
Der Systembenutzer »otrs« existiert bereits. Abbruch.                                                                                   
Verarbeite Trigger für ureadahead ...                                                                                                   
Richte otrs2 ein (2.3.4-1) ...                                                                                                          
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm                                                       
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm                                                        
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm                                                       
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm                                                        
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm                                                       
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm                                                        
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf                                                                      
Replacing config file /etc/otrs/database.pm with new version                                                                            
Module perl already enabled                                                                                                             
Module rewrite already enabled                                                                                                          
 * Reloading web server config apache2                                                                                                              ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm
DBI connect('dbname=otrs;host=localhost;port=5432;','otrs',...) failed: fe_sendauth: no password supplied at /usr/share/otrs/Kernel/System/DB.pm line 216
ERROR: OTRS-otrs.RebuildConfig.pl-10 Perl: 5.10.0 OS: linux Time: Tue Jan  5 09:37:21 2010

 Message: fe_sendauth: no password supplied

 Traceback (30111):
   Module: Kernel::System::DB::new (v1.95) Line: 190
   Module: /usr/share/otrs/bin/otrs.RebuildConfig.pl (v1.8) Line: 53

Got no DBObject! at /usr/share/otrs/Kernel/System/Config.pm line 84.
dpkg: Fehler beim Bearbeiten von otrs2 (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 255 zurück
Fehler traten auf beim Bearbeiten von:
 otrs2

where is the problem? What can i do?

---

