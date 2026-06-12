---
title: "Ubuntu isn't installing"
date: 2011-05-19
forum: General Help
---

### Post by carsd103 on 2011-05-19
Hey I just got Ubuntu and when I installed it via CD, however when I reboot my comp, it gives me a choice between Windows 7 and Ubuntu, I select Ubuntu, and it comes up with the logo and 5 dots which turn from white to red in a row etc, I left this for about 2 hours, and then came back and realised that the dots had stopped changing colour. I tried rebooting to me Windows side but it said I had to use System Restore to make it work, I've tried installing Ubuntu twice more, and the dots stop moving after about 20 seconds...

any help?

EDIT: I used the following method:

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by ghostborg on 2011-05-19
Wow, I have not seen so many bad installs before. Everyday in the forums there are several new entries of people needing help.

I found this as I'm not exactly sure of your problem, maybe it will help.

[http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/") 

Good Luck to you and remember to breathe.. hehe.

---

### Post by bcbc on 2011-05-20
> **carsd103 said:**
> Hey I just got Ubuntu and when I installed it via CD, however when I reboot my comp, it gives me a choice between Windows 7 and Ubuntu, I select Ubuntu, and it comes up with the logo and 5 dots which turn from white to red in a row etc, I left this for about 2 hours, and then came back and realised that the dots had stopped changing colour. I tried rebooting to me Windows side but it said I had to use System Restore to make it work, I've tried installing Ubuntu twice more, and the dots stop moving after about 20 seconds...

any help?

EDIT: I used the following method:

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

It's most likely a hardware incompatibility. What brand/model/graphics card do you have?

---

### Post by carsd103 on 2011-05-20
Hey there, 

I have an "HP G72 Notebook PC" according to dxdiag 

Intel Core i3, 4GB RAM, it's not too bad.

I downloaded the wubi.exe and installed it like that and then rebooted, and chose ubuntu, however it came up with the logo and dots, and after a while froze. Is there anyway I can completely start again, and just have Windows 7, and try reinstalling it from there. Are there any really detailed guides which tell you how to do everything... because some of them are quite complicated..

They tell me to go into Computer Management, and delete my Ubuntu Partition, although one doesn't even come up, and then it tells me to use the fixmbr command or something.. anything to do with Ubuntu only comes up when I have my CD which I burned it onto is in.

Come to think of it, it could be trying to load from the disc when I choice Ubuntu at the very beginning on Boot.

I'll reboot my PC without the CD in.

Cheers all, any more help would be appreciated.

EDIT:

When I reboot my PC it gives me the choice of Windows 7 or Ubuntu, when I chose Ubuntu it came up with the attached picture, but I didn't know what to type so I rebooted to Windows.

To clear things up: if I chose to boot from a CD when I had my burned CD in, it would load up the Ubuntu logo, and then the dots would stop after a while, and the fans in my computer would slowly die down, like nothing was happening at all; at the beginning, they go quite loudly.

---

### Post by bcbc on 2011-05-20
So you installed Ubuntu with Wubi. You can boot Windows and go to the control panel and remove it as any other program (look for "Ubuntu" and uninstall). Wubi does not create an Ubuntu partition and it does not replace the windows bootloader so there should be no messing about required. (If you installed from the Live CD then you'd need to, but clearly you can't even boot a linux kernel, so no chance you could have done this).

The problem you have is that many HP's don't work out of the box with Ubuntu. Likely you need to find and apply some '[kernel boot overrides]("http://ubuntuforums.org/showthread.php?t=1613132")' to get Ubuntu to work.

I'll have a look and see if I can find something that applies to your computer.

---

### Post by bcbc on 2011-05-20
This post indicates it should work [http://ubuntuforums.org/showpost.php?p=10640066&postcount=534](http://ubuntuforums.org/showpost.php?p=10640066&postcount=534)

What graphics card do you have? If you have a bios switchable graphics, try switching to onboard - or else try booting with the 'nomodeset' option from that link in my previous post.

It's best to figure out how to boot from the Ubuntu CD first - select "Try it" (without installing).

---

### Post by linuxinstalledfromhdd on 2011-05-20
Don't Use Wubi to install it if it doesn't go the first time. 

Be old school and install it from a disc.

And make sure to follow a to-do list to make this a piece of cake.

And use the previous version not the bleeding edge version of Ubuntu.

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

That's the to-do list you can follow if you want a very successful pre and post installation.

---

### Post by bcbc on 2011-05-20
> **linuxinstalledfromhdd said:**
> Don't Use Wubi to install it if it doesn't go the first time. 

Be old school and install it from a disc.

And make sure to follow a to-do list to make this a piece of cake.

And use the previous version not the bleeding edge version of Ubuntu.

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

That's the to-do list you can follow if you want a very successful pre and post installation.

Actually, Wubi's great for first timers. People who are just trying it out. It's really easy to uninstall and get on with your life if it doesn't work out.

Once they figure out they like it - for sure... old school, new school whatever, a real install is the way to go.

---

### Post by uRock on 2011-05-20
I have removed all of the off topic rhetoric. Please help keep our forums clean.

Thanks,
uRock

---

### Post by carsd103 on 2011-05-24
Ok well, 

When I turn on my computer, it gives me the option of Windows 7, Ubuntu or Ubuntu (it comes up twice), how can I get rid of these, as Ubuntu or Wubi isn't even coming up on my installed programs, 

I just don't get it, why is it so hard to install, and it's not like I'm retarded at computers it's just failing... I've seen on youtube videos installing 11.04, with the loading screens with dots, it takes like 2 minutes, and mines take forever, and then just freezes, and I can't even do anything about it.

And I also get this grub thing, which looks a tad like the command prompt, but fills the entire screen..

help anyone?

---

### Post by bcbc on 2011-05-24
> **carsd103 said:**
> Ok well, 

When I turn on my computer, it gives me the option of Windows 7, Ubuntu or Ubuntu (it comes up twice), how can I get rid of these, as Ubuntu or Wubi isn't even coming up on my installed programs, 

I just don't get it, why is it so hard to install, and it's not like I'm retarded at computers it's just failing... I've seen on youtube videos installing 11.04, with the loading screens with dots, it takes like 2 minutes, and mines take forever, and then just freezes, and I can't even do anything about it.

And I also get this grub thing, which looks a tad like the command prompt, but fills the entire screen..

help anyone?

Usually uninstalling "Ubuntu" from Control Panel, "Uninstall a program" will remove the boot entry. If it doesn't then you have to use the Microsoft command line tool bcdedit.exe - or if you prefer you can download easyBCD (as the name implies it's supposed to be easier than bcdedit).

For bcdedit, run cmd.exe as adminstrator. Enter "bcdedit" to get a list of the entries. Then select and copy the guid identifier corresponding to the Ubuntu entry and delete the entry: bcdedit /delete {guid}
Please consult the manual ("bcdedit /?" ) and/or Microsoft website guide for using this tool. Obviously harm could come from making mistakes.

As to why it's not booting - I'm not sure. Others report that Ubuntu works on this computer. I would advise booting an Ubuntu CD in live CD mode: Select "Try it" without installing. Then experiment with boot options.

Or if you have plenty of RAM you could run it in a virtual machine.

---

### Post by SparTacux on 2011-05-24
You could try installing from a live USB instead of from CD. I had a similar problem with Linux Mint - I just couldn't get it to get past those dots on screen. Installing from USB worked first time. I never got to the bottom of it but did find a workaround.

---

