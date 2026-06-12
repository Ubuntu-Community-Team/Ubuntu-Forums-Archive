---
title: "Can't boot into Windows -- &quot;too many connections&quot;"
date: 2012-01-10
forum: General Help
---

### Post by le_vainqueur on 2012-01-10
Several months ago I created a dual boot of Windows 7 and Ubuntu on a new computer.  Both operating systems have worked flawlessly up to this point.  However, this morning a serious problem showed up.  When starting up the computer, GRUB did not allow me to select the Windows install.  GRUB is set up to boot into Windows by default, however, this was not working.  Instead, an error message saying “too many connections” appeared, and the computer booted into Ubuntu.  I have attempted to boot the system several times, but each time this error occurs.   I have been unable to find a solution elsewhere in the forums.  I have two questions

1. Are there any suggestions as to how to successfully boot into Windows.  Any ideas are welcome here.  Basically I just need to get into Windows as soon as possible to resume work.

2. What is the root cause, and is there a way to fix it.  

My backup plan is to wipe and reinstall the OS (probably go Windows only to avoid the issue on my work PC in the future).  I would prefer not to do this since the time required to reinstall all of my work software would kill a huge part of my day.
Any suggestions are welcome! Thanks!

---

### Post by oldfred on 2012-01-10
I have not seen too many connections, is this from Windows as it is trying to boot?

Post this just to see if boot is configured correctly still.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

There is a new testing version of bootinfoscript, has a few fixes, try it if you like.
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

---

### Post by N00b-un-2 on 2012-01-10
seems to be an error with GRUB.  Do you by any chance have an ATI graphics card, as I've seen this error before periodically on certain builds of GRUB on computers running certain Radeon cards.

Suggestions:

1) open synaptic and roll grub back to a previous version

2) install an alternative boot loader.  I use BURG, which is a fork of GRUB2.  As much as GRUB2 has been changing lately, BURG seems to stay the same and it just plain works.  Plus it's a graphical boot loader!!!
[URL="https://launchpad.net/~n-muench/+archive/burg"]
https://launchpad.net/~n-muench/+archive/burg[/URL]

---

### Post by QIII on 2012-01-10
Do not change GRUB, revert to an older version or install burg yet.  Work through the problem to solve it.

I am not convinced it is a GRUB problem.  It might be any number of things.

Have you recently updated GRUB?

```
sudo update-grub
```

Did you add a startup program in Windows?

Was there a recent Windows update?

---

### Post by satanselbow on 2012-01-10
+ several to that! All we know at the moment is that windows failed with the mentioned error. Could be anything from a win virus infection to a bad disk to a rogue sql server :(

You need to at least confirm that grub is at fault before going down that route. Rather sounds like grub just did it's job and when the win boot attempt failed (for reason unknown) it fell back to the next os on the list.

---

### Post by Mark Phelps on 2012-01-11
You could try using Boot-Repair to set the PC back to booting directly into Windows:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

At least, if that works, you have ruled out a more serious Windows-related problem.

---

### Post by le_vainqueur on 2012-01-12
Thanks for all of the suggestions.  I was about to do the sudo update-grub command, but decided to just update Ubuntu first.  After an update, everything worked fine.  I’m not sure how that happened since I didn’t update or install anything prior to the system giving me problems.  I’m a little worried that the problem will appear again since I don’t really understand what fixed it.  Is there anything I should do to make sure that there isn’t a bigger problem here?

---

### Post by oldfred on 2012-01-12
I like to have current version repairCD or LiveCD or flash drives with the tools needed to repair a system. I also create a full install in a large flash drive of Ubuntu so it is like another drive. You have the liveCD/USB you used to install Ubuntu. 

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

