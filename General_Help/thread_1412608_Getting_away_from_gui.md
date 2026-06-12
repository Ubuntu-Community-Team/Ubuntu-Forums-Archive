---
title: "Getting away from gui"
date: 2010-02-21
forum: General Help
---

### Post by jmsgz on 2010-02-21
Hi folks
  have been using linux "ubuntu" for about a year now and have been trying to move in the direction of command line only control of the desktop. Some issues i must understand further before getting rid of gui. 

Questions   While attempting to delete a file on a cdrom, i get an  error message "File system is read only" is this an ownership, or permission problem or should some defaults have been set in the disk burner prior to burning or copying? Question what would be the command line syntax for copying a file "test" to cdrom1? is the cp cp command used for cdroms? 

Question    is there a way to view pdf files from the command line if system does not have a gui? if not can they be converted to another format that can be.

Question    can someone point me "link" to info on understanding ip addresses, netmasking, gateways etc. I have read Rute and other sources and am not getting it. Currently using Dhcp but i would rather set my own protocols by static means etc. 

Question    I am currently backing-up my files to a server inside my residence. The server (i know most don't like this) has gui installed to aid me in my education in linux. When using ssh file transfer from my desktop i see gui incons on the server for various file systems. When i remove gnome on the server what will i see from my desktop? 

Question    To start programs such as midnight commander and a terminal prompt at system startup on my desktop, which files should be edited to accomplish this? 


thanks in advance
:)

---

### Post by giammy on 2010-02-21
> **jmsgz said:**
> Hi folks
  have been using linux "ubuntu" for about a year now and have been trying to move in the direction of command line only control of the desktop. Some issues i must understand further before getting rid of gui. 

Questions   While attempting to delete a file on a cdrom, i get an  error message "File system is read only" is this an ownership, or permission problem or should some defaults have been set in the disk burner prior to burning or copying? Question what would be the command line syntax for copying a file "test" to cdrom1? is the cp cp command used for cdroms? 


Hi,

it is a permission settings not ownership settings.

Anyway, you cannot copy a fie to a CD as the CD is a physically readonly device!
If you want put a file on a CD you mast use some software to master CD.
From command line they are mkisofs and cdrecord: you cannot use cp.

> **jmsgz said:**
> 
Question    is there a way to view pdf files from the command line if system does not have a gui? if not can they be converted to another format that can be.


see: [http://linux.bytesex.org/fbida/](http://linux.bytesex.org/fbida/)

> **jmsgz said:**
> 
Question    To start programs such as midnight commander and a terminal prompt at system startup on my desktop, which files should be edited to accomplish this? 


thanks in advance
:)

when you disable the graphical startup, you will get a command line login windows

bye
giammy

---

### Post by pokerbirch on 2010-02-21
I don't have an answer for you but i'm just wondering WHY you want to get rid of the GUI? What is the benefit?

---

### Post by xiainx on 2010-02-21
> **pokerbirch said:**
> I don't have an answer for you but i'm just wondering WHY you want to get rid of the GUI? What is the benefit?

Well, for one it improves your script-writing skill, which can make performing tedious tasks a LOT faster. It's a great way to learn how your computer works also.

---

### Post by jmsgz on 2010-02-21
> **pokerbirch said:**
> I don't have an answer for you but i'm just wondering WHY you want to get rid of the GUI? What is the benefit?

several reasons but the biggest for me are:
*  server resources are wasted by using gui
*  security is better without X
*  control of desktop/server is more powerful/faster from command prompt 
*  knowledge of system resources higher with command prompt knowledge
*  linux control across platforms, is generally universal via command prompt
      whereas gui's between systems change.

---

### Post by giammy on 2010-02-21
> **pokerbirch said:**
> I don't have an answer for you but i'm just wondering WHY you want to get rid of the GUI? What is the benefit?

to the other reasomn: on a Pentium II a linux system is usable on CLI
(or many embedded systems are accessible via CLI ... 

bye
giammy

---

### Post by pokerbirch on 2010-02-21
Ahhh, yes...i assumed you were referring to a Home Desktop PC rather than a server because you referred to "control of the desktop". I've never worked on a server setup, but i assumed it was ALWAYS controlled by command lines and scripts and therefore the "desktop" was none existent.

Give me a year or two and i'll probably be asking the same questions as the OP. :)

---

### Post by jmsgz on 2010-02-21
> **giammy said:**
> Hi,

it is a permission settings not ownership settings.

Anyway, you cannot copy a fie to a CD as the CD is a physically readonly device!
If you want put a file on a CD you mast use some software to master CD.
From command line they are mkisofs and cdrecord: you cannot use cp.



see: [http://linux.bytesex.org/fbida/](http://linux.bytesex.org/fbida/)



when you disable the graphical startup, you will get a command line login windows

bye
giammy

sorry, not cd but cdrw! also there are no man pages for mkisofs or cdrecord?

---

### Post by jmsgz on 2010-02-21
> **giammy said:**
> Hi,

it is a permission settings not ownership settings.

Anyway, you cannot copy a fie to a CD as the CD is a physically readonly device!
If you want put a file on a CD you mast use some software to master CD.
From command line they are mkisofs and cdrecord: you cannot use cp.



see: [http://linux.bytesex.org/fbida/](http://linux.bytesex.org/fbida/)



when you disable the graphical startup, you will get a command line login windows


bye
giammy

yes i understand that thanks but how can they be autostarted at system bootup?

---

### Post by giammy on 2010-02-21
> **jmsgz said:**
> sorry, not cd but cdrw! also there are no man pages for mkisofs or cdrecord?

Same consideration: from what I know, you cannot use cp but mkisofs and cdrecord
[http://linuxcommand.org/man_pages/mkisofs8.html](http://linuxcommand.org/man_pages/mkisofs8.html)
[http://linux.die.net/man/1/cdrecord](http://linux.die.net/man/1/cdrecord)

bye
giammy

P.S: i usually put on google: command_name man page and you get it!

---

### Post by giammy on 2010-02-21
> **jmsgz said:**
> yes i understand that thanks but how can they be autostarted at system bootup?

startup applicatins are started by file in /etc/init

For example /etc/init/tty1.conf
starts the terminal on tty1
you can see examples in your system

bye

---

### Post by jmsgz on 2010-02-21
> **giammy said:**
> startup applicatins are started by file in /etc/init

For example /etc/init/tty1.conf
starts the terminal on tty1
you can see examples in your system

bye



thats the ticket!, thanks !!!!

---

### Post by marshag63 on 2010-02-21
Grab the INX cd or virtualbox version and explore the files/scripts.  INX is a command line only live CD.  Its main purpose is as a tutorial to learn command line linux.  It comes already configured so you can work with files/file systems, access internet via eth0 or wlan, view pictures/pdfs,edit files, manage files, and listen to internet radio/shoutcast or your own music files.  I am sure you will find what you are looking to learn.

[http://inx.maincontent.net/](http://inx.maincontent.net/)

(the newest unstable testing version is 1.17).

Let us know what you think.

MarshaG.

---

