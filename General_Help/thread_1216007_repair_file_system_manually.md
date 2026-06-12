---
title: "repair file system manually"
date: 2009-07-17
forum: General Help
---

### Post by zedi on 2009-07-17
At booting my Jaunty says: unclean shutdown, and starts checking home partition. Very slowly goes to &#8594; 70% (stage 1/5, 2725/2725) and hangs there for about 10 mins. Finally tells me to repair file system manually (how?). 
Should I just delete offending file ~/.local/share/Trash/files/system ???
If I need to run fsck, should I unmount ~/ first? How to do it and would I be able to access my file system than? What exact commands should I use?
Can somebody help me, please!
Bellow some info: {my ~/ is &#8594; sdb7, Jaunty is &#8594; sdb5, Ibex is &#8594; sdb6}
[I][FONT="Lucida Sans Unicode"]
zedi@zedi-komp:~$ sudo blkid

[sudo] password for zedi: 

/dev/sda1: LABEL="A_DRIVE" UUID="491A-83A1" TYPE="vfat" 

/dev/sdb1: UUID="06D048BDD048B529" LABEL="b_Wins" TYPE="ntfs" 

/dev/sdb5: UUID="27509e3f-ed24-4e0e-8ea7-624f60299e02" SEC_TYPE="ext2" TYPE="ext3" 

/dev/sdb6: UUID="db8527c9-211d-4d16-a0a1-30704af4b0db" TYPE="ext3" 

/dev/sdb7: UUID="d166d20c-2250-4d80-8691-a75dca463b38" TYPE="ext3" 

/dev/sdb8: TYPE="swap" UUID="6c3baac7-a7ba-46d6-897c-1aa38b841cd4"




zedi@zedi-komp:~$ ls -l /dev/disk/by-uuid/

total 0

lrwxrwxrwx 1 root root 10 2009-07-18 18:04 06D048BDD048B529 -> ../../sdb1

lrwxrwxrwx 1 root root 10 2009-07-18 18:04 27509e3f-ed24-4e0e-8ea7-624f60299e02 -> ../../sdb5

lrwxrwxrwx 1 root root 10 2009-07-18 18:04 491A-83A1 -> ../../sda1

lrwxrwxrwx 1 root root 10 2009-07-18 18:04 6c3baac7-a7ba-46d6-897c-1aa38b841cd4 -> ../../sdb8

lrwxrwxrwx 1 root root 10 2009-07-18 18:04 d166d20c-2250-4d80-8691-a75dca463b38 -> ../../sdb7

lrwxrwxrwx 1 root root 10 2009-07-18 18:04 db8527c9-211d-4d16-a0a1-30704af4b0db -> ../../sdb6[/FONT][/I]

Log: </var/log/fsck/checkfs>
[FONT="Lucida Console"][I]Log of fsck -C3 -R -A -a 
Sat Jul 18 08:04:43 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sdb7 contains a file system with errors, check forced.
/dev/sdb7: Duplicate or bad block in use!
/dev/sdb7: Multiply-claimed block(s) in inode 6016705: 28006459
/dev/sdb7: Multiply-claimed block(s) in inode 6016770: 28006459
/dev/sdb7: (There are 2 inodes containing multiply-claimed blocks.)

/dev/sdb7: File /zedi/.local/share/Trash/files/system (inode #6016705, mod time Thu Jul 16 20:53:44 2009) 
  has 1 multiply-claimed block(s), shared with 1 file(s):
/dev/sdb7: 	/zedi/.gconfd/saved_state (inode #6016770, mod time Sat Jul 18 00:44:00 2009)
/dev/sdb7: 

/dev/sdb7: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Sat Jul 18 08:16:29 2009
----------------[/I][/FONT]

---

### Post by sisco311 on 2009-07-17
Just run:
```

umount /dev/sdb7
e2fsck -C0 -f -v /dev/sdb7
```

from the BusyBox shell, or boot a LiveCD and use GParted.

---

### Post by zedi on 2009-07-17
sisco311
That was quick! Sorry for newbie question, but what's BusyBox shell? Can I just run your 2 commands in terminal? Do I need to put sudo in front?
And because you seem to be expert, additional request, if I can. How should look my fstab? At the moment I have to manually mount my Wins partition, 2-nd drive and Ibex partition after each booting. I can live with that, but automatic mounting would be nice.

---

### Post by sisco311 on 2009-07-17
> **zedi said:**
> sisco311
That was quick! Sorry for newbie question, but what's BusyBox shell? Can I just run your 2 commands in terminal? Do I need to put sudo in front?

If memory serves, after fsck fails you are dropped to a limited shell where you can run commands or press Ctrl+d(log out) to continue the boot process.

You can also boot in recovery mode to run the commands.

The first command is very important because you have to unmount the partition to scan the partition.

**Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.**  

You don't have to *sudo* the commands because you are root, both in BusyBox and Recovery Mode.

[COLOR="Red"]**If you are not comfortable with the CLI, then I would strongly suggest to you to boot a LiveCD and use GParted to scan the partition.**[/COLOR]

The command to run GParted is:
```
gksu gparted
```



> **zedi said:**
> 
And because you seem to be expert, additional request, if I can. How should look my fstab? At the moment I have to manually mount my Wins partition, 2-nd drive and Ibex partition after each booting. I can live with that, but automatic mounting would be nice.

You can manually edit the file: [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131") 

Or use a GUI tool: [GUI Fstab Editing with PySDM]("http://ubuntuforums.org/showthread.php?t=872197&highlight=pySDM")

If you only need to configure an NTFS drive: [http://psychocats.net/ubuntu/mountwindows]("http://psychocats.net/ubuntu/mountwindows")

---

### Post by zedi on 2009-07-17
Thanks a lot! I will try recovery mode. It takes to long to get dropped to a limited shell. Hope it'll be success!
edit:
Just notice, in <e2fsck -C0 -f -v /dev/sdb7> is it zero or capital 'o'?

---

### Post by zedi on 2009-07-18
sisco311 
I ended up using LiveCD and GParted. Partial success, because now for some reason I can't mount my partitions by clicking in Nautilus. Didn't try terminal (not comfortable with the CLI). Well, looks like I have to learn about fstab now. Anyway, thanks to you I solved my problem and I really appreciate that.

---

### Post by methewjay on 2009-07-18
Hi,
It is quite evident that you require fsck. Run the command: man fsck, to see what the scope and options are.

---

