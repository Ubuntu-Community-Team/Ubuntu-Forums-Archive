---
title: "Touchpad &quot;disappeared&quot; on HP Mini"
date: 2010-07-25
forum: General Help
---

### Post by SamH on 2010-07-25
I upgraded my HP Mini 1120 to 10.04. Everything seemed fine, then after a few days, the touchpad quit working. In the mouse preferences dialog the touchpad setting tabs have disappeared.

I tried uninstalling gpointing-device-settings then reinstalled it. No joy.

Any suggestions?

Thanks,

---

### Post by PaulReaver on 2010-07-26
that one comes with a synaptics touchpad, doesn't it?

my synaptics pad still works after the updates. 
You may have had a hardware failure, you could boot up a live cd and see if it still works.

---

### Post by SamH on 2010-07-26
Ahh....just found and installed the **tpconfig** package that I hadn't tried before.  Installed it and ran it from console as **sudo**.  Pad is back, touchpad tab is back in mouse pref dialog.

Thanks,

---

### Post by SamH on 2010-07-26
Paul,
**tpconfig** ID'd it as a Synaptics unit.

Thanks for your reply.

---

### Post by schulznotee on 2010-08-17
I have the same problem with the touchpad (TP)... it just flat out disappeared last evening. Compaq Presario C500, however. 

Opened Terminal, typed "sudo tpconfig" (as per suggestion here) and got a response of "Found Synaptics Touchpad. Firmware: 8.96 (multiple-byte mode)." 

So, the software knows the TP is there but it doesn't work and there are NO TP tabs anywhere on Mouse, Pointing devices, etc.

Is there some equivalent of MS XP's Device Manager where I can see what hardware this system is working with?

I'm kind of a dweeb on this stuff so, please, be gentle!

---

### Post by schulznotee on 2010-08-17
Oh... I'm using version 10.04, not 8.10

---

### Post by schulznotee on 2010-09-07
Gee, thanks for all the help guys. I guess the rest of you are stumped too, right?

---

### Post by cloyd on 2010-11-06
I had my touchpad stop working today. I did not lose the buttons in mouse manager, it just didn't work. 

A little background. I had installed a "theme" called Macbuntu that really overhauled Gnome. The whole machine shut down and wouldn't boot. As a final act of desperation, I turned the machine off and pulled out the battery. 

It booted.

Worked with it a while. Uninstalled Macbuntu. But before I got it uninstalled, the touch pad just quit. A usb mouse worked, but not the touch pad.  Just about gave up, then, again, I shut it down, and took out the battery. It worked. I have no idea, but the machine did occasionally do squirrelly things with Macbuntu. Finished uninstalling Macbuntu, and I'll see how it works from there.

This was not an hp, but a Gateway netbook running 10.04 (not the netbook edition)

---

