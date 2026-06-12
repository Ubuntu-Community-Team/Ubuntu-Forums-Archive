---
title: "Mouse Stops Working"
date: 2011-01-26
forum: General Help
---

### Post by alimadari on 2011-01-26
I'll try to explain myself as best as I can. Today is the first time  I've ever used an operating system other than Windows. I am familiar  with OS X also because I've used it for long periods of time. Because of  this, if you suggest a solution, please try to explain yourself more so  I know exactly what to do. I would really appreciate it.
 
So, on to the problem. 
 
I downloaded Ubuntu 10.10 today and wrote it onto a CD. I booted it and  went into the OS to try it and see if I would like to install it. I  could use my wireless mouse and keyboard fine for a minute or two. Then,  my mouse would fail completely, with no response whatsoever. My  keyboard was still working fine.
 
However, I decided to install the OS to see if that fixed it. I used the  Wubi method (it came with the 10.10 Desktop Download) to install it so I  could decide which OS to boot, and I wouldn't lose all my data.
 
But the problem did not go away. I even tried to use a wired mouse. It  would still fail after a minute or two of use. The red light at the  bottom of the mouse stayed on, and the only solution was a reboot.  Replugging did not work. 

My wireless keyboard is a "Microsoft Wireless Keyboard 1000 Model 1356"  and my wireless mouse is a "Microsoft Wireless Optical Mouse 2000 Model  1067". They came as one keyboard + mouse combo and they connect using a  "Microsoft Wireless Desktop Receiver 3.1 Model 1028". 
 
Here is a link: [Microsoft Wireless Media Desktop 1000 Review - Keyboards - CNET Reviews]("http://reviews.cnet.com/keyboards/microsoft-wireless-media-desktop/4505-3134_7-33186663.html")
 
I really need some help with this because I really want to use Ubuntu. Does anyone have any solutions?

P.S. The editing menu.lst won't be possible anymore because there is no longer a menu.lst.

---

### Post by Smart Viking on 2011-01-26
What is the name of your computer model?

---

### Post by alimadari on 2011-01-26
> **Smart Viking said:**
> What is the name of your computer model?

I have an Acer AST160-UA352H. I have done a few upgrades to it.

I have 1.5GB RAM and a 1 TB hard drive with an ATI Radeon HD 2600 XT graphics card.

---

### Post by alimadari on 2011-01-26
Bump. :(

---

### Post by Krytarik on 2011-01-26
> **alimadari said:**
> 
P.S. The editing menu.lst won't be possible anymore because there is no longer a menu.lst.
Do you mean the Grub config? Why would you like to edit it?

As of now Grub2 is installed by default, it has a completely different structure:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I've done a short web search on the matter, and it seems that there was bit different issue with a previous version of your receiver, and an older kernel:
[http://ubuntuforums.org/showthread.php?t=438112](http://ubuntuforums.org/showthread.php?t=438112)

Try to set the at least the model of your keyboard in "System -> Preferences -> Keyboard", but I doubt that it fixes it.

---

### Post by alimadari on 2011-01-26
> **Krytarik said:**
> Do you mean the Grub config? Why would you like to edit it?

As of now Grub2 is installed by default, it has a completely different structure:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I've done a short web search on the matter, and it seems that there was bit different issue with a previous version of your receiver, and an older kernel:
[http://ubuntuforums.org/showthread.php?t=438112](http://ubuntuforums.org/showthread.php?t=438112)

Try to set the at least the model of your keyboard in "System -> Preferences -> Keyboard", but I doubt that it fixes it.

Thanks for the reply. :)

I did some Googling and I found that in all the threads I found, people said to add something to a line in the menu.lst file. Unfortunately I can't do that in 10.10.

The keyboard isn't the problem. It works fine. It's the mouse that keeps disconnecting. Any other solutions?

---

### Post by Krytarik on 2011-01-26
> **alimadari said:**
> Thanks for the reply. :)

I did some Googling and I found that in all the threads I found, people said to add something to a line in the menu.lst file. Unfortunately I can't do that in 10.10.

What exactly do they propose to add?
> **alimadari said:**
> The keyboard isn't the problem. It works fine. It's the mouse that keeps disconnecting. Any other solutions?
Yeah, I got that. But as you know, they share the same receiver, so checking that option wouldn't hurt.

---

### Post by alimadari on 2011-01-26
> **Krytarik said:**
> What exactly do they propose to add?

Yeah, I got that. But as you know, they share the same receiver, so checking that option wouldn't hurt.

They say to open up menu.lst and look for the line "# defoptions=quiet splash" and add "acpi=force irqpoll" to end of that line, then update the grub.

---

### Post by Krytarik on 2011-01-26
You can add those option in the new config file of Grub2: /etc/default/grub , as described in the guide I posted earlier.

Add it there to the entry "GRUB_CMDLINE_LINUX_DEFAULT".

After that, as mentioned, do:
```
sudo update-grub
```

---

