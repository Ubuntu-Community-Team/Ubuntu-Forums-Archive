---
title: "Permission denied"
date: 2009-12-25
forum: General Help
---

### Post by wphred on 2009-12-25
I downloaded an app to my desktop, but when I tried to create a directory in /usr/local/games to house the the app, I got a "permission denied" error at the end of my mkdir command.

I'm the only user of this machine, so I don't understand this? - I thought the /usr/local directory would be open.

Ideas?

---

### Post by houseworkshy on 2009-12-25
Though you fully own the machine and system you are not logged in as the super user or "root" by default.  This is a safety device.  However you can assume these privalages when ever you want.  The comand you need is "sudo" without the quotes.  When you prefix any command with this you will be asked for your password   Once you have given it "prooving that you are in fact admin and allowed to make changes to the system the command will be run.  For a full description type man ( which is short for manual ) in front of sudo ( or any comand you wish to know about for that matter ) and the manual page will be displayed.  To clear the page and get back to the prompt press the q key.

---

### Post by hawthornso23 on 2009-12-25
> **wphred said:**
> I downloaded an app to my desktop, but when I tried to create a directory in /usr/local/games to house the the app, I got a "permission denied" error at the end of my mkdir command.

I'm the only user of this machine, so I don't understand this? - I thought the /usr/local directory would be open.

Ideas?

Ubuntu has a very clever security model. Your system directories and files are protected. Anything that involves changing these directories and files has to be done using superuser privileges. This is what makes linux almost completely immune to viruses and the kinds of security threats that afflict windows users. 

You do have superuser privileges. To use them you just need to put `sudo'  (super user do) on the front of the command. It will then ask for your password.

sudo mkdir /usr/games/myapp

should do what you want. It would also be useful for you to learn more about file ownership and permissions.

---

### Post by taurus on 2009-12-25
Here is more info about the sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by houseworkshy on 2009-12-25
A similar command, more pertinant to when one is using the graphic user interphase, is gksu.  It would be worth looking at that too.

I found this free ( well the pdf download is ) book very useful when starting out.  

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by lswb on 2009-12-25
/usr/local is writeable only by root. Just use
"sudo mkdir /usr/local/games/directory-name"
You will also need to use sudo copy files to the directory. If you want to use a gui,
one way is to press <ALT-F2> and type "gksudo nautilus" in the dialog, to run an instance of nautilus file manager as root. Remember to exit from any root-enabled shells or programs as soon as you're done; being root makes it too easy to accidentally mess up your system.

---

### Post by tom.swartz07 on 2009-12-25
> **houseworkshy said:**
> A similar command, more pertinant to when one is using the graphic user interphase, is gksu.  It would be worth looking at that too.

I found this free ( well the pdf download is ) book very useful when starting out.  

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

+1
This guide helped me out so much when I started, and I find myself referring to it every so often!

This should be required reading before people start using Ubuntu! :P

---

### Post by wphred on 2009-12-25
Okay, I get it - a little different than unix. That also explains why the su command doesn't work - asks me for a password, and I'm wondering where could it be.

Thanks to all of you that replied. I've already downloaded the pocket guide - have a little reading ahead of me.

---

