---
title: "Can't boot anymore, filesystem seems corrupted!"
date: 2011-01-02
forum: General Help
---

### Post by Fryie on 2011-01-02
Hello everybody,
I would be very glad if someone could help me with this problem.
I've searched the internet all over, but somehow I didn't find a solution (I REALLY hope there is one :/). Of course I might have missed something, I found a lot of similar, but not quite identical problems.

Today, when I tried to start up my system I was quite shocked, as my Ubuntu 10.10 didn't boot. The error I got was "No init found. Try passing init=bootarg".
I didn't have any problems booting Windows XP, which I had installed alongside Ubuntu, so I burned a Live CD and tried to find out what was the matter.

As it appears, my Linux partition (/dev/sda5) is broken. I can't access it via Nautilus, as I always get a "A job is pending on /dev/sda5" error. Mounting it via terminal doesn't seem to work either.
When trying to check the filesystem, either in Disk Utility or in GParted, I instantly get an error that the "device is busy" and (again) that "a job is pending".
I tried to set a boot flag on /dev/sda5 (it wasn't there before), but this didn't help neither with accessing the partition from the Live CD nor with booting it.
I tried to run the boot info script I found somewhere in a forum post, but it is just hanging itself up as soon as it starts checking /dev/sda5.
And "sudo mke2fs -n /dev/sda5" just gives me a "/dev/sda5 is apparently in use by the system" error.
By the way I did all these steps just by following advices in other threads, so I do not necessarily understand what I did there.

Now please tell me .. is there a way I can get my files back? I would really, really hate having lost all that since my last backup is 3-4 months old (yeah, yeah, I know) and I have some quite important data on that filesystem.
While there seems to be a big problem in that NOTHING seems to be working, GParted still recognizes the partition and how much of the disk space is in use .. so not everything can be lost - or am I wrong?

---

### Post by Bucky Ball on 2011-01-02
Don't think your files are gone; the disk (partition) is busy is all (which is why it won't close down or open). Did you by any chance have a power cut or shutdown Ubuntu suddenly some other way? The partition seems not to have closed properly perhaps.

---

### Post by oldfred on 2011-01-02
Make sure you have not mounted the partition and try this:

From liveCD so everything is unmounted, change sda5 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

---

### Post by Fryie on 2011-01-02
Thanks for the help.

> **oldfred said:**
> Make sure you have not mounted the partition and try this:

From liveCD so everything is unmounted, change sda5 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5
Unfortunately, both times I just get:
"e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?"

>  		Don't think your files are gone; the disk (partition) is busy is all  (which is why it won't close down or open). Did you by any chance have a  power cut or shutdown Ubuntu suddenly some other way? The partition  seems not to have closed properly perhaps
Yes. Sometimes when I shut down the Ubuntu icon (the one with the five(?) dots beneath) just remains there forever, so I have to shut down manually. However, before today this has never caused any problems.

---

### Post by Bucky Ball on 2011-01-02
When you say shutdown manually, do you mean by pressing ctl+alt+delete? I would suggest the method you used may have left the drive open (which is why its busy).

---

### Post by Fryie on 2011-01-02
No, this wouldn't help, I think, since the system is almost completely shut down .. there is just the black screen and the Ubuntu icon.
I just press the Power Button for about 5 seconds.

---

### Post by Fryie on 2011-01-03
I dont want to seem impatient, but I really need help here!

---

### Post by oldfred on 2011-01-03
The way to shutdown if normal shutdown does not work.
Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

Post this to see if something is inconsistent:

Edit obsolete command:
sudo vol_id /dev/sda5

Only can run this:
sudo blkid

but it does not give as much info.

---

### Post by QLee on 2011-01-03
[QUOTE=Fryie]...

Unfortunately, both times I just get:
"e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?"

...[/QUOTE]

If your swap partition is also on an extended partition, for example /dev/sda6, the live CD will be using that swap. You might try making sure all the partitions on your hard drive are unmounted, for example with GParted while booted to the live CD, then close GParted.

oldfred's advice is correct and the way you should proceed (post 3).

---

### Post by Fryie on 2011-01-03
Thanks for the tip on shutting down, I didnt know that!

"vol_id" doesnt seem to work, I get a "command not found" error.
I did a quick google and it appears it might have been replaced by blkid?
At any rate I tried this, if it is any help:

"ubuntu@ubuntu:~$ sudo blkid /dev/sda5
/dev/sda5: UUID="ad1d5a57-13c3-4a5b-9fbc-77bf241e9b6c" TYPE="ext4" "

edit:
Thanks for your advice, QLee. Im currently trying to "unmount"(?) the swap partition .. however this seems to take forever. Not sure if somethings actually happening or if it just hung itself up..

---

### Post by matt_symes on 2011-01-03
Hi

Have you tried running e2fsck on a different superblock than the primary superblock. Maybe that has become corrupted.

Kind regards

---

### Post by Fryie on 2011-01-03
> **matt_symes said:**
> Hi

Have you tried running e2fsck on a different superblock than the primary superblock. Maybe that has become corrupted.

Kind regards
Hi,

I hate to admit it, but I'm quite stupid when it comes to such things, so I do not really understand what I'm supposed to do, and how.
Could you please clarify your advice for me? Or direct me to any source that could explain those things to me?

---

### Post by Kildyt on 2011-01-03
Hi!

I have the same issue. I must repair the partition but I can't do this.
When I try shutdown the ubuntu normally, it stops.

Who can help?

---

### Post by matt_symes on 2011-01-04
Hi

> I hate to admit it, but I'm quite stupid when it comes to such things, so I do not really understand what I'm supposed to do, and how.

Your not stupid. Just learning. See if you can dump the file system first. Open a terminal and type

```
sudo dumpe2fs /dev/sda5 | grep -i backup
```

Enter password as usual. If that works post back the results.

Kind regards

---

### Post by Fryie on 2011-01-04
```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda5 | grep -i backup
dumpe2fs 1.41.12 (17-May-2010)
Journal backup:           inode blocks
  Backup Superblock in 32768, Gruppendeskriptoren in 32769-32772
  Backup Superblock in 98304, Gruppendeskriptoren in 98305-98308
  Backup Superblock in 163840, Gruppendeskriptoren in 163841-163844
  Backup Superblock in 229376, Gruppendeskriptoren in 229377-229380
  Backup Superblock in 294912, Gruppendeskriptoren in 294913-294916
  Backup Superblock in 819200, Gruppendeskriptoren in 819201-819204
  Backup Superblock in 884736, Gruppendeskriptoren in 884737-884740
  Backup Superblock in 1605632, Gruppendeskriptoren in 1605633-1605636
  Backup Superblock in 2654208, Gruppendeskriptoren in 2654209-2654212
  Backup Superblock in 4096000, Gruppendeskriptoren in 4096001-4096004
  Backup Superblock in 7962624, Gruppendeskriptoren in 7962625-7962628
  Backup Superblock in 11239424, Gruppendeskriptoren in 11239425-11239428

```
(Sorry for the German)

---

### Post by matt_symes on 2011-01-04
Hi

Boot into the LiveCD and make sure sda5 is not mounted. Umount if it is. Then type

```
sudo fsck -b 32768 /dev/sda5
```

See if that fixes it.

Kind regards

---

### Post by ezsit on 2011-01-04
To turn off swap:

sudo swapoff -a

This might help too.

---

### Post by Fryie on 2011-01-04
Thank you both.
I turned the swap off, but that doesnt seem to be of any help atm.

Neither did:
```
sudo fsck -b 32768 /dev/sda5
```I just get the same "device or resource busy" error as always :/

edit:
I tried also all the other superblocks that were listed, but I just got the same error over and over. In fact it didnt seem to me as if the command was actually checking anything, since the error message appeared instantaneously.

---

### Post by Fryie on 2011-01-04
I AM THE HAPPIEST MAN IN THE WORLD!

Everything is as it was before. (So now of COURSE I will backup all my data!!)

For anyone interested.
The problem, as I got from another thread here in the forum, was that the Ubuntu Live CD somehow probably automatically accessed /dev/sda5, or whatever, and unmounting didn't help either since it insisted it was not mounted. In any case, trying another live distro (Slax) I didn't have any of those problems and I could run all the tests that were suggested in this thread.
I'm not entirely sure what did the trick eventually, because I tried nearly everything, but it might have been the:[FONT=monospace]
```
[/FONT]sudo fsck -b 32768 /dev/sda5
```
since it spawned a gazillion (really, there was almost no end to it) of error messages I had to confirm with the "y" button.

Then I just set the boot flag back on that had been lost somehow, and bam:
it works!!

Thanks to everybody in this thread!

---

### Post by Bucky Ball on 2011-01-04
Good news and good work for sticking with it! Welcome to the learning curve and enjoy! Think you'll find it worth the effort when all is up and running. ;)

---

