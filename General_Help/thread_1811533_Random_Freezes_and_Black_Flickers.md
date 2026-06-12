---
title: "Random Freezes and Black Flickers"
date: 2011-07-25
forum: General Help
---

### Post by cmd.exe on 2011-07-25
I got Ubuntu 11.04 on my USB and I booted from it for the first time, worked fine.
I went back and it started to flicker and freeze then come back and the rez was stuffed.


Anyone know what's going on? Using an ATI Graphics Card if that helps.

---

### Post by wildmanne39 on 2011-07-25
Hi, run these commands from a terminal
```
sudo lshw
```
```
lspci | grep VGA
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by cmd.exe on 2011-07-26
I'm running Windows and installed Ubuntu using that portable USB live creator thingy for Ubuntu by pendrivelinux.com.
Do you want my computer Specs?

---

### Post by wildmanne39 on 2011-07-26
Hi, run the commands in my last post that will give us the information to start helping you.

---

### Post by deconstrained on 2011-07-26
Which driver are you using?

Alt-F2 (run dialog) gksudo jockey should bring up a nice program for managing 3rd-party/proprietary drivers. Look for and try using other drivers, but first and foremost you should try the one that's recommended.

---

### Post by cmd.exe on 2011-07-26
C:\Users\Administrator>sudo
'sudo' is not recognized as an internal or external command,
operable program or batch file.

---

### Post by wildmanne39 on 2011-07-26
Hi, you need to run those commands from your ubuntu system, and open a terminal by hitting ctrl+atl+t

---

### Post by deconstrained on 2011-07-26
> **cmd.exe said:**
> C:\Users\Administrator>sudo
'sudo' is not recognized as an internal or external command,
operable program or batch file.
But of course. You're using *cmd.exe*, in **Windows**. Your problem is with screen flickering in *Ubuntu*, correct? If the same problem happens in both Windows and Ubuntu, it may be a hardware malfunction.

For future reference, it's safe to assume that whenever anyone in these forums suggests you try a command, **it applies to GNU/Linux or Unix.**

---

### Post by cmd.exe on 2011-07-27
> **deconstrained said:**
> But of course. You're using *cmd.exe*, in **Windows**. Your problem is with screen flickering in *Ubuntu*, correct? If the same problem happens in both Windows and Ubuntu, it may be a hardware malfunction.

For future reference, it's safe to assume that whenever anyone in these forums suggests you try a command, **it applies to GNU/Linux or Unix.**
Seen in the last post about me running Windows, yes it only happened in Ubuntu.

It might be a driver malfunction, but I'm sure I have the updated driver.

---

