---
title: "VirtualBox Help"
date: 2010-04-21
forum: General Help
---

### Post by Flexico on 2010-04-21
OK, I just installed a Windows XP system in VirtualBox, and I'm having a few issues:

1. How do I transfer files between Ubuntu and Windows? (I tried drag-and-drop, and nothing happened.)

2. Some of my USB devices don't work. My mouse, keyboard, and drawing tablet work fine, but my printer and external hard drive aren't detected.

3. When playing "Pinball", I can't launch the ball -- when I hold the plunger button, it just kind of bounces instead of pulling back.

---

### Post by snowpine on 2010-04-21
> **Flexico said:**
> OK, I just installed a Windows XP system in VirtualBox, and I'm having a few issues:

1. How do I transfer files between Ubuntu and Windows? (I tried drag-and-drop, and nothing happened.)

2. Some of my USB devices don't work. My mouse, keyboard, and drawing tablet work fine, but my printer and external hard drive aren't detected.

3. When playing "Pinball", I can't launch the ball -- when I hold the plunger button, it just kind of bounces instead of pulling back.

1. You need to [install guest additions]("http://www.virtualbox.org/manual/ch04.html"), then set up a [shared folder]("http://www.virtualbox.org/manual/ch04.html#sharedfolders").

2. Same thing; install guest additions (and make sure you are using PUEL Virtualbox, not Virtualbox OSE).

3. No idea, sorry. :(

---

### Post by carl4926 on 2010-04-21
> **Flexico said:**
> OK, I just installed a Windows XP system in VirtualBox, and I'm having a few issues:

1. How do I transfer files between Ubuntu and Windows? (I tried drag-and-drop, and nothing happened.)

2. Some of my USB devices don't work. My mouse, keyboard, and drawing tablet work fine, but my printer and external hard drive aren't detected.

3. When playing "Pinball", I can't launch the ball -- when I hold the plunger button, it just kind of bounces instead of pulling back.


[LIST=1]
[*]Read the manual. Setup shared folder in Ub then map the network drive in win explorer
[*]You are using the PUEL version from [http://www.virtualbox.org/](http://www.virtualbox.org/)
[*]No idea
[/LIST]

---

### Post by Flexico on 2010-04-22
Thanks a lot! I got all three fixed. ^_^ Now, however ... 

4. I have no sound or video driver for my Windows XP virtual machine, and I can't find any that work with my HP computer And XP, which only supports Vista forward.

---

### Post by carl4926 on 2010-04-22
The audio settings are in the VBox settings, before you start the virtual machine.
Mine is set to ALSA
try others if necessary

Make sure you have the VBox additions installed - but that's once the machine is up and running

---

### Post by shaka_zulu on 2010-04-22
try here

[http://www.ubuntu-how-to.com/2010/04/virtualbox-ubuntu-how-to-install.html](http://www.ubuntu-how-to.com/2010/04/virtualbox-ubuntu-how-to-install.html)

---

### Post by Flexico on 2010-04-22
Thank you -- sound is a go! But I still get warnings about my graphics drivers being out-of-date when I run some programs. I installed the Guest Additions and gave the virtual graphics card 42 MB. The program that's giving me trouble is called, "Game Maker", and it crashes when I try to compile and run a game -- It's only 2D sprite games, so I don't think it's just too much for the card.

---

### Post by carl4926 on 2010-04-22
> **Flexico said:**
> Thank you -- sound is a go! But I still get warnings about my graphics drivers being out-of-date when I run some programs. I installed the Guest Additions and gave the virtual graphics card 42 MB. The program that's giving me trouble is called, "Game Maker", and it crashes when I try to compile and run a game -- It's only 2D sprite games, so I don't think it's just too much for the card.

Virtual Machine graphics don't come near a real install!

---

### Post by Flexico on 2010-04-22
> **carl4926 said:**
> Virtual Machine graphics don't come near a real install!

I understand that, but why won't the program even run? It should just lag, right? I mean, no video at all is working, even the "coverflow" view in iTunes. I have a good processor and graphics card, 2.4 GHz and 128 MB Nvidia, so I should at least get *something*.

---

### Post by carl4926 on 2010-04-22
I can't really say.
I don't use winders as an OS. I have it installed in Virtual Box and on my HD, but only for testing purposes.
If you point me to the application (wrap any URL in code) - I'll download it and try it for you in my Virtual Machine.

---

### Post by wilee-nilee on 2010-04-22
The video memory should be set to 128 MB. There is a link in the virtual stickies that explains the best set up to get the most from the Vb.

---

### Post by Flexico on 2010-04-22
> **carl4926 said:**
> I can't really say.
I don't use winders as an OS. I have it installed in Virtual Box and on my HD, but only for testing purposes.
If you point me to the application (wrap any URL in code) - I'll download it and try it for you in my Virtual Machine.

[http://www.yoyogames.com/gamemaker/download](http://www.yoyogames.com/gamemaker/download)

OK, you'll need to open up a document (there are a couple examples) and try to compile the program. Thanks for this!

---

### Post by Flexico on 2010-04-22
> **wilee-nilee said:**
> The video memory should be set to 128 MB. There is a link in the virtual stickies that explains the best set up to get the most from the Vb.

Can I do that? I only have 128 MB for my card.

---

### Post by wilee-nilee on 2010-04-22
> **Flexico said:**
> Can I do that? I only have 128 MB for my card.

I am not sure what it means that you only have 128 for your card, I am quite familiar with linux and other OS but I am not a tech, so I don't really have any intrinsic knowledge of hardware and it's limitations, other then I need x amount of ram and x amount of cpu at the least.

---

### Post by carl4926 on 2010-04-22
The Virtual Video memory uses RAM, so yes. Try it first and let us know

---

### Post by wilee-nilee on 2010-04-22
> **carl4926 said:**
> The Virtual Video memory uses RAM, so yes. Try it first and let us know

Thats what I thought, I am just careful when I claim.

---

### Post by Flexico on 2010-04-23
> **carl4926 said:**
> The Virtual Video memory uses RAM, so yes. Try it first and let us know

I got the same error message [attached], with 128 MB (which is the max).

---

### Post by carl4926 on 2010-04-23
I'll try it for you later on mine. But I suspect it doesn't like the Virtual Box graphics driver.

---

### Post by carl4926 on 2010-04-23
It works for me. No error messages.

---

### Post by wilee-nilee on 2010-04-23
So your running Hardy and which vb are you running, and is the XP a legit version or a torrent? here is a link to a legitimate XP download I have run this on the acer I have and other computers it is a slipstreamed sp3 replacement.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
This comes with no key you have to have one.

---

### Post by Flexico on 2010-04-23
> **wilee-nilee said:**
> So your running Hardy and which vb are you running, and is the XP a legit version or a torrent? here is a link to a legitimate XP download I have run this on the acer I have and other computers it is a slipstreamed sp3 replacement.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
This comes with no key you have to have one.

It's a legit Windows, but I haven't gotten the key in yet because I have a "Basic" disk and a "Pro" key -- but thanks for the link, I now have a Pro ISO to burn! =D

---

