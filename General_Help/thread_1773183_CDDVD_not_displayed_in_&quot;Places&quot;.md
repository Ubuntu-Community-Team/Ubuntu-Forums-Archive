---
title: "CD/DVD not displayed in &quot;Places&quot;"
date: 2011-06-01
forum: General Help
---

### Post by SoFl W on 2011-06-01
This has worked before but today I noticed when I put a CD or DVD it doesn't show up in the places menu.  It does not matter if it is a data or media DVD/CD.   If I put a playable DVD in the drive I can play it with VLC, but I have no way of displaying or navigating through the contents of the drive.


The only recent changes I have made to the system besides getting the  latest 2.6.32-32 upgrade the other day I have also installed virtualbox.

Any ideas, am I missing something really simple?

2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux
 Ubunto 10.4 Lucid



**1st EDIT:**
When I looked at the "/media" directory I get this. 
<code>
SoFlW@desktop:/media$ wdir
total 46K
drwxr-xr-x  2 root root 4.0K 2011-01-15 12:35 sdf1
drwxrwxrwx  8 root root 4.0K 2011-04-15 15:32 mp3_files
drwxrwxrwx  8 root root 4.0K 2011-05-26 22:26 media_files
drwxr-xr-x 23 root root 4.0K 2011-05-30 09:33 ..
drwxrwxrwx  1 root root  24K 2011-05-30 14:12 WinShare
dr--------  3 walt walt   88 2011-06-01 11:44 disk
-rw-------  1 root root    0 2011-06-01 16:47 .hal-mtab-lock
drwxr-xr-x  7 root root 4.0K 2011-06-01 18:03 .
SoFlW@desktop:/media$ sudo nano .hal-mtab-lock 
SoFlW@desktop:/media$ cd disk
bash: cd: disk: Permission denied
SoFlW@desktop:/media$ nano disk/
SoFlW@desktop:/media$ cd disk
bash: cd: disk: Permission denied
SoFlW@desktop:/media$ wdir disk
ls: cannot access disk/.: Permission denied
total 0
d????????? ? ? ? ?                ? .
SoFlW@desktop:/media$ sudo mv disk disk_X
mv: cannot move `disk' to `disk_X': Device or resource busy
</code>

What is the "disk" directory?  Is the ".hal-mtab-lock" suppose to be there?

I also noticed that after I put in my usb stick to make a bootable stick the data disk in the DVD drive showed up as a possible choice to make a boot-able stick.  (it isn't a OS image)


**2nd EDIT:**
If I use the command "eject" from the terminal afterwards the "disk" in the directory listing is gone.
when I put a disc back in the tray and close the drive it appears for a second then disappears and problem is as above.

[B]3rd Edit:
[/B]I renamed the **"**.hal-mtab-lock" in case that was giving me the problem and I rebooted.  I am not sure if it is working but deleting the "disk" directory, renaming that file, and rebooting seems to have made things "happier."  The DVD that gives me the trouble was made with a stand alone DVR/DVD burner hooked up to the TV.  I think the DVR/DVD must have given it the volume name "disk".  There could be something odd going on with the DVR/DVD encoding or file structure that just isn't a standard.
I was hoping to get the short video off from the DVD and have it in mpeg format.  I am not sure if this is "Solved" but I will test it for a few more days before marking it as "Solved"
Would still be interested in suggestions.

---

