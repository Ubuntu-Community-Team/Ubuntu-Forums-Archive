---
title: "how to change file permissions to change background screen"
date: 2010-02-21
forum: General Help
---

### Post by Cyteck on 2010-02-21
Hello,

I'm new to Ubuntu Linux but have many years on windows platform. Please can someone help me with how to change the following items.

**No.1** I would like to change the HORRIBLE!! YAK!! brown background color behind the word Ubuntu in the start up screen when the machine loads up (before the login). I have located the image file for this which I have found to be:-

/usr/share/images/xsplash/bg_2560x1600.jpg

but the OS says that root is the owner and that I don't have permission to change this. So how can I change this for a color I do like.

**No.2** I would also like to change the login dialogue screen style. I know this is possible but again I'm fumbling to see how I can do this. I have tried with the start up manager but every attempt fails, the settings don't take. Once again I suspect permissions are at the bottom of the problem? 

**No.3** Would like to have a colorful splash screen image on boot up, I've managed to remove the old one (small white 3 ring ubuntu logo on black background) but havent been able to install or replace with a new one. Its been incredibly frustrating, I'm feel sure I'm missing something simple here. Wondering if its permissions yet again?

Anyone who can offer help on any of the above, guidance or advise me would be much appreciated. Please bear in mind that I'm still very much feeling my way with Linux so keep it simple. Thanks.

---

### Post by Girya on 2010-02-21
**Doing the following will give you the ability to ruin your O/S by deleting system files** you might want to read up on users, files and permissions first. 

[http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html")

you don't want to change file permissions on system files, instead you want to assume root privileges to do administrative jobs. 

**No 1** you need to assume root privileges since the file is owned by root. open up a terminal (Applications>Accessories>Terminal

and type in:

```
sudo naut
``` then press the tab button, then the enter button, then type in your password (you won't see anything at the prompt, no stars, nothing) and press enter one last time. that will give you a file browser with the proper permissions to move files.

---

### Post by JiuJitsu500 on 2010-02-21
the TAB button there just fills in what the system thinks is what you'll type in next (there can only be so many options, like 1)... just type "sudo nautilus" if you'd like :) bash is easy, but where it leads still tricks me...

and you should set a root password too... open a terminal and type "sudo passwd" without the quotes and type your stuff.

I posted a way to change the xsplash (the ugly brown crap with the ubuntu animation before and after login...) and the log-in background earlier... let me find it and I'll post it up for ya!

---

### Post by JiuJitsu500 on 2010-02-21
[Here]("http://ubuntuforums.org/showthread.php?t=1407605") you go :)

My last post on there. Note the login background is different than the splash, so use the same image or it can be strange for anyone looking at your machine boot up...

---

