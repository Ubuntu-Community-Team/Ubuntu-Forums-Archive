---
title: "Gui svn setup?..."
date: 2010-01-27
forum: General Help
---

### Post by VcDeveloper on 2010-01-27
My goal is to setup a subversion control system on Ubuntu for storing my game assets, scripts, source, etc and be able to access them from my Windows OS.

I've installed the Subversion control system and need suggestings on what GUI SVN to use on both sides to be successful at this.  All my development will be on my Windows Vista Ultimate, but I want to check-In and Out of Ubuntu.  The server will also be available for other team developers in collaboration with me.  I want it to be a password access only.

This is my first attempt at this and plenty of help would be very appreciated!

---

### Post by hhlp on 2010-01-27
there is a packet call rapidsvn will help you, you can find in synaptic

---

### Post by VcDeveloper on 2010-01-27
Thanks hhlp! I have not read much into the doc's on the subversion, but what would be a good place to start the repository.  Would this be in a folder off the web server root and create a Virtual Host for it?  Where would you start?  

The RapidSVN didn't have the feature to create a repo, so I installed KDESVN.  But, I can use RapidSVN on my Windows for everything else.

Just need to know how to properly create a repo and the proper place to put it.

---

### Post by ph0nph0n on 2010-01-27
On Windows one of the most famous SVN GUI is [TortoiseSVN]("http://tortoisesvn.tigris.org/"). On Linux (if you're using Gnome), you can use [RabbitVCS]("http://www.rabbitvcs.org/"). They look pretty much the same.

Both integrates with the file browser, so you can perform pretty much everything you need from nautilus/explorer, which is very convenient. Also don't worry, both will let you create new repositories very easily.

Tortoise integrates a diff viewer, Rabbit uses [Meld]("http://meld.sourceforge.net/").

You won't find Rabbit in the official Ubuntu repositories, but they have a PPA (check out their website) you can use.

---

### Post by VcDeveloper on 2010-01-31
Thanks [ph0nph0n]("http://ubuntuforums.org/member.php?u=377731")!

Question, since my Subversion is installed on my Ubuntu Server (Subversion File Server) will I be able to do everything from my WIndows OS using these front-ends?  I see that TortoiseSVN is integrated into Window Explorer.  So, I'm assuming to make a folder share in Samba for my repo and this is where everyone check-out/in projects to work on.

Let me know if this is what everyone else is doing and if night what is the best set-up?

---

### Post by ph0nph0n on 2010-02-02
Are your Ubuntu server and your Windows box two separate computers? If yes you won't have any issue.

However you mentioned a samba folder, so I guess you're dual booting. I don't know if that could work, you'll have to give it a try. How come you want to be able to access it from both systems?

---

### Post by VcDeveloper on 2010-02-21
Oh yea, these are two different OS.  Thanks for the reply!...

---

