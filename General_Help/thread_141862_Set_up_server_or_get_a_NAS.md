---
title: "Set up server or get a NAS?"
date: 2006-03-09
forum: General Help
---

### Post by jacrider on 2006-03-09
I have many users and computers in our household.  Many different operating systems:  Ubuntu, OSX, XP, Win2K.  Both parents and teenagers creating lots of data and in need of better print sharing.

One alternative I am considering is using a machine I have that is not currently in use as a Ubuntu server.  Use Samba to set up home directories for everyone on the server, have two hard drives to mirror for back-up purposes and use the print serving facilities.  Only downsides are additional power usage and the need for a couple of hard drives.  Probably fairly complicated from what I understand about setting up Samba.

Another alternative is to use a NAS device.  I have found one from Buffalo Technologies that serves all of Linux, Mac and Windows and has printer sharing as well.  I think this reallys mean the HD is formatted as a FAT32.  Not to pricy for 250GB at $275 Canadian.  Probably won't give me the ability to set-up home directories, and no mirror capabilities.  Not really a concern as I can plug in a USB HD to it as the back-up device.

Should I be afraid of setting up Samba, or should I choose the easy route?

All and any suggestions welcome.

Thanks.

---

### Post by KnottyMan on 2006-03-09
Samba is cake.  Home directories are already set up as a dynamic share.  So you only have to define any common shares.  And I think there's already one example in the conf file.

Anyway, it's totally easy.  Samba also has really good docs if you get stuck.  

I serve 2T at home via samba for xbox, winxp, and ubuntu clients.  And another 2T at work for 120 winxp clients.

---

### Post by jstueve on 2006-03-09
Have I've done is use the Linksys NSLU2 as a pseudo server.  [http://www.nslu2-linux.org](http://www.nslu2-linux.org) has instructions to re-flash a custom firmware image, and if you have access to a linux box (to compile the custom firmware image) you can even get debian running on the slug.

Benefits:
 - lower power consumption than a full blown server
 - more customizable than a NAS 
 - even out of the box it meets the same specs as a NAS (the original firmware uses SAMBA as the server)
 - The USB drives have to be reformatted for the original firmware, but with custom firmware, you can set it up to run the OS off a flash drive, and run the shares off of any hard drive partitions that linux can read.

Plus it is a fun hacking toy. :)

---

### Post by JimJones56 on 2006-03-09
Seconding the NSLU2 - it's a great hacking toy. I got debian running on it and my linux experience is *limited*, to say the least. Overclocking it (to run at twice the factory-set speed) is also very simple, just cut/desolder/smash a single resistor. I've worked with thousands-of-pounds NAS boxes before and I think this £50 box is the perfect home-NAS solution.

---

### Post by jacrider on 2006-03-09
I spent some time looking at the Linksys device and while I do like playing with neat technology (which I think this is) I don't think it handles print serving, which I really need to get under control.

Are there any great HOWTO's on setting up a Samba installation?

Most of the one's I have seen are fairly advanced ... perhaps assuming more knowledge than I have right now.

Thanks.

---

