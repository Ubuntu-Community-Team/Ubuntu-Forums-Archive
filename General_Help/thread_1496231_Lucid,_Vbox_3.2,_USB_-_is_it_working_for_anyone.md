---
title: "Lucid, Vbox 3.2, USB - is it working for anyone?"
date: 2010-05-29
forum: General Help
---

### Post by infinitejones on 2010-05-29
I know there are a million threads on Ubuntuforums about older versions of Ubuntu and Vbox, but I just can't get my Windows XP virtual machine to recognise USB connections, eg. from my Nokia N95. It's definitely worked in the past but not currently.

Lucid is the host and it's the "full" (ie. not open source) edition of VBox 3.2.

I've set up the filter for the N95 in the settings for the virtual machine, but when I connect the phone, it won't recognise it, no matter whether I'm telling the phone to connect in PC Suite mode or Mass Transfer mode. That's what I use to mount it directly in Ubuntu, which works fine.

This page [https://help.ubuntu.com/community/VirtualBox/USB]("https://help.ubuntu.com/community/VirtualBox/USB") tells me what not to do, and all the other threads I can find here and elsewhere online are for older versions of Ubuntu and Vbox.

Has anyone done it (not just for a Nokia N95, but for any usb device) and if so, can you point me in the right direction?

---

### Post by dcstar on 2010-05-29
> **infinitejones said:**
> I know there are a million threads on Ubuntuforums about older versions of Ubuntu and Vbox, but I just can't get my Windows XP virtual machine to recognise USB connections, eg. from my Nokia N95. It's definitely worked in the past but not currently.
........

VM questions belong in the Virtualization forum.

---

### Post by John Bean on 2010-05-29
I can't really help - my VB 3.2 worked perfectly after installing it in a (clean install) Lucid. I use it with a number of USB devices, all work.

Was your Lucid a clean install or an upgrade? If the latter there may be something still lurking from the earlier version that's upsetting it.

Finally make sure you have the latest version of 3.2 from the Lucid repository, all but the latest version won't work on systems without both hal and usbfs.

---

### Post by rogerdean on 2010-06-01
it's not working for me. I have a new install of Lucid but a VirtualBox profile folder inherited from many versions ago...

---

### Post by davidmohammed on 2010-06-01
... have you looked to make sure you are in the vboxusers group (administration - users & groups)?

---

### Post by Ginsu543 on 2010-06-02
I just upgraded to 3.2 from 3.1.8 (in fact, I didn't know 3.2 was available until I read this post) and everything worked for me out of the box as well (as it has for every single version I've tried). I too run a Windows XP client on my Lucid host to run iTunes to sync my iPhone. All I had to do was uninstall the previous version using Synaptic, download the appropriate .deb file from the VirtualBox website, and install using GDebi. 3.2 immediately recognized my virtual drive and booted XP.

---

### Post by subodh.rohilla on 2010-06-02
Add yourself in vboxusers group (administration - users & groups)
and if you are still getting HAL error , try this link :-

[https://answers.launchpad.net/ubuntu/+question/103523](https://answers.launchpad.net/ubuntu/+question/103523)

---

### Post by pwebster25 on 2010-06-22
This same thing appears to affect me.  I have a host system that I upgraded from Karmic to Lucid.  I had some bugs after the upgrade, mostly related to domain join and likewise open (I should have left the domain and uninstalled lw-open before upgrading).

I had some other permissions problems on login to gnome and I cleared those up by deleting my users /home folders.  I then logged in again and let gnome create a new /home folder for my user.  This may or may not be related to my problems with usb on vbox.

Ubuntu recognizes all of my usb devices and vbox recognizes them as well (there names are all in grey down in the usb icon at the bottom of the window).  However, their status says "unavailable" and you can't select them to activate them like you should be able to do.

I tried the groups check and the hald instructions above.  On the "groups" I didn't come up with vboxusers when I ran it BUT when I added myself it said I was already a member of that group.  I am a domain user so I can't often check in traditional ways.  My domain user account is DOMAIN_NAME\username

Any more ideas?  I am thinking that I got some junk left over from the previous vbox installation.  I wonder if I make a copy of my .vdi virtual disk and then delete my .virtualbox folder if I can let vbox automatically re-create a folder that might have the proper settings in it.  Then I could re-install from my previous .vdi file.  I have really loved virtualbox but I am starting to look at vmware player.  Any opinions?  Does the free version support usb?

This is pretty critical, as I am the only linux user in an entirely windows work environment so I need to start up windows occassionally to make quirky things work.

Thanks
Paul

---

### Post by Vege 4wd on 2010-06-27
I have exactly the same problem with a clean install of lucid.

---

### Post by Vege 4wd on 2010-06-27
Just used the link from #7. Usb now working. Thanks that fixed it.:p

---

