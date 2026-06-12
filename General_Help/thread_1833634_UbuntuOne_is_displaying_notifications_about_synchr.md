---
title: "UbuntuOne is displaying notifications about synchronising the same file over and over"
date: 2011-08-26
forum: General Help
---

### Post by Bazon on 2011-08-26
Ubuntu One is displaying notifications about synchronising the same file(s) over and over and over again, although the file(s) ha(s/ve) not been changed.
I see this notification every time I start the system or resume from standby, and even while running the session the notification appears irregularly, but repeated.

 This is in particular bad when watching some video in fullscreen, because the notification is displayed anyway AND my Cairo(glx)-dock is brought to the front.


**So what can I do to get rid off these useless notifications?**

---

### Post by Bazon on 2011-08-26
"Ubuntu One
**filename** und 2 andere Dateien werden in ihren persönlichen Online-Speicher hochgeladen."

is the displayed message/notification by the way. 
While typing this, it appeared **6** times.

Please help. :-(

---

### Post by Bazon on 2011-08-26
English version is 

English singular: 		
'%(filename)s' and %(other_files)d other file is being uploaded to your personal cloud.
English plural: 		
'%(filename)s' and %(other_files)d other files are being uploaded to your personal cloud.
Current German[0]: 		
»%(filename)s« und %(other_files)d andere Datei werden in Ihren persönlichen Online-Speicher hochgeladen.

as I learned [there](https://translations.launchpad.net/ubuntu/natty/+source/ubuntuone-client/+pots/ubuntuone-client/de/+translate) by the way.

Now, it appeared **5** more times.

---

### Post by Bazon on 2011-08-27
I think it seems to be solved:

One of the folders I share via Ubuntu One, is the pictures folder in the user directory. Inside this pictures folders, there was a hidden folder called .trash-info or .trashinfo. Inside this folder were two sub-folders, called "info" and "files". the files folder contained the file, which seemed to be synchronized on and on. 
*(I think the .trash-info folder was created by moving some pictures in the trash in shotwell.)*

So I deleted the .trash-info folder. But what happened? It re-appeared instantly! 
I had to delete the .trash-info folder several times on my local computer and in the Ubuntu One webinterface before it finally really disappeared.

From that on, I got no further useless notifications. :-)

---

