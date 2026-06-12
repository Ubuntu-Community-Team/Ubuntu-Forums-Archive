---
title: "Not booting from USB"
date: 2012-05-06
forum: General Help
---

### Post by steve7777777 on 2012-05-06
I'm giving 12.04 a spin and installed on a USB hard drive. During installation I specified that it boot from the USB - the default was to have the bootloader on sdc1, a data drive but I chose the USB.

The USB is recognized and the only two files are in root:

intrid.img
vmlinuz

In bios I set USB disk as primary booting device, so bios is set correctly, and still boots into SDA - my current 10.10 installation. Also hit F12 to select boot order, but still booted to SDA. Not a dual boot machine - Ubuntu only.

Any ideas?

---

### Post by wilee-nilee on 2012-05-06
Knowing how you are loading the usb would be helpful, there are a number  of usb loaders available unetbootin is one commonly used. Reformat the usb to a fat32 to have a clean partition to start with as well.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Have you check ed the md5 sum of the ISO?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by steve7777777 on 2012-05-06
> **wilee-nilee said:**
> Knowing how you are loading the usb would be helpful, there are a number  of usb loaders available unetbootin is one commonly used. Reformat the usb to a fat32 to have a clean partition to start with as well.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Have you check ed the md5 sum of the ISO?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The ISO is fine. Before reading your reply I used a different external USB drive - this one a SATA drive, unplugged the internal SATA connectors so the USB was the only storage, and did the default complete intall of 12.04 to rule out user error.

Got the black screen - unable to boot from CDROM. Again the device boot order in the bios was set correctly.

So either my motherboard is the problem - it should definitely be able to boot off of USB - it's an option in the BIOS, or a bug in the 12.04?


My goal is to see if 12.04 runs on my PC before I do a fresh install, I'm currently on 10.10.

---

### Post by wilee-nilee on 2012-05-06
> **steve7777777 said:**
> The ISO is fine. Before reading your reply I used a different external USB drive - this one a SATA drive, unplugged the internal SATA connectors so the USB was the only storage, and did the default complete intall of 12.04 to rule out user error.

Got the black screen - unable to boot from CDROM. Again the device boot order in the bios was set correctly.

So either my motherboard is the problem - it should definitely be able to boot off of USB - it's an option in the BIOS, or a bug in the 12.04?


My goal is to see if 12.04 runs on my PC before I do a fresh install, I'm currently on 10.10.

I am having a bit of a problem understanding the situation exactly, lol I can be a little dense at times. But the black screen notation stands out as possibly a graphic driver needed, I just can't tell exactly when this occurs, internal or external drive. Here is a link on using nomodeset from a install boot on the grub menu with a edit or from a live cd using f6 at the first gui.

The internal or external would be using the same hardware on the computer I just can't tell by the description exactly.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by steve7777777 on 2012-05-06
> **wilee-nilee said:**
> I am having a bit of a problem understanding the situation exactly,...But the black screen notation...

Sorry, I wasn't clear. I'm getting the same message as if there was no hard drive physically connected to the system - the bios asks for a CD to be inserted. If I disconnect all bootable media I'd get that message.

I found this:
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

I'm starting to think that an install on a USB external hard drive from the live cd involves some extra steps.

---

### Post by wilee-nilee on 2012-05-06
> **steve7777777 said:**
> Sorry, I wasn't clear. I'm getting the same message as if there was no hard drive physically connected to the system - the bios asks for a CD to be inserted. If I disconnect all bootable media I'd get that message.

I found this:
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

I'm starting to think that an install on a USB external hard drive from the live cd involves some extra steps.

Wow I am missing it today I saw usb and immediately thought flash drive Doh!

If it is a problem on the external drive in general that would be rather unusual.

Not sure if you split the home out as well, and made a boot partition. The link has these as instructions.

You don't need a boot partition, so I would just try a reinstall if me, use the something else option install ubuntu in one partition on that external and make sure the dropdown on that first gui after the something other choice is putting grub in the MBR like sdb if that is the HD's identifier, not a partition no number in the sdb.

There is also a alternative cd for installing, if you can't get the live desktop from which to install from, and a nomodeset does not get you there.

---

### Post by steve7777777 on 2012-05-07
I used the following (from prior post) [http://www.linuxbsdos.com/2011/05/23...nal-hard-disk/]("http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/") to install 12.04 on the USB drive and still not bootable. I also tested the USB drive on a second PC (changed bios setting to boot from USB of course) and still doesn't work. So...

*I tried two different USB enclosures/drives.
*Tried to boot off of a second PC

Still no luck. If I didn't know any better seems like there is a bug in 12.04. I give up.

---

### Post by sudodus on 2012-05-07
> **steve7777777 said:**
> I used the following (from prior post) [http://www.linuxbsdos.com/2011/05/23...nal-hard-disk/]("http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/") to install 12.04 on the USB drive and still not bootable. I also tested the USB drive on a second PC (changed bios setting to boot from USB of course) and still doesn't work. So...

*I tried two different USB enclosures/drives.
*Tried to boot off of a second PC

Still no luck. If I didn't know any better seems like there is a bug in 12.04. I give up.

[I'm coming from your old thread:]
> **steve7777777 said:**
> I have a solid installation of 10.10. No other OS - only Ubuntu. If I had known better I would have installed 10.04 LTS but, alas, didn't know any better. Seem that 10.10 is at the end of support April 2012. I see at least three options:

1. Do nothing. 
2. Upgrade
3. Fresh install, then reinstall all apps and add back data. 

What do you recommend, and with options 2 o 3 what release should I go to?

Thanks!

Maybe we are not understanding the situation with your hardware well enough. Can you get local help from someone? I mean someone who can actually look at your computer and help you with trouble-shooting and help you understand the response of your computer. Is there some local computer club, or can you ask a friend or colleague, who knows about linux?

Have you tried to install Ubuntu from an alternate iso file (with a text based dialogue)? What about trying some other linux distro?

---

### Post by steve7777777 on 2012-05-07
> **sudodus said:**
> [I'm coming from your old thread:]


Maybe we are not understanding the situation with your hardware well enough. Can you get local help from someone? I mean someone who can actually look at your computer and help you with trouble-shooting and help you understand the response of your computer. Is there some local computer club, or can you ask a friend or colleague, who knows about linux?

Have you tried to install Ubuntu from an alternate iso file (with a text based dialogue)? What about trying some other linux distro?

I build my PC's from scratch and know the hardware inside and out. As I stated I tried the USB drive on a second  PC and it didn't boot. I could install another distro to test that,  but at this point I've spent too much time. If nobody else has the problem - installing 12.04 on a bootable USB hard drive, then it's not an issue.

---

### Post by oldfred on 2012-05-07
With USB drive plugged in and using a liveCD or USB run this script an post the results.txt it creates.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

