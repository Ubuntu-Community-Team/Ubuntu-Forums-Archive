---
title: "disk check on startup."
date: 2011-05-19
forum: General Help
---

### Post by Rob8900 on 2011-05-19
When i change the date with more than 1 day and then restart the pc. Ubuntu always checks the disk and gives the following dialog:

press F to attempt to fix the errors, I to ignore, S to skip mounting or M for manual recovery.

But in my situation i don't have a keyboard the press F.

Any suggestions to fix this problem and not turning of disk check every X time.

I'm using Xubuntu 10.10 and its no option to upgrade to 11.

---

### Post by prshah on 2011-05-19
> **Rob8900 said:**
> But in my situation i don't have a keyboard the press F.

If you cannot press "F" in your keyboard (why?) you can produce a F on a desktop keyboard by doing:
a) Hold down the Alt key
b) tap (rapidly) 0070 from the number keypad
c) Release the Alt key

70 is the ASCII equivalent of the letter "F". Note this will work only in virtual terminals, not emulated terminals. You need to type the number in the number keypad only; it will not work with the top row of numbers. NumLock must be on.

Hope this helps. Please post back if you want more information.

---

### Post by Rob8900 on 2011-05-19
Thanks for the reply.

I use XUbuntu on a control that has only a numeric keyboard. So no alt keys, or other keys are available.

Is there a way have F as a default option (after a timeout for example)?

---

### Post by prshah on 2011-05-19
> **Rob8900 said:**
> I use XUbuntu on a control that has only a numeric keyboard. So no alt keys, or other keys are available.

Is there a way have F as a default option (after a timeout for example)?

Sorry, no idea about that.

However you can force a disk check on the next reboot by placing a blank file "forcefsck" in the root of the filesystem, Eg```
sudo touch /forcefsck
``` So, I suggest you do this everytime you change the date..

Just a suggestion..

---

### Post by Rob8900 on 2011-05-19
No, this does not work. I still get the error message before. Then I need to press F. After the fix, the system reboots and then runs the forced system check.

No further idea???

---

### Post by Toz on 2011-05-19
> **Rob8900 said:**
> Any suggestions to fix this problem and not turning of disk check every X time.

from **man fstab**:
```
The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.  Filesystems within  a  drive
       will  be checked sequentially, but filesystems on different drives will
       be checked at the same time to utilize  parallelism  available  in  the
       hardware.   [COLOR="Red"]If  the sixth field is not present or zero, a value of zero
       is returned and fsck will assume that the filesystem does not  need  to
       be checked.[/COLOR]

```

I'm not sure this is really a safe thing to do (the root filesystem should be checked regularly), but it is an option. If you choose to do this, you should develop some sort of process to manually check the disk for errors on a regular basis. Hint:```
touch /forcefsck
```

---

### Post by prshah on 2011-05-19
> **Rob8900 said:**
> I still get the error message before. Then I need to press F. After the fix, the system reboots and then runs the forced system check.

Another suggestion: You can turn off time dependent checking. ```
sudo tune2fs -i 0 /dev/sda1
``` However, this is less recommended. Your essential problem will still not be solved, in the sense that max mount count checks will still be run. Also, as and when file system damage is detected, the checks will still be run. At that point, I don't know if the "F" option screen appears or not.

Perhaps you may want to try it out.

btw, turning off max mount count checks (-c) AND time based check (-i) is highly NOT recommended.

---

