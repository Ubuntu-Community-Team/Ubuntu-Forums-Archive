---
title: "Hosed Install??"
date: 2010-04-02
forum: General Help
---

### Post by Jeffster999 on 2010-04-02
Hello all, Here is what I have done...

I successfully set-up a dual bot system on my laptop and feeling a bit confident I decided to do the same my desktop. I installed a 1 TB WDC drive in the machine, partitioned it to 3 partitions ( M:,P:, L: ) formatted the partitions to NTFS and thought I was ready...Keep in mind there is another HDD ( C: ) on which Win XP is installed.

Initially, I installed wubi (before reading about it enough) and realized I did not want that type of install. I then installed from the CD (btw ver 9.10) and went through the steps installing to the L: drive on the 2nd HDD theinstall looked to be successful until I rebooted the computer.
My boot screen shows:

     Windows XP Media Center Edition
     Windows XP Media Center Edition SP2
     Ubuntu
When I choose Ubuntu, I get a terminal screen and when I type BOOT it get back 'no kernel loaded'

Now you know the setup and here is what I have done thus far:


I googled and found this page: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

followed the directions closely until I get to this portion and am a little confused

sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda

[FONT=Verdana]One question I have is which drive do I list in the above string? The drive with the MBR or the
drive that Ubuntu is on?

Also if you guys can tell me what I could have done differently.

Thank You in advance [/FONT]

---

### Post by ankspo71 on 2010-04-02
> **Jeffster999 said:**
> 

I googled and found this page: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

followed the directions closely until I get to this portion and am a  little confused

sudo grub-install  --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda

[FONT=Verdana]One question I have is which drive do I list in the  above string? The drive with the MBR or the
drive that Ubuntu is on?

 [/FONT]
First, make sure that the Wubi installation is completely removed. I haven't ever used wubi before, but as I understand it, there is a bootloader that needs to be removed too. More details on uninstalling is at: [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?)

Once you are sure it is all removed, continue with the following:

If your XP(s) are on the first drive, and Ubuntu is on the second,  install Grub to the MBR of the first drive (hda). This is the typical way  to do it.

OR you can choose to install it to MBR of the second drive (hdb), but  doing this would require you to either change the hard drive priority  afterwards (if available) in your bios, or selecting between hard drives  upon every startup by pressing a certain key (if available) on the keyboard . It  is probably best to use the above method to avoid any possible problems.

Here is another link that might help you out:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Hope this helps.

---

