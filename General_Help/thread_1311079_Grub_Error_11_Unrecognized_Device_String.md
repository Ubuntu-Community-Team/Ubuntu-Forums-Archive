---
title: "Grub Error 11 Unrecognized Device String"
date: 2009-11-02
forum: General Help
---

### Post by jheaton5 on 2009-11-02
Running 9.04 NBR on Dell mini9
Decided to install grub2 (I am using it on my laptop with 9.10 and I like it.)

During the install I was prompted to confirm the kopt command.  There was no command provided for me to confirm, so I assumed that there was nothing to enter.

On reboot I get the error 11 message and then it shows the grub menu with the grub2 chainloader.  I have tried all menu options and cannot boot anything.

I have reviewed several threads on Error 11 and tried the recommendations, except the ones that require that I be booted into a live CD since I don't have a CD drive.  I can make a bootable USB drive with the 9.04 Live CD iso, but that will have to wait until I get home so I can get on my other computer.

Is there any way to fix this issue from the grub command line?

I have done this:
[quote=grub wiki]Error 11

After upgrading from GRUB Legacy
Error 11: Unrecognized device string... 
&#8226;press any key to continue 
&#8226;highlight "Chainload into GRUB 2" 
&#8226;press e 
&#8226;highlight "root xxxxxxxxxxxxxxxxxxxx" 
&#8226;press e 
&#8226;change "root xxxxxxxxxxxxxxxx" to "uuid xxxxxxxxxxxxxxxxxx" 
&#8226;press b to boot "uuid xxxxxxxxxxxxxxxxxxx" 
&#8226;load your kernel and press enter [/quote]

---

### Post by samasat on 2009-11-02
I don't know much about Ubuntu ... however, remeber to came across this recently ...May be step '4a' explanation in this help you:

< [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) >

samasat

---

### Post by jheaton5 on 2009-11-02
> **samasat said:**
> I don't know much about Ubuntu ... however, remeber to came across this recently ...May be step '4a' explanation in this help you:

< [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) >

samasat

Thanks, but it doesn't help.

---

### Post by ranch hand on 2009-11-02
There are a lot of links in the thread in my sig.  The second one may be of the most help to you.

There is also one for installing grub-legacy toward the bottom that may be of interest.

---

### Post by jheaton5 on 2009-11-02
> **ranch hand said:**
> There are a lot of links in the thread in my sig.  The second one may be of the most help to you.

There is also one for installing grub-legacy toward the bottom that may be of interest.

Ranch Hand, thanks for your willingness to help.  I think you are probably my best resource at this point.  What I failed to make clear is that I have not done an upgrade-from-grub-legacy yet, so I am still in the grub-legacy menu. 

From the grub command line I have read the menu.lst file.  All appears correct there.  "kopt=root=UUID=xxxxxxxxxxxxxxxxxxx"  The root partition is (hd0,0)  I assume that since I am still in grub-legacy that the partitions are numbered from 0.  Perhaps I should test setting root to (hd0,1)?

The only thing that was curious during the install of grub2 was the request to confirm the kopt command.  But there was no kopt command to confirm and I did not know the kopt command so I just hit <OK>.  I think that is the mistake I made.  I know the correct kopt command now, but I can't figure out where or how to input the data.  I have read the [Grub Manual]("http://www.gnu.org/software/grub/manual/grub.html") and all the command line commands.  I would like to fix the problem from the grub command line if possible.  If not I'll have to make a USB boot stick to get access to the menu.lst and grub.cfg file.

Any thoughts would be greatly appreciated.

---

### Post by jheaton5 on 2009-11-02
OK, ```
grub> geometry (hd0)
Drive 0x80: C/H/S - 933/255/63, The number of sectors = 15005088, LBA
   Partition num: 0, Filesystem type is ext2fs, partion type 0x83
   Partioion num: 4, Filesystem type unknown, partition type 0x82

grub> cat /etc/fstab
# /dev/sda1 UUID=9ddd4f70-9133-4a30-8539-53876c3d13f6  /  ext3  realtime,errors=remount-ro  0
# /dev/sda5 UUID=5e0da0c9-74f1-4d23-8f77-ae1d04925f90 none swap sw  0  0

grub> cat /etc/mtab
/dev/sda1 / ext3 rw,realtime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
Proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexed,nosuid,noev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```

---

### Post by ranch hand on 2009-11-02
I think that your main problem is grub-legacy.  I have installed grub on a couple of other OS' and forgot that option to not remove grub-legacy and chainload.

The reason I didn't remember it is that I turned it down with out even thinking about it.  The devs were trying to get folks to try it that way and a lot of folks had problems with it.  Some did not.  Seeing that I have been using grub2 since 9.04alpha2, I knew it would work.

I do not know how to even begin to try to remove grub-legacy from the grub command line, or even if that is possible.

I would chroot into your OS and run the upgrade from grub-legacy command and hope it works as there are folks that have had trouble with that too.  If it does not work I would use apt-get to remove/purge grub .97 and then run apt again and try to install grub-common and grub-pc.  Grub-pc will probably survie the demise of grub-legacy but grub-common will probably be gone so it needs to be installed.

If it does not run automatically you will need to run update-grub and I would, just to be sure run grub-install /dev/sda.

I am away from my normal OS as I am on my test platform getting set up for 10.04 testing.  I will be back there soon and have more resources at hand.

I would, if I were you, recheck the second link in my intro post.  drs305 can make grub2 sit up and beg.

---

### Post by jheaton5 on 2009-11-02
Thanks again for your reply.  I have been able to load and boot the kernel.  So now I will try upgrade-from-grub-legacy.

---

### Post by ranch hand on 2009-11-02
That is great news.

The 2 grubs just do not seem to play nice together.

I have, in my short time using Linux and Ubuntu, come to love grub-legacy.  Grub2 still has some rough spots but I really think it is and will be better.

OPTION
If you enable the karmic universe repo for a little bit and run apt-get update.  You will get some updates available.  Do not use any of them except grub-pc and grub-common.  This will upgrade your grub2 to 1.97beta4.  After doing this get rid of the karmic repo and run apt-get update again.

1.96 will probably be fine.

---

### Post by jheaton5 on 2009-11-02
What I think I' going to do is:
1. Make my old menu.lst file active again
2. aptitude purge grub2
and wait until I upgrade to Karmic to try grub2.  I plan to do the upgrade this coming weekend.

Thanks again for your help.

---

### Post by ranch hand on 2009-11-02
That would work too.

---

### Post by jheaton5 on 2009-11-02
After purging grub2, purging grub, installing grub then running update-grub, all is well.

---

### Post by ranch hand on 2009-11-02
Life is good.

Mark the thread solved  (top of page under Thread Tools)

---

