---
title: "Ubuntu Desktop 12.04 Install Problem"
date: 2012-07-20
forum: General Help
---

### Post by Duubztep on 2012-07-20
First off I need to say, if this post is in the wrong section I am sorry, and admins, feel free to move it.

So... This morning I woke up to find that my Windows 7 Ultimate PC stopped working on me! It wouldn't boot, I tryed startup repair, system restore, and a bunch of other stupid fixes. But none of them worked! So then I thought, why not use Ubuntu? I use Ubuntu on my netbook, and it's alot better that Windows! So I did!

At first I mounted Ubuntu Desktop 12.04 32-bit onto a 2GB flash drive (with Universal USB Installer), and when I went to boot it off my desktop PC, it went to the Ubuntu welcome screen, as it should.

[IMG]http://s10.postimage.org/stfx8y82x/IMG_0060_1.jpg[/IMG]

BUT (there's always a but), when I choose either 'Run Ubuntu from this USB', or 'Install Ubuntu on a Hard Disk', it takes me to a command prompt (or terminal). Now here is where I am getting my first problem. As you can see from the image below, the process freezes at the end. 

[IMG]http://s8.postimage.org/t4ntlr2b9/IMG_0059_1.jpg[/IMG]

Now I can't specify what it stops at, because it's different every time. At first I thought the problem was that Ubuntu could install the driver for my Microsoft wireless mouse & keyboard. So I disconnected the adapter, and plugged in a wireless mouse & keyboard, and then booted Ubuntu again. But nothing changed! So then, I opened up my pc to see if it was anything to do with that. I disconnected my graphics card, memory, hard drive, cd drive, and reconnected them, and nothing changed when I booted Ubuntu! So then, I thought it may be something to do with the usb, so I used a different one. But that didn't work! So then, I tryed using a DVD-R to install Ubuntu. But the problem still consists! So (it's like i'm writing a freaking novel!), then I tryed the USB with Ubuntu Desktop 12.04 64-bit. It still didn't work.

At this point, as you probably would be, I was getting pee'd off. So I really really need your help! If anyone could give even the slightest piece of information or help I could use to get my PC back up and running, you would be sooo awesome!

Thanks,
Will (Duubztep)
{email removed}
[EMAIL="duubstepx@gmail.com"][/EMAIL]

---

### Post by oldfred on 2012-07-20
Welcome to the forums.

Deleted email, best to post in forum. Occassional use PM, but if you have your email you will get spammed to death.

What hardware? Old, new specs if available?

Often a video issue, sometimes other issues.

From advanced options try the nomodeset option.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Duubztep on 2012-07-20
> **oldfred said:**
> Welcome to the forums.

Deleted email, best to post in forum. Occassional use PM, but if you have your email you will get spammed to death.

What hardware? Old, new specs if available?

Often a video issue, sometimes other issues.

From advanced options try the nomodeset option.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Sorry, but I am fairly new to Ubuntu and I do not understand half of what you said :(
Could you explain to me what I have to do to get my PC up and running with Ubuntu?
Sorry for being a noob :)

---

### Post by Duubztep on 2012-07-20
Sorry, but I am fairly new to Ubuntu and I do not understand half of what you said 
Could you explain to me what I have to do to get my PC up and running with Ubuntu?
Sorry for being a noob

---

### Post by oldfred on 2012-07-20
What model computer is it? Do you know video processor chip or board?

The links give details on how to add nomodeset as a boot option. From the menu you posted you can use the Advanced Options which should let you add it for the liveCD or USB, but then it will be different after you install.

---

### Post by Duubztep on 2012-07-21
> **oldfred said:**
> What model computer is it? Do you know video processor chip or board?

The links give details on how to add nomodeset as a boot option. From the menu you posted you can use the Advanced Options which should let you add it for the liveCD or USB, but then it will be different after you install.
Ah! The nomodeset boot option has got it working! Thank you so much! I will set the post to [SOLVED] now! Cheers, again!

---

