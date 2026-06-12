---
title: "installing Kubuntu"
date: 2006-06-02
forum: General Help
---

### Post by dumbsnake on 2006-06-02
OK,
    So I totally searched for a long time to try and find out how to install kubuntu, and I am pretty sure I got that answered.  One problem though: my computer can't find the package kubuntu desktop to install.

I want to install my computer to be able to boot as either KDE or GNOME and possible X later.  It seems that the command I should be using is:

  sudo aptitude install kubuntu-desktop
  
  OR

  sudo apt-get install kubuntu-desktop

  OR

  I could use the package manager.

In any event, why do I not have that package?  Any ideas?  I just want to install KDE to try out KDevelop.  I am a very experienced C++ programmer, but I love a good GUI when I program.  Thanks in advance for any help.  If you ever need help with C++, send those questions my way.

---

### Post by ArizonaKid on 2006-06-02
Are you adding the CDROM to pull from?  That might be the problem.

The procedure on Breezy was as follows:

> insert Kubuntu Disc
Type:  "sudo apt-cdrom add"
Type:  "sudo apt-get install kubuntu-desktop"
logout, end session


Finally, in session select KDE.

I don't believe the procedure is different on the dapper live CD.  I am so used to the "alternate based install"

---

### Post by ericesque on 2006-06-02
that is strange.  I assume you have a working install of Ubuntu 6.06.  I just checked and the package    kubuntu-desktop   is available in Synaptic.  Try doing a search in Synaptic

---

### Post by dumbsnake on 2006-06-02
yeah, it isn't in synaptic.

I am trying the sudo apt-cdrom add thing but it is just hanging on "Mounting CD-ROM..." so I am thinking maybe something is corrupted in memory right now.

I'll try it after a reboot.

---

### Post by ericesque on 2006-06-02
you might also want to do a 

sudo apt-get update  

just to make sure you have a fresh list of the packages.

---

### Post by dumbsnake on 2006-06-02
OK,

   After rebooting, I was able to do the sudo apt-cdrom add thing.  That didn't add the package and neither did apt-get update.  I noticed that the CD is label ubuntu 5.10, but I am pretty sure I selected one of the 6.06 downloads when I downloaded my ISO.  Is there any way to manually get a package?  I appreciate all the help you guys have given so far.

---

### Post by ericesque on 2006-06-02
gedit /etc/apt/sources.list

check the file and read through it to see if the entries say breezy or dapper.  --it will say one or the other in the first few lines of the file.  Report back in the next five min if you can, cuz I'm going to sleep soon-- haha.

---

### Post by dumbsnake on 2006-06-02
its breezy...yeah, but that shouldn't prevent me from getting the kubuntu package should it?

I uncommented those lines after doing a sodu to edit the text (I am learning), I am going to see if it pulls it in yet.

---

### Post by ericesque on 2006-06-02
sorry, dude, I should have read your first post more carefully.  Did you know that you can run a KDE app in Gnome?  I didn't until recently--which is why I ask.  You don't have to install KDE to try Kdevelop unless you're trying to develop and test a KDE app.

---

### Post by dumbsnake on 2006-06-02
I didn't know that.  How do I do that?  God, there is so much to learn.  I know jack.

I think I am going to burn an ISO of 6.06 anyway.  Might as well learn the new generation...

Linux take 4...  But I am learning.  Thanks so much for the help.  Seriously.

---

### Post by ericesque on 2006-06-02
just install it.  Most apps will run just fine.  It looks like it's in Synaptic for dapper.

---

### Post by ericesque on 2006-06-02
no problem.  I suppose AIM would have been quicker, but this works.  To upgrade your breezy install to dapper just

sudo apt-get update
sudo apt-get dist-upgrade

and after a significant download-- albeit less than an ISO-- you'll have Dapper without losing any configuration you've done.

good luck!  feel free to PM me.

---

### Post by ArizonaKid on 2006-06-02
Ok...

The terminal command
> $ sudo apt-cdrom add
allows you too add the CD as a source to pull the package direcly off a Kubuntu 6.06 CDROM.

If you don't have a Kubuntu 6.06 CDROM, and yes having the Kubuntu 5.10 version is not ideal, than type in the following commands in terminal in order, hitting enter after each command.
> $ sudo apt-get update
$ sudo apt-get install kubuntu-desktop

I believe this is what you were referring to as grabing the package the manual way.  I'll assume it means downloading directly / install.

Just to be clear, on the above command, don't type the $ symbol.  I actually did that when I started with Linux and was following the forums.  lol  I later found out those symbols refered to seperate commands.

---

### Post by ArizonaKid on 2006-06-02
Here is a really good web page on installing KDE on Ubuntu.  It has very good screenshots and I noticed was updated for Dapper.

**[SIZE="3"][Installing KDE on Ubuntu at Psychocats.net]("http://www.psychocats.net/ubuntu/kde.html")[/SIZE]**

---

