---
title: "**Unclean shut down checking drives....NOOO"
date: 2009-08-20
forum: General Help
---

### Post by stillcen on 2009-08-20
when booting ubuntu i get a

unclean shut down, checking drives

the check gets up to 34% and then the wheels fall off.

if i just try to boot again the same thing keeps happening.

here is what i get--

error reading block 23625828 (attempt to read block form file system resulted in a short read) while getting next Inode from scan.
/dev/sda6 : unexpected inconsistancy; run fsck manually.
 (i.e., without -a or -p options)
fsck died with exit status 4
           [FAIL]
a log is being saved in /far/log/fsck/checkfs if that location is writable.
please repair the file system manually.
a maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot
Bash: no jab control in this shell
Root@Makkc:~#

-------

the /var/log/fsk reads


fsck 1.41.4 (27-Jan-2009)
/dev/sda6 contains a file system with errors, check forced.
Error reading block 23625828 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
fsck died with exit status 4


---------


what i did prior to this happeing;---

Updates on 8-19  from the update manager
---

edited my grub menu.lst with
 
map (hd1) (hd0)
map (hd0) (hd1)


----------


i should note that i had gotten this checking drive thing before but had the option to press esc and ignore,  i did, like a couple of times.



what the eck?

when it finally dumps me back in to terminal/consul  i can type exit and a bunch more stuff scrolls past and the system loads.




thanks


stilcen

---

### Post by utnubuuser on 2009-08-20
Try booting from liveCD, going to System>>Administration>>Partition Editor, then select a partition and right-click, then select Check.

I'm not sure on this point, but I do believe gParted's "Check" feature will repair any errors it finds, (if it can).  - There are also options available through drop-down menus.

---

### Post by tgeer43 on 2009-08-20
The error is caused by one or more bad blocks on the drive and the exit code 4 means: Errors were found but not corrected.
 The answer is contained in the error message:
```
/dev/sda6 : unexpected inconsistancy; run fsck manually.
 (i.e., without -a or -p options)
```Boot from the Live CD or another Linux installation and run:
```
fsck -rV /dev/sda6
```The -r option will cause fsck to prompt you before making each repair. The -V option is for Verbose mode so it will tell you what's going on as it runs.

_**MAKE SURE THE DRIVE YOU ARE CHECKING IS NOT MOUNTED OR YOU WILL RISK DATA CORRUPTION/LOSS!**_

tgeer

---

### Post by stillcen on 2009-08-20
Right i 

1) backed up key info

2) tried to unmount dev/sda6---- said i could not, possible as it is "home"

3) booted from Ubuntu CD making no changes to the system

4) goto GParted Hi-Light dev/sda6
 A) I do not have an option to Unmount (light grey)
 B) Information says the drive is unmounted
 C) when i select to check that partition i get
     ---Editing partitions has the potential to cause LOSS of DATA.
You are advised to backup your data before proceeding.--

5)  i assume that i do Fsck from terminal/consul

THE Question

If i booted from a CD is the hard disk Unmounted?
If not, how do i Unmount it for a safer Fsck?


THANKS


Stillcen

---

### Post by tgeer43 on 2009-08-20
> If i booted from a CD is the hard disk Unmounted?
If not, how do i Unmount it for a safer Fsck?Yes, when you boot from a Live CD your hard drives are unmounted until you mount them via the command line, with gparted, by selecting them in the Places menu, etc. When a drive is mounted gparted will show a lock icon or set of keys (depending on the version of gparted) next to the device name (eg. sda6).

I don't know why you are getting the warning when you select 'Check' but if there's no lock or keys icon and the unmount option is greyed out while the mount option is not then you can be reasonably sure that it is currently unmounted.

You can use gparted's 'Check' feature to try to repair the drive/partition and if that errors out for some reason then run fsck manually from the terminal.

If after running fsck you still have the same problem, try running it again with the -c option which will cause fsck to invoke the badblocks program. This will check the entire disk/partition for bad  blocks and mark them accordingly so that the system will not try to use these blocks in the future.

When using the -c option with fsck be prepared to wait a long time, especially if there are bad blocks on the drive as this can slow down the execution of the badblocks program considerably.

tgeer

---

### Post by stillcen on 2009-08-21
confirmed partition is unmounted (thanks)

went to terminal and 

Sudo fsck -rV /dev/sda6

2 hours latter hitting lots of <enter> to force ignores and writes for
error  reading block ######## (attemped to read block from file system resulted in short read)  while getting next inode from scan.

so i tried fsck -p  and got

must do manual fsck without -a or -p

so went back to just a 

fsck  no options

and spent another hour hitting enters for the same thing

the numbers keep getting bigger but for the love of Hathor  3 hours of hitting enter so i hit NO

back to terminal

so i did the Gparted check feature been around 7 hours latter, and it is still working away?

Any suggestions?

the home partitions is about 182.52 Gig


stilcen

---

### Post by tgeer43 on 2009-08-21
You're not doing anything wrong, if that's what you are asking. You have a relatively large drive with lots of errors/bad blocks and it takes a long time to run as you now know. If you use the -c option to run the badblocks problem it's going to take even longer. :(

Looks like the drive is on it's way out. - sorry.

If you still want to try to recover it you could try running:
```
sudo fsck -rVay /dev/sda6
```Then go on vacation or something.
The -a option will cause fsck to automatically answer 'Yes' to all questions and the -y option will do the same thing for any programs that fsck invokes like e2fsck and badblocks.

Normally you wouldn't want to give fsck this much leeway but in your case you might not have much to lose. Having said that, if this screws up your drive even worse than it already is, don't say you weren't forewarned.

By all means back up whatever data you can before attempting any filesystem repairs.

tgeer

---

### Post by stillcen on 2009-08-22
tgeer43;  you were not kidding about the vacation.

been running the fsck -y  for 9 hours, after 3 hours of the other fscking and 8 1/2 hours of Gparted check disk.  i feel as though sack cloth and ashes are in order.

as a note of info  when i first stated fscking  i would hit  2-3 blocks in a row then jump a few thousand.  The amount of block in a row, that are bad, in now just over 100.

i did a little online seach to figure out how many bits are in a block to try a little math to see just how many fracking blocks could be in 180 gigs.  remembered somthing about 512 bits....oh how times have changed since my first hard drive.  a gig is a really big number.

Thanks for the info.


stillcen

---

### Post by tgeer43 on 2009-08-22
Stillcen,

It looks like the handwriting is on the wall. When I checked a failing 100GB drive fsck exhibited the very same behaviour. It started out processing large numbers of blocks at a time but they got incrementally smaller and smaller until things ground almost to a halt.

Look at the bright side. Drives are dirt cheap, especially online. Unless your drive is pretty new you can probably buy a 500GB or at least 320GB.

It's 3:00am, I better get some sleep.

tgeer

p.s. Speaking about how times have changed. My first three computers didn't have hard drives but my first real hard drive was an Apple Profile about the size of a mini tower case that set me back over $1200 and had a whopping capacity of 5MB! (yes, Megabytes) :)

---

### Post by stillcen on 2009-08-25
Shear stubbornness and 76 hours latter of fscking has checked/fixed blocks 28 million to 37 million.  

Even if, for some miracle, fsck does reaches the end of the bad block/ short reads, what are the odds of the drive working properly?

any one have a notion of odds?

----------

Back in my DOS days i had a program that flagged the bad sectors of a hard disk, that let you continue to use your failing hardrive/ floppy disks, by zoning off the dodgy bits.  it was pretty quick to, mapped out a 32 meg drive in about a hour.   any one know of a program like that for ubuntu?


stillcen

---

### Post by tgeer43 on 2009-08-25
> **stillcen said:**
> Shear stubbornness and 76 hours latter of fscking has checked/fixed blocks 28 million to 37 million.  

Even if, for some miracle, fsck does reaches the end of the bad block/ short reads, what are the odds of the drive working properly?

any one have a notion of odds?I can't give you any numerical odds but as stated in my previous post, the drive is almost certainly failing and will very likely continue to do so. It may operate correctly if fsck successfully repairs everything but future bad blocks are all but inevitable. It's time to cut your losses and replace it ASAP. Your efforts to repair the drive are only useful for attempting to salvage as much data as possible for backup purposes.

> Back in my DOS days i had a program that flagged the bad sectors of a hard disk, that let you continue to use your failing hardrive/ floppy disks, by zoning off the dodgy bits.  it was pretty quick to, mapped out a 32 meg drive in about a hour.   any one know of a program like that for ubuntu?Yes, fsck with the -c option does exactly that. It invokes the badblocks program which marks all of the bad blocks accordingly so that the system will not attempt to use them. As for speed, fsck is much faster than what you used in DOS way back in the day. It's not so much a function of the program as it is the massive increases in the speeds of processors, memory, system bus, and hard drive performance. What you've got to consider is that your current 180GB drive is well over 5000 times larger than that old 32MB drive was. Even if fsck is 10 times faster it will still take over 500 times as long.

tgeer

---

### Post by stillcen on 2009-08-25
i appreciate you smacking me with what i already knew but was tying not to accept.




Now the search for the new drive.....


thanks.


stillcen

---

