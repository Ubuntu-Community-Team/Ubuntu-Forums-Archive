---
title: "fstab &amp; NTFS not working"
date: 2010-06-09
forum: General Help
---

### Post by kwagga on 2010-06-09
OK guys, I'm about to pull my hair out of my head....

I have a several NTFS drives that I want to have mounted on boot, but I keep getting the strangest errors from mountall.

Error Output:
[[img]http://i.imagehost.org/t/0525/09062010112.jpg[/img]](http://i.imagehost.org/view/0525/09062010112)

=> System Specs: Ubuntu 10.04 Server x64, auto updates.

=> Drives in question:
/dev/sdb1: LABEL="Terra 3" UUID="38809080809045F2" TYPE="ntfs"
/dev/sdc1: LABEL="Terra 4" UUID="A8DEA95ADEA92214" TYPE="ntfs


My fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=315ab8c2-8a31-4c79-965b-b083556229d5 /               ext4    errors=remount                                                                                                                 -ro 0       1
# swap was on /dev/sda5 during installation
UUID=c897ef64-235b-4b1a-b1f3-c00f674a859c none            swap    sw                                                                                                                               0       0

[COLOR="Red"]#UUID=38809080809045F2 /dev/sdb1 /media/Terra1     ntfs-3g    defaults    0 0 

#UUID=A8DEA95ADEA92214 /dev/sdc1 /media/Terra2     ntfs-3g    defaults    0 0  [/COLOR]

[B][COLOR="Lime"]
ANY help will be greatly appreciated![/COLOR][/B]

Also, when I mounted the drive (standard mount) I noticed the system couldn't show me the drive contents from one of the drives... right there I got a cold chill down my spine, the one drive mounted fine, the other "apparently" empty...

---

### Post by TeoBigusGeekus on 2010-06-09
It should be

```
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=315ab8c2-8a31-4c79-965b-b083556229d5 / ext4 errors=remount -ro 0 1
# swap was on /dev/sda5 during installation
UUID=c897ef64-235b-4b1a-b1f3-c00f674a859c none swap sw 0 0

UUID=38809080809045F2 /media/Terra1 ntfs-3g defaults 0 0 

UUID=A8DEA95ADEA92214 /media/Terra2 ntfs-3g defaults 0 0
```

You specify the volumes by uuid and again by the /dev/sdxx arguments...

---

### Post by kwagga on 2010-06-09
Thanks SOOOOO much TeoBigusGeekus! You're a master! - I never even saw that mistake!

May I pick your brain one more time, I've mounted the drives SUCCESSFULLY (Yay! ;)) But they seem to be empty... what do you think the cause might be? - I was under the impression a dirty drive would automatically not be mounted?

> **TeoBigusGeekus said:**
> It should be

```
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=315ab8c2-8a31-4c79-965b-b083556229d5 / ext4 errors=remount -ro 0 1
# swap was on /dev/sda5 during installation
UUID=c897ef64-235b-4b1a-b1f3-c00f674a859c none swap sw 0 0

#UUID=38809080809045F2 /media/Terra1 ntfs-3g defaults 0 0 

#UUID=A8DEA95ADEA92214 /media/Terra2 ntfs-3g defaults 0 0
```

You specify the volumes by uuid and again by the /dev/sdxx arguments...

---

### Post by TeoBigusGeekus on 2010-06-09
Unmount them and fsck them to fix any errors they might have.

---

### Post by WorMzy on 2010-06-09
To clarify what Teo said, you're identifying the partition twice. Look at the first line:
```
# <file system> <mount point> <type> <options> <dump> <pass>
```
This shows you what arguments you need to include on each fstab line. Now look at the two lines in question in relation to this:

```
# <file system>        <mount point> <type>        <options> <dump>   <pass>
#UUID=38809080809045F2 /dev/sdb1     /media/Terra1 ntfs-3g   defaults 0       0
#UUID=A8DEA95ADEA92214 /dev/sdc1     /media/Terra2 ntfs-3g   defaults 0       0
```

As you can see, you've specified the partition twice on both lines, throwing the other arguments out of order. Just use /dev/sdb1 OR UUID=38809080809045F2, they both identify the same partition, so either is fine, the UUID is more reliable though.

As Teo posted, the correct lines would be:


```
# <file system>        <mount point> <type>  <options> <dump> <pass>
#UUID=38809080809045F2 /media/Terra1 ntfs-3g defaults  0      0 
#UUID=A8DEA95ADEA92214 /media/Terra2 ntfs-3g defaults  0      0
```

Wow, I took longer writing that than I thought.

---

### Post by kwagga on 2010-06-09
Thanks WorMzy for your input! I appreciate it. 

TeoBigusGeekus, I ran a fsck on the disks, still nothing, I hardly ever work with NTFS, that's why I'm battling like this. I also don't have a Windows box to run an actual chkdsk on the drive... Plan B? I tried everything, forcibly marking the drive as dirty then running fsck, still nothing.

***EDIT: The one drive is fine now, the other still seems to be blank, even after it's been checked.

---

### Post by TeoBigusGeekus on 2010-06-09
Are you sure you have data on the drives?
Did you have them abandoned in a dusty basement before you connected them to your pc, for, say, 2 years or something?
Boot with a live cd and see if you can read anything from them.

---

### Post by kwagga on 2010-06-09
He he, yeah I know the drives have data on them, they were in a Windows PC just hours ago... the one drive seems to be fine. The other... not looking good. I'm installing a Windows PC now to find out... I can see the drive labels are still in tact, maybe a glimmer of hope?

---

### Post by TeoBigusGeekus on 2010-06-09
Yeah, who knows...
Maybe it was ready to die and unplugging it and plugging it again gave it the final shot.
Post if you have any news...

---

### Post by kwagga on 2010-06-09
Good and bad news... the drive is physically fine... but emotionally.... it's dead.

I'm running a data recovery app now, just so that I can get the file table to see what was on it... it's sad though.. I hate it when drives crash...

I'm actually going to format this drive, and take it to ext4...

---

### Post by TeoBigusGeekus on 2010-06-09
Sad indeed...
Always be careful when you plug/unplug hds - I've learnt this the hard way...

---

### Post by kwagga on 2010-06-09
Yeah, I think it was wishful thinking regarding ntfs-3g as super safe and stable, yet it managed to delete a drives mbr.... I hope I can get this fixed...

---

