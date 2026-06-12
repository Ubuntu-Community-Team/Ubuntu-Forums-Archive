---
title: "unable to mount location. no media in the drive"
date: 2009-07-06
forum: General Help
---

### Post by daffy_parasite on 2009-07-06
hallo! i am a new ubuntu 9.04 user and i face a few problems quite discouraging! one of them and maybe the most important issue is the problem with the cd rom
when going to    places -> computer->cd rw drive and i double click on cd rw drive i get an error message saying "unable to mount location" and below that "no media in the drive".the cd i am using when trying this is an autocad 2009!
the cd driver is a plexwriter...  the strange thing is that i didnt face this problem from the first time i put ubuntu on since i used my cdrom in order to create a virtual box with windows!2-3 weeks after though i got this annoying message!
can anybody help?autocad is a vital program for my school projects so i would really appreciate it if somebody could give me a hand!
thanx in advance

---

### Post by taurus on 2009-07-06
So it doesn't automount when you insert the disc into the drive?

What does your /etc/fstab look like anyway?

```
cat /etc/fstab
```

---

### Post by Taxman415a on 2009-07-06
Can you describe exactly what happens when you place the disc in the drive? By default Ubuntu will automount it. Aftern inserting the disc, try opening a terminal and typing in the following commands.
```
dmesg | tail -n 20
mount
```

Also attach the dmesg.txt file that results from
```
dmesg > dmesg.txt
```

Then perhaps from that we can see what's going on or have you try to mount the disc manually and see what kind of errors are returned.

---

### Post by michy99 on 2009-07-06
Are you having the problem with all CDs or only that one?

---

### Post by daffy_parasite on 2009-07-06
this is what i get when i type     cat /etc/fstab


marios@marios-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d498000b-8da9-4db9-924c-9ba622bb1c9d /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=a0f5581a-26d9-480b-a2c6-df1a14ef103e none            swap    sw              0       0
/dev/scd1       /dev/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
marios@marios-desktop:~$

---

### Post by taurus on 2009-07-06
What happens if you insert the CD into the drive?  If it doesn't automatically mount, post the output of this command from a terminal (while the CD is still in the drive).

```
dmesg | tail
```
Do you have problems with other CDs?

---

### Post by daffy_parasite on 2009-07-06
as soon as i put the cd in the cdrom the light of the cd rom turns orange but not steadily(it turns on-off)after that nothing happens...after that i try to double click on the icon at the file browser but i get what i wrote in the first thread!
here are the results for the codes you suggested!


...**marios@marios-desktop:~$**** dmesg | tail -n 20**
[ 8594.918833] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8597.922495] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8600.926660] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8603.930526] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8606.934337] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8609.938152] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8609.942158] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8905.493196] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8908.496957] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8911.500716] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8914.504505] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8917.508165] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8920.511823] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 8920.515898] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 9624.272071] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 9627.275702] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 9630.279449] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 9633.283141] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 9636.286841] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 9639.290477] sr0: CDROM not ready.  Make sure there is a disc in the drive.






**marios@marios-desktop:~$ mount**
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/marios/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marios)
marios@marios-desktop:~$ 


i didnt understand the thing with the 
dmesg > dmesg.txt

---

### Post by taurus on 2009-07-06
Have you tried that same disc with another computer?  Does your computer able to mount another CD?

---

### Post by daffy_parasite on 2009-07-06
i have a problem with the other cd rom but i think this is a coincidence....to become more specific as soon as i plug in a cd/dvd it immediatelly ejects it...i actually dont remember if this issue (dvd rom)appeared before or after first using linux

---

### Post by taurus on 2009-07-06
If another computer can't read that same disc, then chances are there is something wrong with the disc.  Are there scratches on the disc?  Do other CD/DVD discs work on Ubuntu?

---

### Post by irv on 2009-07-06
Have you tried restarting the computer, putting in a different CD to see if this same thing happens again? If not try that first.

---

### Post by daffy_parasite on 2009-07-06
i tried this cd with another computer and it run just fine! i also tried another cd with my computer and the light of the cd rom turned green!however, it runs neither automatically nor by clicking on the icon at the file browser!:(

---

### Post by irv on 2009-07-06
> **daffy_parasite said:**
> i tried this cd with another computer and it run just fine! i also tried another cd with my computer and the light of the cd rom turned green!however, it runs neither automatically nor by clicking on the icon at the file browser!:(

Have you restarted the computer since this problem started?

---

### Post by daffy_parasite on 2009-07-06
this problem first appeared about 2 weeks ago so i have turned it off a few times....

---

### Post by taurus on 2009-07-06
If the same CD/DVD discs work fine with another computer but won't work on yours, then there is something wrong with your drive.  Make sure the cable is securely plugged in.  Otherwise, swap the CD/DVD drive with another one that you know that works and see what happens.

---

### Post by prasad_n08 on 2009-07-06
hai..............
               i am too having the problem of not able to mount the cd or dvd in ubuntu9.04
                 when i kept the ubuntu os cd it automatically mounted and opened but when i am keeping the other cd's or dvd's it is not mouting can any one help me.................

                      plz..........................

---

### Post by daffy_parasite on 2009-07-06
isnt there any chance there is a "system " problem? i just asked a friend of mine and he said that i should maybe remove synaptic links.....i have no idea what that means:S      in addition how can it be to not work either of the two cd/dvd roms.....isnt it a bit strange that both are down?by that i want to say that it is a bit difficult to have both broken down...i cant be that unlucky!(can i?)

---

### Post by taurus on 2009-07-06
Open up the case and check the cables.

---

### Post by michy99 on 2009-07-06
Do you have dual-boot with Window? If so, then try the CD in Windows. If it works fine there, then the problem is with Ubuntu. If it doesn't work in Windows either, then the problem is either the CD or the drive.

---

### Post by prasad_n08 on 2009-07-06
no i am not having any other os i am having only ubuntu

---

### Post by prasad_n08 on 2009-07-06
every thing is ok when i am keeping the ubuntu os it is mounting automatically and it is not recognising any of the other cds

---

### Post by daffy_parasite on 2009-07-06
i have created a virtual box with windows...i try the cd with it but it doesnt recognise it at all!!.after that i try another cd and it runs ok...(in the virtual box)(i dont get it....i have tried the autocad cd with my brother's pc running xp and it runs ok!!)this is so confusing!
guys i am sorry but it is the situation like that....i am begging for your patience :S

---

### Post by daffy_parasite on 2009-07-06
i have created a virtual box with windows...i try the cd with it but it doesnt recognise it at all!!.after that i try another cd and it runs ok...(in the virtual box)(i dont get it....i have tried the autocad cd with my brother's pc running xp and it runs ok!!)this is so confusing!
guys i am sorry but it is the situation like that....i am begging for your patience :S

---

### Post by daffy_parasite on 2009-07-06
i noticed something but i dont if it is important! when i put the autocad cd in the cd rom it says "no media in the drive", but when i put another cd with some powerpoint presentations the error message says "cant mount file"..i dont think this is helpful but i mention it just in case!

---

### Post by irv on 2009-07-06
Here is a link to someone having the same problem with a solution. It is for an older version of Ubuntu, but it will give you something to look at.
[https://answers.launchpad.net/ubuntu/+question/14278]("https://answers.launchpad.net/ubuntu/+question/14278")

---

