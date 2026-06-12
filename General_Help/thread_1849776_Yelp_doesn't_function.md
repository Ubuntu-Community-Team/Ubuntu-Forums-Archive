---
title: "Yelp doesn't function"
date: 2011-09-25
forum: General Help
---

### Post by semsaudade on 2011-09-25
Hi to everybody. I have recently noticed that in my Asus eeePc with Ubuntu Netbook Edition 10.04.02 yelp is not working anymore. If I start the guide (from terminal or clicking on ? icon), it opens and then closes again immediatly.

Here is the result from terminal:

```
$ yelp

(yelp:1726): Gtk-CRITICAL **: gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:1726): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:1726): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:1726): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(yelp:1726): Gtk-CRITICAL **: gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:1726): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:1726): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:1726): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed
Errore di segmentazione
```

Thanks a lot for your help!
Giancarlo

---

### Post by dino99 on 2011-09-25
yelp does its job: its inform you :) that dont mean it has to be blamed.

are you using non genuine repo/package(s) like ppa ?

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a

---

### Post by semsaudade on 2011-09-25
Thanks for your kind answer. I followed your suggestion but no luck: yelp continues not starting and there were many error messages.

If you have the time to read i, here is what I got:

```
giancarlo@giancarlo-laptop:~$ sudo apt-get-update 
[sudo] password for giancarlo: 
sudo: apt-get-update: command not found 
giancarlo@giancarlo-laptop:~$ sudo apt-get update 
Trovato http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/me-tv-development/ppa/ubuntu/ lucid/main Translation-it 
Trovato http://ppa.launchpad.net lucid Release.gpg  
Trovato http://archive.ubuntu.com lucid Release.gpg  
Trovato http://archive.ubuntu.com/ubuntu/ lucid/main Translation-it 
Trovato http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-it 
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-it 
Trovato http://ppa.launchpad.net lucid Release       
Trovato http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-it 
Trovato http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-it 
Scaricare:1 http://archive.ubuntu.com lucid-updates Release.gpg [198B] 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-it 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-it 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-it 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-it 
Trovato http://ppa.launchpad.net lucid Release                             
Scaricare:2 http://archive.ubuntu.com lucid-security Release.gpg [198B]    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-it 
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-it 
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-it 
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-it 
Scaricare:3 http://archive.ubuntu.com lucid-proposed Release.gpg [198B] 
Trovato http://archive.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-it 
Trovato http://archive.ubuntu.com/ubuntu/ lucid-proposed/main Translation-it 
Trovato http://archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-it 
Trovato http://archive.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-it 
Trovato http://ppa.launchpad.net lucid/main Packages 
Trovato http://archive.ubuntu.com lucid Release      
Scaricare:4 http://archive.ubuntu.com lucid-updates Release [44,7kB]       
Trovato http://ppa.launchpad.net lucid/main Packages                         
Scaricare:5 http://archive.ubuntu.com lucid-security Release [44,7kB]        
Scaricare:6 http://archive.ubuntu.com lucid-proposed Release [44,7kB] 
Trovato http://archive.ubuntu.com lucid/main Packages 
Trovato http://archive.ubuntu.com lucid/restricted Packages 
Trovato http://archive.ubuntu.com lucid/main Sources 
Trovato http://archive.ubuntu.com lucid/restricted Sources 
Trovato http://archive.ubuntu.com lucid/universe Packages 
Trovato http://archive.ubuntu.com lucid/universe Sources 
Trovato http://archive.ubuntu.com lucid/multiverse Packages 
Trovato http://archive.ubuntu.com lucid/multiverse Sources 
Scaricare:7 http://archive.ubuntu.com lucid-updates/main Packages [513kB] 
Scaricare:8 http://archive.ubuntu.com lucid-updates/restricted Packages [3240B] 
Scaricare:9 http://archive.ubuntu.com lucid-updates/main Sources [201kB] 
Scaricare:10 http://archive.ubuntu.com lucid-updates/restricted Sources [1443B] 
Scaricare:11 http://archive.ubuntu.com lucid-updates/universe Packages [225kB] 
Scaricare:12 http://archive.ubuntu.com lucid-updates/universe Sources [80,4kB] 
Scaricare:13 http://archive.ubuntu.com lucid-updates/multiverse Packages [10,5kB] 
Scaricare:14 http://archive.ubuntu.com lucid-updates/multiverse Sources [5070B] 
Scaricare:15 http://archive.ubuntu.com lucid-security/main Packages [206kB] 
Scaricare:16 http://archive.ubuntu.com lucid-security/restricted Packages [14B] 
Scaricare:17 http://archive.ubuntu.com lucid-security/main Sources [63,2kB] 
Scaricare:18 http://archive.ubuntu.com lucid-security/restricted Sources [14B] 
Scaricare:19 http://archive.ubuntu.com lucid-security/universe Packages [83,2kB] 
Scaricare:20 http://archive.ubuntu.com lucid-security/universe Sources [25,8kB] 
Scaricare:21 http://archive.ubuntu.com lucid-security/multiverse Packages [4559B] 
Scaricare:22 http://archive.ubuntu.com lucid-security/multiverse Sources [1751B] 
Scaricare:23 http://archive.ubuntu.com lucid-proposed/restricted Packages [14B] 
Scaricare:24 http://archive.ubuntu.com lucid-proposed/main Packages [132kB] 
Scaricare:25 http://archive.ubuntu.com lucid-proposed/multiverse Packages [14B] 
Scaricare:26 http://archive.ubuntu.com lucid-proposed/universe Packages [21,7kB] 
Recuperati 1712kB in 6s (259kB/s)                                                                                           
Lettura elenco dei pacchetti... Fatto 
giancarlo@giancarlo-laptop:~$ sudo apt-get install -f 
Lettura elenco dei pacchetti... Fatto 
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto 
0 aggiornati, 0 installati, 0 da rimuovere e 27 non aggiornati. 
giancarlo@giancarlo-laptop:~$ sudo dpkg-reconfigure -phigh -a 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information 
update-rc.d: see <http://wiki.debian.org/LSBInitScripts> 
acpid stop/waiting 
acpid start/running, process 1827 
 * Stopping web server apache2                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName 
 ... waiting                                                                                                          [ OK ] 
 * Starting web server apache2                                                                                               apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName 
                                                                                                                      [ OK ] 
 * Starting AppArmor profiles                                                                                                Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
                                                                                                                      [ OK ] 
 * Reloading AppArmor profiles                                                                                               Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
                                                                                                                      [ OK ] 
stop: Unknown instance: 
start: Job failed to start 
Unknown media type in type 'all/all' 

Unknown media type in type 'all/allfiles' 

Unknown media type in type 'uri/mms' 

Unknown media type in type 'uri/mmst' 

Unknown media type in type 'uri/mmsu' 

Unknown media type in type 'uri/pnm' 

Unknown media type in type 'uri/rtspt' 

Unknown media type in type 'uri/rtspu' 

Unknown media type in type 'fonts/package' 

Unknown media type in type 'interface/x-winamp-skin' 

atd stop/waiting 
atd start/running, process 2237 
Unknown media type in type 'all/all' 

Unknown media type in type 'all/allfiles' 

Unknown media type in type 'uri/mms' 

Unknown media type in type 'uri/mmst' 

Unknown media type in type 'uri/mmsu' 

Unknown media type in type 'uri/pnm' 

Unknown media type in type 'uri/rtspt' 

Unknown media type in type 'uri/rtspu' 

Unknown media type in type 'fonts/package' 

Unknown media type in type 'interface/x-winamp-skin' 

avahi-daemon stop/waiting 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service dbus force-reload 

Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus 
avahi-daemon start/running, process 2311 
update-alternatives: viene usato /usr/share/man/man7/bash-builtins.7.gz per fornire /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in modalità automatica. 
 * Disabling additional executable binary formats binfmt-support                                                      [ OK ] 
update-binfmts: warning: current package is mono-runtime , but binary format 
already installed by mono-common 
update-binfmts: warning: current package is openjdk-6, but binary format 
already installed by sun-java6 
 * Enabling additional executable binary formats binfmt-support                                                       [ OK ] 
Unknown media type in type 'all/all' 

Unknown media type in type 'all/allfiles' 

Unknown media type in type 'uri/mms' 
 
Unknown media type in type 'uri/mmst' 

Unknown media type in type 'uri/mmsu' 

Unknown media type in type 'uri/pnm' 

Unknown media type in type 'uri/rtspt' 

Unknown media type in type 'uri/rtspu' 

Unknown media type in type 'fonts/package' 

Unknown media type in type 'interface/x-winamp-skin' 

Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service dbus force-reload 

Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service udev reload 

Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the reload(8) utility, e.g. reload udev 
Unknown media type in type 'all/all' 

Unknown media type in type 'all/allfiles' 

Unknown media type in type 'uri/mms' 

Unknown media type in type 'uri/mmst' 

Unknown media type in type 'uri/mmsu' 

Unknown media type in type 'uri/pnm' 

Unknown media type in type 'uri/rtspt' 

Unknown media type in type 'uri/rtspu' 

Unknown media type in type 'fonts/package' 

Unknown media type in type 'interface/x-winamp-skin' 

update-initramfs: Generating /boot/initrd.img-2.6.32-34-generic 
update-alternatives: viene usato /usr/bin/bsd-write per fornire /usr/bin/write (write) in modalità automatica. 
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done. 
Running hooks in /etc/ca-certificates/update.d.... 
updating keystore /etc/ssl/certs/java/cacerts... 
done. 
done. 
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list) 
Unknown media type in type 'all/all' 

Unknown media type in type 'all/allfiles' 

Unknown media type in type 'uri/mms' 

Unknown media type in type 'uri/mmst' 

Unknown media type in type 'uri/mmsu' 

Unknown media type in type 'uri/pnm' 

Unknown media type in type 'uri/rtspt' 

Unknown media type in type 'uri/rtspu' 

Unknown media type in type 'fonts/package' 

Unknown media type in type 'interface/x-winamp-skin' 

WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list) 
Unknown media type in type 'all/all' 

Unknown media type in type 'all/allfiles' 

Unknown media type in type 'uri/mms' 

Unknown media type in type 'uri/mmst' 

Unknown media type in type 'uri/mmsu' 

Unknown media type in type 'uri/pnm' 

Unknown media type in type 'uri/rtspt' 

Unknown media type in type 'uri/rtspu' 

Unknown media type in type 'fonts/package' 

Unknown media type in type 'interface/x-winamp-skin' 

Unknown media type in type 'all/all' 

Unknown media type in type 'all/allfiles' 
 
Unknown media type in type 'uri/mms' 

Unknown media type in type 'uri/mmst' 

Unknown media type in type 'uri/mmsu' 

Unknown media type in type 'uri/pnm' 

Unknown media type in type 'uri/rtspt' 

Unknown media type in type 'uri/rtspu' 

Unknown media type in type 'fonts/package' 

Unknown media type in type 'interface/x-winamp-skin' 

Your console font configuration will be updated the next time your system 
boots. If you want to update it now, run 'setupcon' from a virtual console. 
update-initramfs: Generating /boot/initrd.img-2.6.32-34-generic 
This is not dpkg install-info anymore, but GNU install-info 
See the man page for ginstall-info for command line arguments 
install-info: File di indice non specificato; usare «--help» per maggiori informazioni. 
giancarlo@giancarlo-laptop:~$ lsusb 

```

---

### Post by semsaudade on 2011-09-25
Did you notice that "Errore di segmentazione" (Segmentation Error) displayed at the end of my yelp comand? I believe this is an important error, isn't it?

---

### Post by gmargo on 2011-09-25
> **semsaudade said:**
> ```

0 aggiornati, 0 installati, 0 da rimuovere e [COLOR=Red]27 non aggiornati[/COLOR]. 

```

Doesn't that say 27 packages not upgraded?  You should do a "apt-get dist-upgrade" or "aptitude full-upgrade", then reboot, then try yelp again.

---

### Post by semsaudade on 2011-09-26
Thank for your help. I performed a aptitude full-upgrade on my pc as suggested, but problem remains. Same segmentation error as before on executing yelp.

Notice that help functions without any problem inside of single programs, but general help is not working (it doesn't load).

---

