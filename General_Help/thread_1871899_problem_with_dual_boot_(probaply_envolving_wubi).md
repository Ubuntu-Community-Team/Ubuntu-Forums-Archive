---
title: "problem with dual boot (probaply envolving wubi)"
date: 2011-10-29
forum: General Help
---

### Post by wpdunin on 2011-10-29
so, i got 2 o.s's in my pc, ubuntu and 7. untill yesterday the windows 7 was on top of my dual boot list, but i wanted to change it, so i went inside windows configurations and put ubuntu first, but i also set the time to 0 cause i thought i could acess windows trhought grub, but it happens that after i upgraded my ubuntu to 11.10 that screen with boot options dont show windows 7 anymore.
i went online searching for a solution to my problem, most of them told me to configure some grub options and others to use programs to do it....i've done them all and still cant acess windows 7.
just in case my problem is not clear yet, this is how was my boot before i messed all up:

windows 7 
ubuntu

with a time of 10 secs to choose between both.

this is how i wanted it to be

ubuntu
windows 7
 0 time to choose, but inside ubuntu i could acess windows trhought that grub screen.

but this is what happens:
ubuntu
windows 7
0 time, so it dont let me choose anything and jumps inside ubuntu
then inside ubuntu grub doesnt show up anymore (black screen) and it starts ubuntu normally.

as i said i tryed to fix this many times from different ways inside ubuntu but nothing worked, also when i try do do something and then upgrade my grub (sudo upgrade-grub) it shows this message:

Generating grub.cfg ...
Found Windows 7 (loader) on /dev/sda1
Skipping Windows 7 (loader) on Wubi system
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
done

thats why in the title i said it could probably be my wubi messing all up.

anyone heave a solution for this?
do you need more information?what?

i think that putting on the windows CD and repairing the system should do the trick, but i dont heave the CD, at least not untill monday....and i need a solution faster than monday.


thanks for helping

---

### Post by Blaqksheep on 2011-10-29
Hi there.  From what you're describing, your problem isn't grub at all.

Do me a favor and run this command in your Ubuntu terminal.

```
sudo fdisk -l
```

This code will display your partition tree for your HDD.  Please copy/paste the results of it into your next post to confirm my hypothesis.

**Hypothesis**
An install through Wubi doesn't use Grub to boot.  It utilizes Windows MBR (Master Boot Record) and adjusts your BOOT.INI in Windows to allow you the dual boot.

**The reason none of the solutions you have tried has worked is because they're meant to fix Grub, not MBR.**

I'm an A+ Certified Tech with an expertise in Windows OS.  If you're comfortable with Windows and trusting me, these are the steps to fix your problem.

-----

**Solution**
1)  Boot into Ubuntu.
2)  Open your Nautilus file manager (just go into any folder)
3)  Click on your Windows partition to mount and enter it.
- This partition *should* be C:\, the Windows "root" folder.
4)  Confirm this is C:\ by locating the following folders:
- Program Files
- Windows
- Documents and Settings
5)  If this is C:\, look for a file titled BOOT.INI
6)  Copy this file and paste a duplicate in your Ubuntu Documents folder or onto a flash drive as a backup.
7)  Open this file in a text editor.  It should look something like this:
```
[boot loader]
 timeout=0
 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
 [operating systems]
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows 7" /fastdetect
 multi(0)disk(0)rdisk(0)partition(2)\LINUX="Ubuntu"
```
8)  Edit the part that says **timeout=0** to whatever time you wish.
9)  Save and overwrite the current version.

-----

When you restart your computer, you should be greeted once more by Windows MBR and be able to select your OS.

**Remember!**
When installing through Wubi, Grub is never utilized.

-----

Hope it works.  =)

---

### Post by bcbc on 2011-10-30
Windows 7 doesn't use boot.ini. And this problem is a bit of a pain to fix. Which is one of the reasons that windows entries are hidden from the grub menu on wubi installs (new on release 11.10) - this mistaken concept that you can boot Windows from a wubi grub. You see, Windows bootloader --> windows bootsector --> windows bootmanager --> either windows or ubuntu (if you select ubuntu and then select windows, it goes back to --> windows bootsector --> windows bootmanager). So you can see that setting Ubuntu as the default and the timeout to zero, and then trying to boot windows from Ubuntu just causes a loop.

Try:
Hitting the Up arrow repeatedly at boot. This has been reported (unconfirmed) to make the windows boot manager show.
You can try hitting F8 as well.

Otherwise, your only option is a Windows 7 repair command prompt. You can try:
bcdedit /timeout 10

Also, you could try
bcdedit /set {bootmgr} displaybootmenu Yes

---

### Post by Blaqksheep on 2011-10-30
Duh!  Been a long day...

Try pressing F5 prior to the operating system loading.  Depending on your computer, it will bring up a diagnostic screen with several options.  One of the options is to boot into Windows in a diagnostic mode, and another should bring up the boot menu.  

Alternatively, you can full-install Ubuntu to a flash drive (Burn the Ubuntu ISO to a cd and install it on your flash drive as you would a hard drive), and set the USB Drive to boot first from your BIOS.  That will launch a working Grub you can use to boot to Windows.

From inside Windows, the easiest way to fix it is to do this:

1)  Open Start Menu
2)  Type "msconfig" and hit enter
3)  Open the "Boot" tab
4)  Change to desired Timeout in bottom right corner
5)  Click OK
6)  Huzzah!

---

