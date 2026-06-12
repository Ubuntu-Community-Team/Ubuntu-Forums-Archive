---
title: "Logkeys keymap messed up"
date: 2010-06-15
forum: General Help
---

### Post by Adrenochrom3 on 2010-06-15
ugh i installed Logkeys on to my: Dell Studio 1555 laptop, which runs ubuntu 10.04 lucid lynx. and for some reason when i start logging, the letters will be wrong and i cant read whats being recorded. therefore, the keymap must be screwed up. how do i go about fixing this problem. i would love to get this thing working right.

---

### Post by Adrenochrom3 on 2010-06-15
heres what i downloaded and installed. it works great, except for the major problem of the keymap not being right

[http://code.google.com/p/logkeys/](http://code.google.com/p/logkeys/)

---

### Post by Adrenochrom3 on 2010-06-15
can any one give me a little help please?

---

### Post by wildman4god on 2010-06-15
Linux apps should use the global key-map, if this app isn't working, try going into its configuration/preferences to see if it has it's own key-map settings, otherwise its a bug that needs to be filed.

if not sure about preferences options, post a screenshot of the preferences dialog

---

### Post by liquider on 2010-06-17
What (language) keyboard layout are you using? There are a couple of [pre-made logkeys keymaps](http://code.google.com/p/logkeys/wiki/Keymaps#Download) on their site, and if you are using a US keyboard, you should probably use -u switch to run the program.

Also, there's some information on [how to modify the keymaps manually](http://code.google.com/p/logkeys/wiki/Documentation#Logkeys_outputs_wrong_characters). Doesn't it help?

---

### Post by aguilera2k on 2010-08-06
Proceed with 
$ tar xvzf logkeys-0.1.1a.tar.gz     <<<# to extract the logkeys
 
$ cd logkeys-0.1.1a/build    
$ ../configure               
$ make                       
( become superuser now )     
$ make install               
**Running for US keyboards **
$ logkeys --start --us-keymap 
**Autorun at system start **
$ sudo gedit /etc/init.d/logkeys-start 
**Paste this in there **
#!/bin/bash 
sudo logkeys --start --us-keymap 
**and save it **
**Run this **
$ sudo su 
$ cd 
$ cd /etc/init.d/ 
$ update-rc.d logkeys-start defaults 
$ chmod +x /etc/init.d/logkeys-start 
**reboot That's it **
The log file will be the one that is at  
$ sudo nano /var/log/logkeys.log

---

