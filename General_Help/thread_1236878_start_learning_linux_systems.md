---
title: "start learning linux systems"
date: 2009-08-10
forum: General Help
---

### Post by chad_fiend on 2009-08-10
hello , 

i want to learn all about linux systems , i have been using ubuntu for sometime but i want to be much more than a user.

can anyone give some hints to start or maybe resources on how to start understandign linux systems , especially ubuntu.

any hints on how to start would be helpful :)

thanks in advance ,

---

### Post by michy99 on 2009-08-10
A google search for 'linux tutorial' would probably turn up some good places to start.

---

### Post by amauk on 2009-08-10
best way to learn is to do things
you could read up on things all day long and not really learn anything, unless you put it into practise

Think of something to do, then do it

Setting a local mail server, so all user's email is stored and controlled centrally, is probably a good project to do.

You can start out with a simple system just serving IMAP folders, and gradually add features to it (webmail, spam filtering, etc. etc.)

---

### Post by TheForumTroll on 2009-08-10
I would recommend you to setup a Ubuntu Server without any user interface then administer it via SSH. Could be in a virtual machine. Read about file permission, shell scripting (I use [Zsh]("http://www.zsh.org/") instead of bash), init.d, cron, logs and so on.

There's lots on google but you could have a look [here]("http://lowfatlinux.com/"), [here]("http://www.linuxconfig.org/") and [here]("http://tldp.org/LDP/abs/html/").

Create a few scripts. Like create a script that ping a few servers (like google) to see if the network is up and if it's not it restart the network. Then add it to cron and run it every few minutes. Those small scripts is going to become very handy in the long run :)

---

### Post by marshag63 on 2009-08-10
You could try out a live cd of a command line distro called INX.  It even has built in tutorials:

How to navigate directories.
How to search for things.
Package management.  
Plus, it has lots of things already built in and setup - you can watch a short movie in framebuffer mode, check gmail/email, IRC chat, surf the net in text and graphical web browser, connect to wireless internet, listen to radio streams and play CDs or music stored on your computer, learn to use "screen" and dvtm, etc.

Ever wonder what is a quick way to search for an application you might like to install?  apt-cache search TYPE OF APPLICATION - it don't get no faster than that :)

Its now completing testing phase of scripts to make a USB bootable flash drive with INX (with persistence).

I highly recommend it!  :)

[http://inx.maincontent.net/](http://inx.maincontent.net/)

MarshaG.

---

### Post by scouser73 on 2009-08-11
> **chad_fiend said:**
> hello , 

i want to learn all about linux systems , i have been using ubuntu for sometime but i want to be much more than a user.

can anyone give some hints to start or maybe resources on how to start understandign linux systems , especially ubuntu.

any hints on how to start would be helpful :)

thanks in advance ,

You should have a look at [[COLOR="Red"]**Free Ubuntu e-books**[/COLOR]]("http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html"), for getting a better understanding of Ubuntu.

---

