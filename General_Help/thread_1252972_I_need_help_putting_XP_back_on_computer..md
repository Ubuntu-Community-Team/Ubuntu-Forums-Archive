---
title: "I need help putting XP back on computer."
date: 2009-08-29
forum: General Help
---

### Post by gbus59 on 2009-08-29
I've been using Ubuntu all summer and quite frankly I'm fed up with it so I went and bought a XP start up Cd and when I try to run it I get this error message:
[/media/cdrom0/setup.exe]
End-of-central-directory signature not found. Either this file is not a zip file, or it constitutes one disk of a multi-part archive. 

The entire message is longer but thats is the jest of it. Please help.

---

### Post by jocko on 2009-08-29
> **gbus59 said:**
> I've been using Ubuntu all summer and quite frankly I'm fed up with it so I went and bought a XP start up Cd and when I try to run it I get this error message:
[[COLOR=Red]/media/cdrom0/setup.exe[/COLOR]]
End-of-central-directory signature not found. Either this file is not a zip file, or it constitutes one disk of a multi-part archive. 

The entire message is longer but thats is the jest of it. Please help.
Are you trying to run the windows install from within ubuntu?
Don't. The setup.exe you are trying to run is a windows program, so it doesn't work in linux (not even in wine, as it needs to access a real windows file system and real windows libraries and not the emulated ones of wine...).
You need to boot from the cd.

---

### Post by gbus59 on 2009-08-29
How do I boot from the CD?

---

### Post by gbus59 on 2009-08-29
And yes, I am trying to install windows from inside ubuntu

---

### Post by Vince N on 2009-08-29
In most cases you just put the CD in the drive then restart the computer.  If that does not work then you have one of two problems.

1. The CD is non bootable (Unlikely if it is a genuine Windows disk but possible if you burned it from somewhere, You will need to re-burn it and make it bootable)
or
2. Your system BIOS is configured to boot from a Hard Drive before CD ROM, in which case you will need to alter your BIOS settings to boot from CD-ROM first.  The directions on how to do this very from motherboard to motherboard so you'll need to go into the BIOS and hunt or consult your documentation.

You cannot install Windows as the Primary OS from within Ubuntu as the Windows install program is not a Linux compatible application.

---

### Post by str8outtacpt on 2009-08-29
hey you all. i am having a similar problem. i think i did something very bad. i put linux on my computer and i accident went to partition editer and made my hard allocated instead of ntfs but i never commited the change but i cant back to windows and i do not have anything to back it up with so is there anyway i can get windows back without losing all my data?


please answer quick....im having a mental break down literately

---

### Post by str8outtacpt on 2009-08-29
> **Vince N said:**
> In most cases you just put the CD in the drive then restart the computer.  If that does not work then you have one of two problems.

1. The CD is non bootable (Unlikely if it is a genuine Windows disk but possible if you burned it from somewhere, You will need to re-burn it and make it bootable)
or
2. Your system BIOS is configured to boot from a Hard Drive before CD ROM, in which case you will need to alter your BIOS settings to boot from CD-ROM first.  The directions on how to do this very from motherboard to motherboard so you'll need to go into the BIOS and hunt or consult your documentation.

You cannot install Windows as the Primary OS from within Ubuntu as the Windows install program is not a Linux compatible application.

i think i did something very bad. i put linux on my computer and i accident went to partition editer and made my hard allocated instead of ntfs but i never commited the change but i cant back to windows and i do not have anything to back it up with so is there anyway i can get windows back without losing all my data?

---

### Post by gbus59 on 2009-08-29
> **Vince N said:**
> 
 2. Your system BIOS is configured to boot from a Hard Drive before CD ROM, in which case you will need to alter your BIOS settings to boot from CD-ROM first.  The directions on how to do this very from motherboard to motherboard so you'll need to go into the BIOS and hunt or consult your documentation.

You cannot install Windows as the Primary OS from within Ubuntu as the Windows install program is not a Linux compatible application.
So how do I get into these BIOS Settings?

---

### Post by Vince N on 2009-08-29
> i think i did something very bad. i put linux on my computer and i accident went to partition editer and made my hard allocated instead of ntfs but i never commited the change but i cant back to windows and i do not have anything to back it up with so is there anyway i can get windows back without losing all my data?

If you never committed the change then you may be ok so long as you did not tell Ubuntu to install over the whole drive.  YOu can download a program called "gParted" from the repositories that will allow you to look at and manipulate your hard drive.  You can use it to see if the NTFS partition is there.  If it is then you can reconfigured Grub to try and get into it.  If it isn't then your options are going to be pretty limited.

			 		 	 	 > So how do I get into these BIOS Settings?

Most mainboards use either F1 or Escape at boot time during the initial startup before the OS begins to load (when you see it doing the RAM TESTS and such).  If your not sure what you are doing then I suggest you read up on it and be very careful when you first go in.  Make sure whatever you change you make note of what the value was before in case it does not behave as you expect.

---

### Post by TrakerJon on 2009-08-29
Guys guys guys...ok here we go.

You need to do two things...overwrite your master boot record (MBR) or you'll be screaming because XP won't boot and secondly delete any existing particians you don't want any more.

Boot from your XP disk either by setting your BIOS boot device order to CD/DVD ROM before hard disk or by trying F11 or F12 at startup and selecting it from the menu. 

Using the System Recovery Console in XP get to a DOS prompt and type fixmbr to overwrite the Grub reference in the MBR to allow you to boot to XP. Make sure you only use these commands on a system with one operating system installed. If you have more than one operating system installed, fixmbr could mess up everything.

Now, reboot, boot to the XP CD and reinstall XP after deleting the particians you no longer want or need.

---

### Post by jocko on 2009-08-30
> **TrakerJon said:**
> Guys guys guys...ok here we go.

You need to do two things...overwrite your master boot record (MBR) or you'll be screaming because XP won't boot and secondly delete any existing particians you don't want any more.

Boot from your XP disk either by setting your BIOS boot device order to CD/DVD ROM before hard disk or by trying F11 or F12 at startup and selecting it from the menu. 

Using the System Recovery Console in XP get to a DOS prompt and type fixmbr to overwrite the Grub reference in the MBR to allow you to boot to XP. Make sure you only use these commands on a system with one operating system installed. If you have more than one operating system installed, fixmbr could mess up everything.

Now, reboot, boot to the XP CD and reinstall XP after deleting the particians you no longer want or need.
Why would it be necessary to fix the mbr BEFORE he installs XP??? XP will install it's boot loader to the mbr anyway, so it makes no difference whatsoever what's on the mbr before installing XP.
The XP installer also let you set up the partitions, so there's no need to delete or add any partitions before installing xp (unless you want to resize a partition you want to keep).
So: Just boot from the XP cd and let it install.

To boot from cd, there are different ways for different computers:
In most computers you need to set the boot order in bios. To enter the bios setup you need to press a certain key on the keyboard during the power-on self-test (POST; when you see the bios screen just after you power on the computer). Usually it says somewhere on the screen which key you need to press (usually Del, F2 or F1).
In some computers you can access a bios boot menu where you can select the boot device for just that boot (again you need to hit a special key during POST, and it usually says somewhere on the screen which key to press).

If the POST is too quick for you to read the instructions, either just try Del, F2 and F1 (or Esc or other F-keys), or press the Pause button to pause the POST and read what it says... Or find the manual for your motherboard.

When you manage to get into the bios setup, look for an item named something like "boot", "boot order" or "Boot device priority" (or something similar). This usually contains a list of a few devices (hard disks, optical drives, USB devices, etc.). Make sure your CD/DVD drive is at the top of this list, and your hard drive is second.

---

### Post by gbus59 on 2009-08-30
> **jocko said:**
> 

When you manage to get into the bios setup, look for an item named something like "boot", "boot order" or "Boot device priority" (or something similar). This usually contains a list of a few devices (hard disks, optical drives, USB devices, etc.). Make sure your CD/DVD drive is at the top of this list, and your hard drive is second.
I got that far but the cd drive is second, is that a big deal or should I continue anyways?

---

### Post by gbus59 on 2009-08-30
nevermind, I moved it up but when it boots it works great until it says 

"Remove any newly installed hard drvies or hard drive controllers. check your hard drive to make sure it is properly configured and terminated." 

I'm assuming this is refering to Ubuntu.

---

