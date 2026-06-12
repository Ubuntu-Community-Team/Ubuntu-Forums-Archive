---
title: "Upgrade advice? I want to save some settings and etc"
date: 2009-10-28
forum: General Help
---

### Post by blueridgedog on 2009-10-28
I have an 8.10 setup that I have used for the past year with delight and enjoyment.  It is setup perfectly, customized to my needs and I want for nothing in my computing world.  I manage multiple ipods, email accounts and music collections with ease.  I have an Intel Quadcore CPU and 4 gig of RAM so I am inclined to upgrade to 9.10 and go to 64 bit at the same time now that firefox and flash have their 64 bit issues resolved.  

I am thinking that his is a format of /.  That is OK, as I have all of my files on a different partition and links to my folders in my /home/user location.  I can backup my home directory but I am concerned with what might happen after I restore it.  I have some virtual machines that I want to save (Sun Virtualbox).

So, I install 9.10 64bit, put all the restricted extras on that I use, then mount my /documents drive and restore my /home/user directory...then what is required to get my virtual machines working and ????

Or....am I a fool to mess up a perfectly working system and should I ride 8.10 until I have no other choice?

---

### Post by bendib on 2009-10-28
64 bit is not all that great. Apps are not as easy to find for 64bit. But you can upgrade to 9.10 if you want. You do not have to format the system at all, or risk the loss of one file. Just hit ALT-F2 and run update-manager -d Avoid updating until the 29th of October (tomorrow) or you will get the RC version. When update manager comes up, there should be a message saying "a new distribution release 910 is available." and next to it a button that says upgrade. Click upgrade. This will take some serious bandwidth, but it's sure easier. Hope this helps, Ben.

---

### Post by fluffman86 on 2009-10-28
I'll have to disagree with bendib on several points:

1. 64 bit is *MUCH* faster, at least on my computer.  Plus, you'll finally get to use all 4 gigs, instead of 3.5 or whatever you're limited to now.

2. Programs are *NOT* harder to find, because if necessary you can manually install a 32 bit program (which is rare--the only one I've had to do since going 64-bit 2 years ago was Amazon mp3).  Just ask here for how to do it, or google it. :P

3. If you do an upgrade, you'll have to upgrade to 9.04 first, which will take a few hours, and *THEN* upgrade again to 9.10 tomorrow.  That leaves a lot of wiggle room for stuff to go wrong.

4. If you upgrade, you'll miss out on ext4, which provides (for me, at least) a *MASSIVE* performance gain.  Faster boot, faster application launches, happier me. :)

That said, here's what I would do:

1. Back up all of your files to an external hard drive.  In your home folder, just hit ctrl+H and be sure to get all of the .hidden files.

2. Once you're sure you have everything, do a *FULL* format and reinstall with 9.10.  This is the only way to take advantage of the ext4 improvements.

3. Unfortunately, you'll need to reinstall some programs, but that's a small price to pay.

4. Recover stuff from your old, backed up /home directory sparingly.  There's some new features and widgets that are saved in areas like ~/.local and ~/.gnome2 that you *DON'T* want to replace with your backups.  Instead, just get the important stuff like .evolution, .mozilla, .ssh, .gnupg, and of course Documents, Desktop, Music, Pictures, etc.

5.  I'm pretty sure all of your virtual machines are saved in ~/.virtualbox but it's been a while since I've used it.  Double check on this before proceeding.

---

### Post by blueridgedog on 2009-10-31
Am I correct in thinking that a reinstall is required to go to 64 bit?  

Also, can anyone comment if floola, handbrake and k9copy work well in 64 bit?

---

### Post by fluffman86 on 2009-10-31
Yes, you must reinstall to go 64bit.  But there's lots of reasons to reinstall anyway, and 64bit rocks. :)

I can guarantee that handbrake works well.  They offer a 64bit version on their website, and since it's compiled with 64bit support, it runs WAY faster.

I've never had any luck at all with k9copy or others, but since it's in the repositories it has 64bit support, again, running faster.  I usually just install dvdshrink under wine, though, which works well. 

It looks like floola is a 32bit cross platform binary, which means that yes it will work on 64bit.  You can still run 32bit programs on 64bit ubuntu.

I never really liked floola, so I manage my iPod with Banshee, which handles music, podcasts, and video, and even automatically converts music files to mp3 if they aren't already.  Rhythmbox is installed by default and it will manage the music on your iPod.  gtkPod is more powerful, and handles pretty much everything and iPod can do.

---

