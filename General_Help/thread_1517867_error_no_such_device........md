---
title: "error: no such device:......."
date: 2010-06-25
forum: General Help
---

### Post by Morthax on 2010-06-25
Hi. Absolute Ubuntu noob here.

Friend had gotten a virus on his windows xp machine. A co worker suggested installing Ubuntu to scan for it because no other virus programs for windows was finding it. I got Ubuntu installed, was unsuccessful in finding it. So now I was trying to remove Ubuntu from his computer and the co worker just said to delete the partition in disk manager. I did this and restarted the computer to make sure Ubuntu was removed and am now getting 

"error: no such device: fb043c6a-21f9-4655-b7f2-d5186ef80d65.
grub rescue>"

I seen another thread with this similar problem, only on a vista machine and was trying to follow the same procedure, but I keep getting an unknown command. I checked the boot devices and keep coming back to this error. Any suggestions? Please dont tell me I just trashed my friends machine, he wont be happy and I wont be happy >_<

Thanks!

edit:  Also just for clarification, when I installed Ubuntu, I installed it beside Windows. Im sure this is obvious, but just wanted to throw it out just in case.

---

### Post by sisco311 on 2010-06-25
You have to replace GRUB with the Windows bootloader:
[http://expertester.wordpress.com/2008/07/27/how-to-remove-ubuntu-boot-loader-xp-and-vista/](http://expertester.wordpress.com/2008/07/27/how-to-remove-ubuntu-boot-loader-xp-and-vista/)

---

### Post by Morthax on 2010-06-25
> **sisco311 said:**
> You have to replace GRUB with the Windows bootloader:
[http://expertester.wordpress.com/2008/07/27/how-to-remove-ubuntu-boot-loader-xp-and-vista/](http://expertester.wordpress.com/2008/07/27/how-to-remove-ubuntu-boot-loader-xp-and-vista/)


Ok so I did what the link said, well tried too. Put in the disc, let it boot and load up and Im getting a BSOD. Its telling me to check for viruses or remove any new HDD's or HDD controllers. It tells me to run a chkdsk /f. How can I do this if I cant get it to boot up into windows? Any further help anyone can offer would be greatly appreciated.

---

### Post by oldfred on 2010-06-25
This is mostly windows issues.

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by Morthax on 2010-06-26
> **oldfred said:**
> This is mostly windows issues.

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

The problem though is I cant get into anything. Without the XP installation disc, I get the error: no such device and this doesnt let me do anything. With the disc in, it does the setup by loading a bunch of drivers, I think, and when that finishes it just blue screens and tells me to check for the virus or run a chkdsk which I dont know how to do other than from the run command inside windows. Is there another way to do this without the OS loading? I hope Im giving enough info, Im a complete noob to this stuff, even more so with Ubuntu. This is my first attempt to do anything with it. I plan to learn more.

---

### Post by oldfred on 2010-06-26
You can download a Vista disk and run chkdsk from it. Just do not use it to install the boot loader (fixboot) as the Vista boot loader is different than XP.

See post #15
[http://ubuntuforums.org/showthread.php?t=1392524&page=2](http://ubuntuforums.org/showthread.php?t=1392524&page=2)

---

