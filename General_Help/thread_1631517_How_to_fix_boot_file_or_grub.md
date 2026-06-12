---
title: "How to fix boot file or grub"
date: 2010-11-26
forum: General Help
---

### Post by paulXPS on 2010-11-26
I tried to change my splash screen and login screen theme. now after grub comes up i choose linux i see the ubuntu splash for like 2 seconds then it goes to this


Ubuntu 10.10 paul-Inspiron-1720 tty1
paul@paul-Inspiron login

I type my login name in then password thats it nothing like a terminal, i can type commands but i dont know what to type to get it back or to even load..Anyone ever seen this or have a solution?

---

### Post by emoguitarist06 on 2010-11-26
It sounds like you have a "boot into Command Line" type of option inside Grub2. Just remove the option. 

[https://help.ubuntu.com/community/Grub2#Editing Menus During Boot]("https://help.ubuntu.com/community/Grub2#Editing Menus During Boot")

[LIST]
[*]If the menu is not normally displayed during boot, hold down the SHIFT key as the computer attempts to boot to display the GRUB 2 menu. 
[*]With the menu displayed, press any key (except ENTER) to halt the countdown timer and select the desired entry with the up/down arrow keys. 
[*]Press the 'e' key to reveal the selection's settings.
[/LIST]

---

### Post by I'mGeorge on 2010-11-26
what happens when you type 
```

startx

```
as a command line ? You might have damaged your login screen trying to change it's theme. But startx command should allow you to load your Desktop/

---

### Post by paulXPS on 2010-11-27
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")



trying to use method 3 chroot to fix my grub2, 
root@ubuntu:/# sudo mount /dev/sda5 /mnt , but get this error 
sudo: unable to resolve host ubuntu
mount: you must specify the filesystem type

---

### Post by paulXPS on 2010-11-27
That didn't work...If I could just boot in to the desktop I could undo what I did..

---

### Post by paulXPS on 2010-11-27
OK I edited the grub at start up took out the resolution dimensions for the boot splash to where it ends in quiet splash. then booted up fine now I get change everything back..Thanks alot for the help..

---

### Post by I'mGeorge on 2010-11-27
> **paulXPS said:**
> [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")



trying to use method 3 chroot to fix my grub2, 
root@ubuntu:/# sudo mount /dev/sda5 /mnt , but get this error 
sudo: unable to resolve host ubuntu
mount: you must specify the filesystem type

I don't think grub it's your problem. As long as grub loads your operating systems entries it's alright, that's it's part of duties, what happens after that it's not grub's problem. You've claimed that you can put your username and password so you would get to the command line. To be sincere it's kinda strange, if your log in screen it's your only problem, why didn't "startx" command worked.

It would help a lot if you could give details about how exactly have you tried to change your log in screen (by the way in Ubuntu theres a graphical preinstalled application for that just go to System->Administration->Login Window) or if you could post the output of the startx command, an error or something.

---

### Post by I'mGeorge on 2010-11-27
> **paulXPS said:**
> OK I edited the grub at start up took out the resolution dimensions for the boot splash to where it ends in quiet splash. then booted up fine now I get change everything back..Thanks alot for the help..

Oooh ok huh, don't mind my previous post than. I'm glad you've figured it out eventually.

---

### Post by paulXPS on 2010-11-27
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)


this is the site that messed it up for me..did everything liked it said.
now i can undo it all.

---

