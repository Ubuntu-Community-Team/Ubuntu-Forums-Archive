---
title: "How can I delete recent files ?"
date: 2011-11-23
forum: General Help
---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-11-23
At first I apologize if the subject was in the wrong place
 The reason is that I do not speak English
 And enlisted Google to translate can I register and add this topic :smile:
[COLOR=Red]  I have a question:[/COLOR]

**How can I delete recent files ?**

**[COLOR=DarkOrange]ubuntu 11.10[/COLOR]**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207832&stc=1&d=1322048558[/IMG]

---

### Post by ajgreeny on 2011-11-23
This may have changed in Ubuntu 11.10, but in 10.04 the information on  recently used files is in a hidden file in /home/user called **.recently-used.xbel**

Maybe deleting that file, if it exists in 11.10, will get rid of that  listing.  If not it may be worth using the command ```
locate recently  | grep $USER
``` in terminal to see if any similarly named files exist in your home instead.

---

### Post by mikejonesey on 2011-11-23
.recently-used.xbel

ps file should be purged or manualy edited as it is xml, the recent docs are not symlinks so you can't use find n rm... (you could develop some piped seds / awk but  it's easyer just to purge...)

---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-11-23
[COLOR=Red]I did not find this file[/COLOR] "**.recently-used.xbel**"

---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-11-23
[COLOR=Red]after using the command :[/COLOR]** locate recently  | grep $USER**

> r3d@r3d:~$ locate recently  | grep $USER
/home/r3d/.icedtea/cache/recently_used
/home/r3d/.local/share/recently-used.xbel

---

### Post by ajgreeny on 2011-11-23
OK, so now try removing the **/home/r3d/.local/share/recently-used.xbel** file.  That should do it for you.  The file has obviously been moved now, in 11.10.

---

### Post by oldtimer7777 on 2011-11-23
I use Bleachbit for this..

sudo apt-get install bleachbit
sudo bleachbit

---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-11-23
> **ajgreeny said:**
> OK, so now try removing the **/home/r3d/.local/share/recently-used.xbel** file.  That should do it for you.  The file has obviously been moved now, in 11.10.

[COLOR=Red]I found the file. What I was doing now?[/COLOR]

> **oldtimer7777 said:**
> I use Bleachbit for this..

sudo apt-get install bleachbit
sudo bleachbit

[COLOR=Red]Can you explain the program?[/COLOR]

---

### Post by mikejonesey on 2011-11-23
> **&#1593 said:**
> [COLOR=Red]I did not find this file[/COLOR] "**.recently-used.xbel**"

you have now lol, open a terminal and;

```
rm **.recently-used.xbel**
```
to remove it

or

```
mv **.recently-used.xbel** backup.recently-used.xbel
```to move it to backup

the easyest way to refresh after is to "killall gnome-panel" which will restart the panel applet...

---

### Post by matt_symes on 2011-11-23
Hi
> [FONT=monospace]
[/FONT]mv **.recently-used.xbel** backup.recently-used.xbel
A variant on this (copy and paste)

```
mv .recently-used.xbel{,.backup}
```Less typing :D

Kind regards

---

### Post by &#1593;&#1603;&#1608;&#1586; &#1576;&#1603;&#1608;&#1586; on 2011-11-23
> **mikejonesey said:**
> you have now lol, open a terminal and;

```
rm **.recently-used.xbel**
```to remove it

or

```
mv **.recently-used.xbel** backup.recently-used.xbel
```to move it to backup

the easyest way to refresh after is to "killall gnome-panel" which will restart the panel applet...

> **matt_symes said:**
> Hi

A variant on this (copy and paste)

```
mv .recently-used.xbel{,.backup}
```Less typing :D

Kind regards

[COLOR=Red]Hi
I find this command and delete recent files :[/COLOR]
```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon –replace
```[COLOR=Red]How I Make this command a shortcut in Create-Launcher ?[/COLOR]

---

