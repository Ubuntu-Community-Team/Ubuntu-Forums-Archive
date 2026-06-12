---
title: "Usplash Is in Karmic?"
date: 2009-10-31
forum: General Help
---

### Post by moore.bryan on 2009-10-31
I know xsplash replaced usplash, but when on installs ubuntu-desktop in karmic, it installs usplash as a dependency. Huh? I'm a little confused.

---

### Post by moore.bryan on 2009-11-05
No devs have an answer to this?

---

### Post by Ray() on 2009-11-05
I had the same question but read in [another thread ]("http://ubuntuforums.org/showthread.php?t=1302200&highlight=usplash+xsplash") that the usplash is there just because the boot isn't fast enough to jump to xsplash right away so there has to be something that looks more representable before the xsplash kick in - in this case the ubunut logo before the xsplash starts...

I was quite disappointed by that because I was looking forward to the xplash themes and so on. Hopefully this should be solved(and usplash removed) in the next release of ubuntu.

---

### Post by moore.bryan on 2009-11-06
Thanks, Ray(), but I'm concerned about RAOF's response:
> 
The goal is to eventually only load usplash in exceptional circumstances: when fsck kicks in, or when you need to enter a passphrase for your encrypted partition before X can start.

My understanding is that usplash is currently unconditionally enabled because the boot process isn't yet quite fast enough to skip straight to X. As I understand it, a Lucid goal is to have boot fast enough to not use usplash in the common case (and thus speed boot up a bit more ).

Why is the boot so slow as to *require* usplash? I understand the discussions happening elsewhere in the fora about boot times, mainly because I'm part of them, and the connection to upstart and grub2; but, still...

---

### Post by Ray() on 2009-11-09
I don't understand it either... In my case the usplash is visible for like 75% of the boot time, then I see the nice xsplash but just for a few seconds before the login screen shows up. It would have been better if they left there just the usplash when it takes so much time to load everything necessary to show the xsplash :-/ Btw doesn't this whole procedure slow down the whole boot process? I haven't seen any comparison between ubuntu 9.10 and 9.04 boot times.

---

### Post by moore.bryan on 2009-11-10
From what I've gathered in discussions with others is the Jaunty vs. Karmic boot-time comparisons are faulted because Jaunty only measures from kernel choice in grub to login screen, whereas Karmic measures from kernel choice in grub2 to "usable desktop."

---

### Post by pootan on 2009-11-10
Something semi-related. Once I removed Ubuntu One,  Couch Desktop and CouchDB(?) and all references to it my boot time decreased considerably. Just removing Ubuntu One generated an error list 20 lines long on boot.

---

### Post by moore.bryan on 2009-11-10
Hmm... interesting. I hadn't thought about UbuntuOne being installed by default in Karmic. I knew it was, just hadn't put 2-and-2 together. As far as CouchDB goes, I'm not sure why it's installed at all. Perhaps someone could fill me in?

---

### Post by Ray() on 2009-11-10
Thanks for the suggestion, I tried using ubuntu one - why not I thought. It's always nice to share data between multiple computers in a convenient manner but after trying it, it never showed me any uploaded files. It always said something like "ubuntu one finished synchronization" but when I went to the ubuntu one website and logged in no files showed. Probably my mistake didn't have time to get into it - just simply don't need it.

I read that couch DB and couch desktop is a system and database for storing application data in one place - do I understand it correctly that they want to share application settings, data, etc using ubuntu one?

And more importantly is it safe to remove or do I get a long error list on boot as well? :D

---

### Post by moore.bryan on 2009-11-10
> **pootan said:**
> Something semi-related. Once I removed Ubuntu One,  Couch Desktop and CouchDB(?) and all references to it my boot time decreased considerably. Just removing Ubuntu One generated an error list 20 lines long on boot.
> **Ray() said:**
> And more importantly is it safe to remove or do I get a long error list on boot as well? :D
I *just* removed all couchdb and ubuntuone references from my lappie and rebooted. Boot seemed *a little* quicker, but I'm using ureadahead from a PPA to try and speed up my system, so it'll take a couple more reboots to double-check the bootcharts. I was greeted with aptitude wanting to remove *a lot* of stuff after I uninstalled couchdb/ubuntuone, but nothing I seemed to *need*. 

Something else which is strange; as of right now, my network connection is flying. I wonder if some of the networking issues related to Karmic may be UbuntuOne related...

---

### Post by Ray() on 2009-11-10
So I removed ubuntu one, couch desktop and couch db without any boot problems. As far as the boot time is considered, it might be faster but not very significantly. (using ubuntu 9.10 64bit btw)

---

### Post by moore.bryan on 2009-11-13
I will agree with the "seems faster," but only negligibly. Shame; I wish I understood the upstart boot process more because I'm *convinced* that's where a lot of this is. I know it's a "work in progress."

---

### Post by snip3r8 on 2010-04-01
usplash can be removed without a problem,it will just show your bootup info instead of ubuntu logo

---

