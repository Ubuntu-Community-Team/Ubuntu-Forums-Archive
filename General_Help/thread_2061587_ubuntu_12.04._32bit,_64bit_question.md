---
title: "ubuntu 12.04. 32bit, 64bit question"
date: 2012-09-22
forum: General Help
---

### Post by pretty_whistle on 2012-09-22
I have Ubuntu 12.04 32bit.  I'm looking for a new computer but the ones I'm looking at are 64bit.  Can I use my current 32bit on it??  

I'm asking because I have a saved disk image of the 32bit which has all my folders etc on it.  I want to use this disk image, a 32bit, on a 64bit machine but will it work ok?

---

### Post by wojox on 2012-09-22
Sure can.

---

### Post by deadflowr on 2012-09-22
The only problem I could see is if you installed proprietary drivers on your saved disk image. Like if your old system used an nvidia card and the new system uses something else, like an intel or ati card. If you ran it with the open-source drivers then it would be no problem. But it shouldn't be a major problem, as purging those drivers is simple enough.

---

### Post by feardotcom on 2012-09-23
You can, but why? you cant take full advantage of your new machine with it on 32bit. Like the poster said before you may have problems with the drivers from the previous machine. TBO, the best, and easiest, thing to do is to probably do a new install on the new machine, and just copy your files from your old machine. You could either setup network sharing to just copy and paste over the network from the old computer to the new computer, or you can back up your files on a USB storage device, or CD/DVD.

---

### Post by DMGrier on 2012-09-23
Or just take advantage of Ubuntu one for doing a new back up of your folders and files. I would go with 64 bit to get true speed out of your machine.

---

### Post by pretty_whistle on 2012-09-23
> **feardotcom said:**
> You can, but why? you cant take full advantage of your new machine with it on 32bit. Like the poster said before you may have problems with the drivers from the previous machine. TBO, the best, and easiest, thing to do is to probably do a new install on the new machine, and just copy your files from your old machine. You could either setup network sharing to just copy and paste over the network from the old computer to the new computer, or you can back up your files on a USB storage device, or CD/DVD.
I'd like to avoid a fresh install of the 64bit because not only do I have files to copy over but settings I have set up plus all the programs I've installed as well.  With a fresh install I'd have to redo all that.

---

### Post by pretty_whistle on 2012-09-23
I wonder if I could just do an upgrade, like 1st restore the 32bit disk image and then upgrade to 64bit.  Am I onto something here???  Wait.  It probably wouldn't offer to upgrade that, would it??

---

### Post by 1clue on 2012-09-23
I don't believe you can "upgrade" from 32 to 64.  You CAN start with 64 and add 32-bit libraries so you can run both platforms.

I've been using Linux since 1995 or so.  I have never had a happy installation like what you're describing.  I've tried to copy from one computer to another, but if it's not the same CPU family and extremely similar hardware I always wind up installing again anyway.  That includes pulling the hard drive out of the old system and putting it in a new one.

Your settings are in your /home/youruser folder.  Make a backup of your home directory, and browse through your apps to see which ones are most important to you.

Generally speaking, you'll have a bunch of apps you installed and then never really used.  This is an opportunity to start fresh.  Installing Ubuntu takes an extremely small amount of time IMO, less than any Windows or Mac OS I've ever tried, and certainly less than Solaris or SCO.  As long as you're not trying anything fancy Ubuntu is about as easy and fast as it gets.  I've timed an install from clicking "go" to rebooting with a runnable system in 5 minutes flat.

Since you're going from 12.04 to 12.04 you might get away with keeping your settings from the 32-bit install.  In that case, you take your home folder and extract it over the top of the new one.

However, I haven't really had any luck trying this from say 11.10 to 12.04 for example.  An upgrade, or a different distro, very few of the config files actually work.

Instead what I do is extract my email addresses and other data to something that is transportable, then copy those files and re-import them on the new system.  I also ALWAYS back up my home directory.  There's almost always some file I forgot.

Good luck and have fun.

---

### Post by Sef on 2012-09-23
> I don't believe you can "upgrade" from 32 to 64. 

That is correct. You can install one or the other or both on one computer, but upgrading is impossible.

---

### Post by pretty_whistle on 2012-09-23
> **Sef said:**
> That is correct. You can install one or the other or both on one computer, but upgrading is impossible.
Rats.

I cant seem to find a laptop that is 32bit so its a good thing I can use a disk image of 32 on a 64.
Likewise I can install 64bit and simply copy over everything.

Now all I have to do is decide which one I'll do.  So I'll go ahead and mark this thread as solved.

---

### Post by mayagrafix on 2012-09-23
Is the old PC still running? why not use it as a server for a while, in a bit all of your must have docs will end up on your new machine and you can put the rest in deep storage.

Do a clean install on your new PC. Then using the modem router for your Internet (usually u can hook up more than one box) u can create a home network with both computers. 

64bit is like a six lane highway compared to a two lane road for 32bit. Might as well use it.

---

