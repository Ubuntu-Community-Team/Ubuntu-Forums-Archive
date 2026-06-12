---
title: "Ubuntu 10.10 Slow Boot Time"
date: 2011-01-17
forum: General Help
---

### Post by max54 on 2011-01-17
[B][SIZE="2"]Hi..I use Ubuntu 10.10 x64 .when i install os boot time be fast but,later really strong slow down i dont know why this my Bootchart log [/SIZE]
[/B]

**[SIZE="2"]Bootchart log[/SIZE]** -->  [http://img88.imageshack.us/img88/2089/oxygenmaverick201101172.png]("http://img88.imageshack.us/img88/2089/oxygenmaverick201101172.png")

**[SIZE="2"]Any Idea?[/SIZE]**

---

### Post by lithopsian on 2011-01-17
The first thing I see is 15s to even start the boot.  Do you have a massive initrd file?

Then your bootchart shows nearly 20s checking a filesystem.  That shouldn't happen every time you boot, although it will happen occasionally.  If it happens every time then you have a problem with that drive.  Or you have a problem that it is getting checked every time.  Turn off quiet boot and see what the messages say.  Are you also mounting an ntfs drive?

apt-check seems to be taking a long time.  Should it even be running every time you boot?  Not the worst thing, worry about it later.  Same for apparmor.  What is it doing maxing your CPU for 10 seconds?

Then you bootchart runs on long past when you have a usable desktop, so you should probably ignore everything after about 60s.  Or if all that stuff starts at every boot, then consider reprofiling because it isn't included in readahead and so is taking longer than necessary.  I also notice a readahead job lurking in there, which shouldn't be happening since you have ureadahead.

All in all it is a bit of a dogs dinner.  Work on what look like the major problems first and then there might be other tweaks.  Like are you using concurrent boot since you have a quad core?

---

### Post by oldfred on 2011-01-17
i might try running chkdsk on all the NTFS partitions. Even if they work, a chkdsk may help and cannot hurt. If you get errors with chkdsk rerun it until you get no errors as it does not fix everything on one pass.

 
Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Bazzi313 on 2011-01-17
Open up the /boot/grub/menu.lst file in your favorite text editor. I’m using gedit:[INDENT]sudo gedit /boot/grub/menu.lst
 [/INDENT]Now find the section that looks like this:[INDENT]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout 3
 [/INDENT]The timeout value is in seconds. Save the file, and when you reboot  you will have that many seconds to choose the menu item you want.


If you find a blank notepad, just type ( #timeout SECONDS )FOR EG #TIMEOUT 2,= 2 SECONDS, if you set it to -1, it will disable timeout

COMMENT ON REULTS, HOPE I HELPED

---

