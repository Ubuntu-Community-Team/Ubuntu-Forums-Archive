---
title: "Get rid off some files that don't wanna erase themselves"
date: 2011-01-27
forum: General Help
---

### Post by &gt;hankim&lt; on 2011-01-27
Hello, 
that's my problem, can't find a way to erase 2 files that apparently don't want to move to the rubish bin.. it says: *can't move the file to trash, wan't to erase it permanently? *I click on erase and the thing still there! could you please get me some commands?
and by the way, how do I find how to use the command line so I don't bother you all the time? would it take me a hole engineering carrer or something? any 'document' recommended?
thx, fairwell!

---

### Post by AlphaLexman on 2011-01-27
What are the filenames?
What directory are they in?
What is the output of ```
ls -la ../
```

---

### Post by &gt;hankim&lt; on 2011-01-27
edit: the properties tell me they are all unknown, but they used to be a  folder and a openoffice file i think, they are located in the desktop, I don''t quite know what I should do by:     ls -la ../   

$ ls -la ../
total 12
drwxr-xr-x  3 root root 4096 2010-04-23 12:11 .
drwxr-xr-x 22 root root 4096 2011-01-26 05:38 ..
drwxr-xr-x 53 han  han  4096 2011-01-27 20:02 han

is that?

---

### Post by AlphaLexman on 2011-01-27
You didn't actually answer my questions...
Please paste the output of this command:
```
ls -la ~/Desktop; ls -la ~/;
```
and let us know exactly which two files you are trying to delete | remove.

---

### Post by &gt;hankim&lt; on 2011-01-27
sorry man, I'm using spanish and it gives me no value...
ls -la ~/Escritorio; ls -la ~/;

---

### Post by AlphaLexman on 2011-01-27
> **>hankim< said:**
> sorry man, I'm using spanish and it gives me no value...
ls -la ~/Escritorio; ls -la ~/;

Are those directories empty? What do you mean by 'no value'?

Even an empty directory will 'ls -la' dot and dotdot output.

Even if you think the information output is meaningless post it anyway. I'm looking for ownership problems within your directory structure.

---

### Post by &gt;hankim&lt; on 2011-01-27
actually It just retarded a bit...

han@han-laptop:~$ ls -la ~/escriptori; ls -la ~/;
ls: no se puede acceder a /home/han/escriptori: No existe el fichero o el directorio
total 69168
drwxr-xr-x 53 han  han      4096 2011-01-27 20:02 .
drwxr-xr-x  3 root root     4096 2010-04-23 12:11 ..
drwx------  3 han  han      4096 2010-09-20 23:18 .adobe
drwxr-xr-x  4 han  han      4096 2010-12-19 05:18 .audacity-data
-rw-------  1 han  han      3429 2011-01-26 21:39 .bash_history
-rw-r--r--  1 han  han       220 2010-09-19 02:10 .bash_logout
-rw-r--r--  1 han  han      3103 2010-09-19 02:10 .bashrc
drwx------ 16 han  han      4096 2011-01-27 17:34 .cache
drwx------  3 han  han      4096 2010-09-25 01:43 .compiz
-rwxrwxrwx  1 han  han      1213 2010-09-24 23:49 .com.zerog.registry.xml
drwxr-xr-x 25 han  han      4096 2011-01-27 18:16 .config
drwx------  3 han  han      4096 2010-09-19 02:13 .dbus
drwxr-xr-x  3 han  han      4096 2011-01-26 19:45 Descargas
-rw-r--r--  1 han  han        31 2011-01-27 17:34 .dmrc
drwxr-xr-x  2 han  han      4096 2011-01-24 18:04 Documentos
drwxr-xr-x  2 han  han      4096 2011-01-26 05:26 .elegant_gnome_backup
drwxr-xr-x 13 han  han      4096 2011-01-27 18:16 Escriptori
drwxr-xr-x  2 han  han      4096 2011-01-27 18:16 Escritorio
-rw-------  1 han  han        16 2010-09-19 02:13 .esd_auth
drwxr-xr-x  8 han  han      4096 2011-01-10 15:43 .evolution
-rw-r--r--  1 han  han       179 2010-09-19 02:10 examples.desktop
-rwxr-xr-x  1 han  han        60 2010-09-24 23:54 .flexlmrc
drwxr-xr-x  2 han  han      4096 2011-01-26 04:45 .fontconfig
drwx------  6 han  han      4096 2011-01-27 17:34 .gconf
drwx------  2 han  han      4096 2011-01-27 22:47 .gconfd
drwx------  4 han  han      4096 2010-10-27 20:26 .gegl-0.0
drwxr-xr-x 22 han  han      4096 2011-01-24 17:50 .gimp-2.6
-rw-r-----  1 han  han         0 2011-01-26 17:02 .gksu.lock
drwx------  3 han  han      4096 2010-12-04 18:36 .gnome
drwx------ 10 han  han      4096 2011-01-27 00:49 .gnome2
drwx------  2 han  han      4096 2010-09-19 02:14 .gnome2_private
drwx------  4 han  han      4096 2011-01-26 22:02 .googleearth
-rw-r--r--  1 root root 35050518 2011-01-26 17:29 googleearth_6.0.1.2032+0.5.7-1_i386.deb
-rw-r--r--  1 root root 33589497 2011-01-19 12:15 GoogleEarthLinux.bin
drwxr-xr-x  2 han  han      4096 2011-01-27 21:51 .gstreamer-0.10
-rw-r--r--  1 han  han       468 2011-01-27 18:16 .gtk-bookmarks
dr-x------  2 han  han         0 2011-01-27 17:34 .gvfs
-rw-------  1 han  han     42418 2011-01-27 17:34 .ICEauthority
drwxr-xr-x  2 han  han      4096 2010-09-19 03:31 .icons
drwxr-xr-x  4 han  han      4096 2010-10-18 13:36 Imágenes
drwx------  3 han  han      4096 2010-09-25 22:06 .kde
drwx------  3 han  han      4096 2011-01-09 01:42 .kompozer.net
drwx------  3 han  han      4096 2010-09-19 02:14 .local
drwx------  3 han  han      4096 2010-12-04 18:36 .loki
drwx------  3 han  han      4096 2010-09-20 23:18 .macromedia
drwxr-xr-x  3 han  han      4096 2010-09-24 23:54 .maple
drwxr-xr-x 19 han  han      4096 2010-09-24 23:49 maple13
drwx------  3 han  han      4096 2010-09-20 21:03 .mission-control
drwx------  4 han  han      4096 2010-09-20 20:36 .mozilla
drwxr-xr-x  2 han  han      4096 2010-09-19 02:13 Música
drwxr-xr-x  2 han  han      4096 2010-09-19 02:13 .nautilus
drwxr-xr-x  3 han  han      4096 2010-09-19 02:27 .openoffice.org
drwxr-xr-x  3 han  han      4096 2011-01-26 04:56 .orta
drwx------  2 han  han      4096 2011-01-24 04:07 PDF
drwxr-xr-x  2 han  han      4096 2011-01-27 17:36 Plantillas
-rw-r--r--  1 han  han        37 2010-11-06 20:58 .printer-groups.xml
-rw-r--r--  1 han  han       700 2011-01-26 19:51 .profile
drwxr-xr-x  2 han  han      4096 2011-01-27 17:36 Público
drwx------  2 han  han      4096 2011-01-27 17:34 .pulse
-rw-------  1 han  han       256 2010-09-19 02:13 .pulse-cookie
-rw-------  1 han  han    268649 2011-01-27 20:02 .recently-used.xbel
-rw-------  1 han  han   1356812 2011-01-26 23:13 Sense títol.ogg
drwx------  3 han  han      4096 2011-01-26 23:56 .Skype
-rw-r--r--  1 han  han         0 2010-09-20 20:39 .sudo_as_admin_successful
drwxr-xr-x  2 han  han      4096 2010-09-19 03:31 .themes
drwx------  5 han  han      4096 2010-09-29 12:45 .thumbnails
drwxrwxr-x  2 han  han      4096 2011-01-24 01:25 Ubuntu One
drwx------  2 han  han      4096 2011-01-24 05:53 .update-notifier
drwxr-xr-x  2 han  han      4096 2011-01-27 17:36 Videos
drwxr-xr-x  3 han  han      4096 2010-10-18 13:36 Vídeos
drwxr-xr-x  4 han  han      4096 2010-12-20 23:12 .wine
drwxr-xr-x  2 han  han      4096 2011-01-26 19:51 .xinput.d
-rw-------  1 han  han    232530 2011-01-27 22:47 .xsession-errors
-rw-------  1 han  han      4019 2011-01-27 00:49 .xsession-errors.old


there it goes

---

### Post by AlphaLexman on 2011-01-27
Which files are you trying to delete | remove ?

google-earth? if, yes use sudo.

EDIT: Linux is case-sensitive:
```
ls -la ~/**E**scriptori; ls -la ~/
```

---

### Post by &gt;hankim&lt; on 2011-01-27
would the command be: sudo rm -rf /home/han/Escritorio/Wget-log?

---

### Post by AlphaLexman on 2011-01-27
> **>hankim< said:**
> would the command be: sudo rm -rf /home/han/Escritorio/Wget-log?

That will work, but you really don't need the '-r' flag.

Is there another file | directory you need to erase?

---

