---
title: "Flash issues"
date: 2009-10-25
forum: General Help
---

### Post by jhb1608 on 2009-10-25
Hello, I have issues on Flash, I can view anything, BUT I encountered a problem: "(insert any website here) need to access the webcam. Do you accept? Allow or Deny" dialog, but I tried ot click accept, nothing happens!

What shall I do to solve this issues?

---

### Post by mgmiller on 2009-10-25
There is a known bug with flash not accepting mouse clicks for its settings with 64 bit Ubuntu.  It uses the nspluginwrapper to support the 32 bit flash and it gives this behavior if compiz is enabled.

Try turning off desktop effects and see if the problem persists.
System > Preferences > Appearance  go to the "Visual Effects" tab and select "None".

---

### Post by jhb1608 on 2009-10-25
> **mgmiller said:**
> There is a known bug with flash not accepting mouse clicks for its settings with 64 bit Ubuntu.  It uses the nspluginwrapper to support the 32 bit flash and it gives this behavior if compiz is enabled.

Try turning off desktop effects and see if the problem persists.
System > Preferences > Appearance  go to the "Visual Effects" tab and select "None".

it is off. and I don't have compiz installed and my ubuntu 9.04 is 32bit.

---

### Post by jhb1608 on 2009-10-25
well, still not working. I use wired, not wireless.

---

### Post by jhb1608 on 2009-10-25
what is the other way to fix that issues? by using gnash or something?

---

### Post by mgmiller on 2009-10-25
The only other things I can think of are:

1) A video driver issue.  What video card do you have and what driver are you using?

2) Multiple versions of flash are installed.  Check to make sure you don't have gnash installed.  Only the adobe-flashplugin should be installed. 

You could also use flashplugin-installer, which will install the exact same version of flash as the adobe-flashplugin package.

The main thing is to only have 1 version of flash installed.

---

### Post by jhb1608 on 2009-10-25
> **mgmiller said:**
> The only other things I can think of are:

1) A video driver issue.  What video card do you have and what driver are you using?

2) Multiple versions of flash are installed.  Check to make sure you don't have gnash installed.  Only the adobe-flashplugin should be installed. 

You could also use flashplugin-installer, which will install the exact same version of flash as the adobe-flashplugin package.

The main thing is to only have 1 version of flash installed.

ok then how do I look on my video? it is not a video card, it is the motherboard on intergated video.

plus how do I look on the flash package that is installed?

---

### Post by mgmiller on 2009-10-25
> ok then how do I look on my video? it is not a video card, it is the motherboard on intergated video.

First, open a terminal:
Applications > Accessories > Terminal

Enter the following command to display which vdeo card you have:
 ```
 lspci -x | grep -i "vga\|display"
```

That will tell us what card you have.

Take a look in System > Administration > Hardware Drivers
Give it a few seconds to run and it will tell us if any proprietary drivers are available and if you are using them.

> plus how do I look on the flash package that is installed? 	

Fire up System > Administration > Synaptic Package Manager

In the Quick search box, type "flash" (without the quotes).

It should give you a list of things.  Only look at the ones that have a green square next to them.  Post that list here.

In my system, the only things that come up green are:
flashplugin-installer
swfdec-mozilla
libswfdec-0.8-0

I have no problems with flash in my 32 bit installation.

---

### Post by jhb1608 on 2009-10-25
> **mgmiller said:**
> First, open a terminal:
Applications > Accessories > Terminal

Enter the following command to display which vdeo card you have:
 ```
 lspci -x | grep -i "vga\|display"
```

That will tell us what card you have.

Take a look in System > Administration > Hardware Drivers
Give it a few seconds to run and it will tell us if any proprietary drivers are available and if you are using them.



Fire up System > Administration > Synaptic Package Manager

In the Quick search box, type "flash" (without the quotes).

It should give you a list of things.  Only look at the ones that have a green square next to them.  Post that list here.

In my system, the only things that come up green are:
flashplugin-installer
swfdec-mozilla
libswfdec-0.8-0

I have no problems with flash in my 32 bit installation.

Alright. I installed, and I see no drivers install for video display driver... I don't understand.

```
jason@jason-desktop:~$ lspci -x | grep -i "vga\|display"
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
jason@jason-desktop:~$ 

```

---

### Post by mgmiller on 2009-10-25
OK, you have a VIA onboard video card from this family: 
CN896/VN896/P4M900

There are no proprietary drivers available for this card, that is why Hardware drivers came up blank.  You are using the open source driver built into the Linux kernel.

This type of video card has limited capabilities.

Have you checked in Synaptic to make sure only the flash packages I mentioned are installed?

If so, that's about all you can do.  As far as I know.  It's a limitation in your video card (or in the open source driver that runs it).

It's possible that this will be fixed in future releases.  Have you tried Ubuntu 9.10 yet?  There are a lot of updates in there that may resolve your problem.  

Try running it from a live CD and see if it works.  You can install flash in the live CD session.

---

### Post by jhb1608 on 2009-10-25
> **mgmiller said:**
> OK, you have a VIA onboard video card from this family: 
CN896/VN896/P4M900

There are no proprietary drivers available for this card, that is why Hardware drivers came up blank.  You are using the open source driver built into the Linux kernel.

This type of video card has limited capabilities.

Have you checked in Synaptic to make sure only the flash packages I mentioned are installed?

If so, that's about all you can do.  As far as I know.  It's a limitation in your video card (or in the open source driver that runs it).

It's possible that this will be fixed in future releases.  Have you tried Ubuntu 9.10 yet?  There are a lot of updates in there that may resolve your problem.  

Try running it from a live CD and see if it works.  You can install flash in the live CD session.

I'll rather wait until 9.10 comes out, it will come out in 4-5 days.

---

### Post by jhb1608 on 2009-10-25
> **mgmiller said:**
> OK, you have a VIA onboard video card from this family: 
CN896/VN896/P4M900

There are no proprietary drivers available for this card, that is why Hardware drivers came up blank.  You are using the open source driver built into the Linux kernel.

This type of video card has limited capabilities.

Have you checked in Synaptic to make sure only the flash packages I mentioned are installed?

If so, that's about all you can do.  As far as I know.  It's a limitation in your video card (or in the open source driver that runs it).

It's possible that this will be fixed in future releases.  Have you tried Ubuntu 9.10 yet?  There are a lot of updates in there that may resolve your problem.  

Try running it from a live CD and see if it works.  You can install flash in the live CD session.

Also... I think I can get a graphics card next month, but I still have hard time deciding.

---

### Post by jhb1608 on 2009-10-25
Will this link (guide) work?

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by jhb1608 on 2009-10-25
Maybe I can just get a video card and install and get 9.10 and upgrade? Oh, yes. Which graphic cards that support 3D?

---

### Post by fluffman86 on 2009-10-25
> **jhb1608 said:**
> I'll rather wait until 9.10 comes out, it will come out in 4-5 days.

I would actually recommend against that.  Everything is pretty much set in stone now that we have the release candidate available.  And once the final version comes out, the servers are going to be hammered, and it will take FOREVER to download.  Easier just to get it now. :P

---

### Post by jhb1608 on 2009-10-25
> **fluffman86 said:**
> I would actually recommend against that.  Everything is pretty much set in stone now that we have the release candidate available.  And once the final version comes out, the servers are going to be hammered, and it will take FOREVER to download.  Easier just to get it now. :P

well I'd rather have the stable Ubuntu than unstable Ubuntu. if I get unstable Ubuntu, then it makes things harder. It's why I am waiting for 9.10 to come out and I'll download no matter what you say. I like the patience and waiting. Stability is more important than testing.

---

### Post by jhb1608 on 2009-10-25
Oh, and also, which video card I need ot get? Do there is a list of supported hardwares somewhere in this website or what?

---

### Post by nu2this on 2009-10-26
Get a card made by nvidia.

---

### Post by jhb1608 on 2009-10-26
ok I'm writing this down, thanks!

---

