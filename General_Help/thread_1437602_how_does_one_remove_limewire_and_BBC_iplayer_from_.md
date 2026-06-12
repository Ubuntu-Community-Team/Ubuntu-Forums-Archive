---
title: "how does one remove limewire and BBC iplayer from karmic koala"
date: 2010-03-24
forum: General Help
---

### Post by shantiq on 2010-03-24
[COLOR=Blue][B][FONT=Comic Sans MS][SIZE=3]how does one remove limewire and BBC iplayer from karmic koala


got these two on my system and i see no way of removing them which i want to do


the software centre has no option i can see for third party programs


any thoughts ?
[/SIZE][/FONT][/B][/COLOR]

---

### Post by Ubuntist on 2010-03-24
Have you tried Help available from iPlayer's control panel?  Do a search for "uninstall" and it comes up with some results; haven't tried it myself.

---

### Post by shantiq on 2010-03-24
[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]ok so followed your advice
[URL="http://iplayerhelp.external.bbc.co.uk/help/download_programmes/uninstall_desktop_linux"]
got to here[/URL]


and it says =>

[/B]**BBC iPlayer Help**

**How do I uninstall BBC iPlayer Desktop for Linux?**


[/COLOR][/SIZE][/FONT]                             [FONT=Century Gothic][SIZE=2][COLOR=Blue]Please see [the advice on Adobe's site]("http://blogs.adobe.com/air/2008/12/tips_on_resolving_application.html#uninstall15app").
This link will take you to a website outside BBC Online. The BBC is not responsible for content or software downloaded from external sites.[/COLOR][/SIZE][/FONT]
   


 [SIZE=2][COLOR=Blue][B]

so next step is

[IMG]http://blogs.adobe.com/air/Uninstall.png[/IMG]

and then you get to there

[IMG]http://img191.imageshack.us/img191/3738/screenshotiye.png[/IMG]

once adobe air which you must have to run iplayer is gone iplayer is disabled but still not removed

as for limewire found the answer [here ]("http://ubuntuforums.org/showthread.php?t=34566")

and it simply was 

[/B][/COLOR][/SIZE]```
sudo apt-get remove limewire-basic
```

[SIZE=2][COLOR=Blue]**so my question still remains    i do not see a way to remove BBC Iplayer Desktop from my machine**[/COLOR][/SIZE]

---

### Post by shantiq on 2010-03-24
[FONT=Century Gothic][SIZE=2][COLOR=Blue]**ok found it with help [from here from the reply by 3rd album]("http://ubuntuforums.org/showthread.php?p=7780340#post7780340")**[/COLOR][/SIZE][/FONT]
[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]


1. [/B][/COLOR][/SIZE][/FONT]     
     ```
apt-cache search iplayer 
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]
2.  if you scroll down you will find the name of YOUR iplayer each one has an ID number 
 [/B][/COLOR][/SIZE][/FONT]     
     ```
bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1 
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]


3. then run the usual

[/B][/COLOR][/SIZE][/FONT]   
     ```
sudo apt-get remove bbciplayerdesktop.61db7a798358575d6a969ccd73ddbbd723a6da9d.1 
```[FONT=Century Gothic][SIZE=2][COLOR=Blue][B]not exactly simple and helping the user but that is the way to do it
took me a while to work it out[/B][/COLOR][/SIZE][/FONT]

---

