---
title: "Recently understood the value of backing up"
date: 2011-06-15
forum: General Help
---

### Post by micha8l on 2011-06-15
Hello Ubuntuers!

I've recently had to reinstall Ubuntu and start fresh 'cos I messed thing up :lolflag:
*luckily enough* I had a pen drive handy to transfer my important docs, but man it was a pain to get all the docs back in there right places - I don't fancy much doing it again!

What I'm looking for is some software that'll **back-up my home folder**, yet I'm having a real difficult time finding something suitable. I'm looking for something that may:

[LIST]
[*]Auto schedule backups
[*]Retain file permissions
[*]Options for excluding particular file extensions i.e. .avi, .mp3 etc
[/LIST]
Is there any software that'll do the job?

Regards
Mike

---

### Post by terrykiwi83 on 2011-06-15
SpiderOak is by far the best, been using for some time - its the most secure and beats DropBox in everyway plus its easy to install on ubuntu.

[http://www.spideroak.com](http://www.spideroak.com)

Hope that helps

---

### Post by inameiname on 2011-06-15
Grsync is a basic, good enough one to use. It is a gui for rsync, and I believe does all that you mentioned. However, this is for backing up to another hard drive / usb drive you have, not for online storage.

---

### Post by micha8l on 2011-06-15
Thanks for your reply [terrykiwi83]("http://ubuntuforums.org/member.php?u=882205"), I've already got a storage solution; I've got a Windows XP machine that I network to to store crap -- incidentally I've named it 'crap hauler' -- which makes me wonder if permissions will be retained if I port data from an ext3 to an NTFS file system?

Kind Regards,
Mike

---

### Post by whatthefunk on 2011-06-15
If you can write basic bash scripts, its pretty easy to write your own backup program to better suit your needs.  Mine makes a copy of my home folder, minus some things that I don't feel are necessary, and important system configuration files like my xorg.conf file.  It also makes a list of all the programs I have installed so that I can easily put them all back.  It saves them all in a new folder in the home directory called "Backup" and creates a log file that will be read (eventually, when I finish writing it) so that the files can be automatically put back where they belong.  I simply have to drag this "Backup" file over to a USB drive and I'm ready to go.  It would be pretty easy to schedule the program to run at set intervals, but I choose to just run it when I feel like it.

---

### Post by inameiname on 2011-06-15
True, whatthefunk. I'm curious what yours is. Here are a couple that can be handy. Feel free to make use of them if anybody wishes.

---

