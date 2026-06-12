---
title: "Restart doesn't restart"
date: 2011-12-16
forum: General Help
---

### Post by morhin on 2011-12-16
[SIZE=2]I searched for restart issues and didn't find mine so I'll put it out there.
When I hit **restart** 10.04 shuts down and _*does not*_ restart.
So I hit the power button and the only thing that starts is the fan on my Aspire 5250 and then I can't turn it off.
Resolution: turn the laptop over, pull the battery, and put it back in.
Power it up and 10.04 starts like nothing ever happened.
Now that's what I call a resolution. But when other people see me do it they look at the Ubuntu sticker on my laptop and shake their heads. Wonder what they're thinking?

Anyone have a different resolution besides yanking the battery or not using restart?

thx[/SIZE]

---

### Post by zero2xiii on 2011-12-16
Hay,

Hit a F* key during the "shutdown" and see if the terminal gives any hint.

Also try rebooting from a terminal or shutting down from a terminal and see if any error messages are printed... 

I had a issue with my drive not unmounting during shutdown to to a missconfig in bios. Might be similar. But view the outputs and see.

CHerz

---

### Post by morhin on 2011-12-28
Thx for the reply and I apologize for taking so long to get back.

I tried your suggestions and did not get an error message.

I searched and found this is an old issue. Never did find a resolution. 

I'll not use restart as it's not that hard to shut down and come back in. 

Again, thx for the reply.

---

### Post by jri48858 on 2011-12-30
> **morhin said:**
> Thx for the reply ... 
I'll not use restart as it's not that hard to shut down and come back in.  ... 

Maybe there is a simple fix. Setting up my son's Acer Netbook I was having the same problem -- restart didn't restart. But I found a fix (following a suggestion from fabio.hipolito), by adding the option "reboot=bios" to GRUB_CMDLINE_LINUX in /etc/default/grub

A [Novell document]("http://www.novell.com/support/viewContent.do?externalId=7009779&sliceId=1") spells out the options for "reboot" and my sense is that different options will work with different machines.


--------
Here are more details, including how to edit the GRUB file (from fabio.hipolito's post):

 add the option "reboot=pci" to GRUB_CMDLINE_LINUX in /etc/default/grub

to do this Code: sudo gedit /etc/default/grub
look for GRUB_CMDLINE_LINUX=""
and change it to  GRUB_CMDLINE_LINUX="reboot=pci"
save, exit and update grub
Code: sudo update-grub

---

### Post by morhin on 2012-01-26
Sorry it took so long to get back, however, since my last post I have had some updates and the problem seems to be fixed. Restart does restart.
Thanks for everyones input on this.

Morhin

---

