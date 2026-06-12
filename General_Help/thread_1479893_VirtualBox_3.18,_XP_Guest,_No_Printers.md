---
title: "VirtualBox 3.18, XP Guest, No Printers"
date: 2010-05-11
forum: General Help
---

### Post by timgood on 2010-05-11
Hi Guys

I'm using the newest VB 3.18 Lucid AMD64 .deb downloaded from Sun. Previous versions have not had USB support in Lucid. Now, when I start the XP guest, all my USB devices seem to be detected. My USB phone is shown as 'busy' as is my mouse. However, both my printers remain greyed out and are shown as being 'unavailable'. I have tried manually adding the printer filters before starting the guest, but no dice. Is anyone else having this problem? Any ideas as to a possible cause?

Thanks for your time.

---

### Post by timgood on 2010-05-11
Hmm - while it seems that there are many posts about lack of USB support in VirtualBox 3.17 under Lucid, many people seem to be getting 3.18 to work OK with XP. Can anyone confirm that USB works in VB 3.18 for them under Lucid?

---

### Post by Detonate on 2010-05-11
How I got my printers working in Virtualbox.

Make sure your XP install and Lucid are both members of the same workgroup.

Make sure your printers are "Shared" in Lucid, and make sure your Server Settings are set to show the shared printers.

In XP, open Printers and Faxes and select "Add Printer".

Choose to add a network printer.

Browse for printers.

Your printer should show up.

Select it and install it.  You may have to provide the driver if it is not in the list.

---

### Post by seenthelite on 2010-05-11
> **timgood said:**
> Hmm - while it seems that there are many posts about lack of USB support in VirtualBox 3.17 under Lucid, many people seem to be getting 3.18 to work OK with XP. Can anyone confirm that USB works in VB 3.18 for them under Lucid?
 
I have 3.18 installed on 64 bit 10.04 and everything is working including USB.

---

### Post by timgood on 2010-05-11
Thanks for this Floyd - I can confirm that I can now print over the network! Still don't know why the USB printing is not working though - but at least I now don't have to reboot into Gate's territory. I would still like to get my USB printers working normally, as the network printing is a bit slow. Someone on the VBox forums suggested that I add my logon to the lp group - have done that but no dice. I had this problem in the Beta as well. Running VB as root makes the printers accessible, but I can't see where there is a permission problem. Help me out guys!

---

### Post by cheaka on 2010-05-13
I had a very similar problem on upgrading to 3.1.8 where some (but not all) USB devices were greyed out for my user account (but not for root). This was on Karmic.

The problem in the end was that the Vboxdrv kernel module didn't get built and installed properly during the upgrade to 3.1.8 (possibly because I hadn't rebooted since a kernel update??). Anyhow, after my next reboot, I got an informative error message when I ran VirtualBox from the command line, telling me that I needed to run an install script. I ran that, it compiled and installed the Vboxdrv kernel module, and I was off to the races.

Hope this helps. 
Tom

PS, in my troubleshooting, I found the 'VBoxManage list usbhost' command to be really helpful. Devices that would be grayed out in a guest machine are listed as 'Unavailable', rather than 'Available', or 'Busy'. This saves you time spent starting up your VMs over and over.

---

### Post by timgood on 2010-05-14
Thanks for this Tom. I was going to follow your advice, and started VB up this morning. For no apparent reason, everything is now working. It wasn't yesterday, but it is today. I can't figure this out!

---

### Post by encurto on 2010-06-26
Hi! this is how I solved the "grayed out usb" problem on Ubuntu 10.04 64 bits
[http://ubuntuforums.org/showthread.php?t=615847](http://ubuntuforums.org/showthread.php?t=615847)

[I]
In host machine go to system -->Administration---->Users and Groups

click on 'manage groups'

Scan down the list, there should be a group called 'vboxusers'.  If  there is, double click on it and make sure that your username is ticked  so that you are a member of the group.  If there is no group, create one  by clicking on 'Add Group', typing vboxusers in the group name field  and making sure that your user name is ticked so that you are a member.   Then, restart the host machine.  When you a start your virtual  machine, everything should work!

Good luck![/I]

---

