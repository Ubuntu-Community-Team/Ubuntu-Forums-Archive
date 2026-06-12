---
title: "Grub Problem"
date: 2010-03-31
forum: General Help
---

### Post by noxary on 2010-03-31
Everytime I boot up my computer, grub boot loader, doesn't really show up, but grub does.

It goes straight to, a bash-like interface.

I'm confused and I don't know where to go from here.

---

### Post by drs305 on 2010-03-31
noxary,

Welcome to the Ubuntu forums. If you are using Grub 2, what may be happening is that you are being dropped to the Grub prompt. Do you see "grub>" or the the grub rescue prompt?

If so, the good news is that Grub 2 allows you to boot from the command line when it can't boot for itself. Here is a link to the community doc for using the Grub 2 command line. It looks a bit confusing but it you just follow the guide you may be able to boot into your system. We can then help sort out what the problem might be:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by noxary on 2010-03-31
Wow, what a quick reply. :-)

Well, at first, it was the grub rescue menu. I then tried to troubleshoot the problem but couldn't. I ended up installing two new versions of Ubuntu, but niether fixed it. Then I followed steps for installing grub from another forum thinking it might fix the problem. but instead, everytime I turn on the computer, I get

grub>

Whatttt should I do?

Edit:

I also have two hard drives sda and sdb.

---

### Post by drs305 on 2010-03-31
> **noxary said:**
> Wow, what a quick reply.

Well, at first, it was the grub rescue menu. I then tried to troubleshoot the problem but couldn't. I ended up installing two new versions of Ubuntu, but niether fixed it. Then I followed steps for installing grub from another forum thinking it might fix the problem. but instead, everytime I turn on the computer, I get

grub>

Whatttt should I do?

Edit:

I also have two hard drives sda and sdb.

At the grub prompt, see if running "ls" gives you the partitions on your drives. From that, you can look for the grub files. As an example, say "ls" returns (hd0) (hd0,1) (hd0,5) (hd1) (hd1,1).

Linux will be installed on a partition, so it should be on one of the entries with a drive and partition (hd0,1), (hd0,5) or (hd1,1) in the above example.

Next search the for the kernel. You can try to guess which partition with a command such as "ls (hd0,5)/boot" or you can let Grub2 search using:
"search -f /vmlinuz"

If you find the kernel, go back to the command line link I provided previously to see if you can run the commands there now that you know the correct partition to use in the commands.

If you still are having problems, give us the errors and which partition your Ubuntu install is on.

---

### Post by noxary on 2010-03-31
It says that ls is not a known command.

---

### Post by drs305 on 2010-03-31
I know you said you tried to reinstall grub. It's probably time to do it again, since we don't know exactly what state your system is in. There is a set of instructions in the previous link I posted for reinstalling Grub2 from the LiveCD.

Also from the LiveCD, you can run meierfra's boot info script and post the results to tell us the state of your system. If you post the results, click on the # icon in the post's menu and paste the results between the "code" tags.

---

### Post by cashyy on 2010-03-31
Hi guys, When I turn on my cpu I get the same error "File not found" Grub rescue>
I've seen some solutions, but I'm not sure what to do, one problem is that I don't have my live cd, so I don't know what to do, any help would be appreciated.

Heres what happended, I upgraded ubuntu 9.10 to 10.04 beta and I could no longer boot into windows 7, so I found online that I could upgrade grub and I put in a command, and then I turned off my pc, and when it comes on I get the error.

---

### Post by john newbuntu on 2010-04-01
As drs305 suggested, download the script, run it using a liveCD and post the output of the command from:
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript)
This will help the readers diagnose the problem.  You need to post the output of "RESULTS.TXT".  Thanks.

---

### Post by drs305 on 2010-04-01
> **cashyy said:**
> Hi guys, When I turn on my cpu I get the same error "File not found" Grub rescue>
I've seen some solutions, but I'm not sure what to do, one problem is that **I don't have my live cd**, so I don't know what to do, any help would be appreciated.

Heres what happended, I upgraded ubuntu 9.10 to 10.04 beta and I could no longer boot into windows 7, so I found online that I could upgrade grub and I put in a command, and then I turned off my pc, and when it comes on I get the error.

The Grub2 rescue mode usually means grub is having problems finding it's files. If you don't have a LiveCD, you might be able to find the files using the "ls" command.

At the prompt, run "ls" and if G2 is working you should be able to find out what partitions it sees. The first drive is 0, the first partition is 1, so sda1 is "hd0,1", sdb5 would be "hd1,5".

If you think you know which partition contains the grub files, use this command to see if they are there. Substitute the correct partition.
```
ls (hd*0,5*)/boot/grub
```
Try different combinations from the "ls" results until you find the files.
You can also try the command "search -f /vmlinuz" if you get meaningful results from the first one.
Then try this series of commands from the G2 prompt. Use the actual partition and path for your system:
```

set prefix=(hd*0,5*)/boot/grub
insmod (hd*0,5*)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sd*a5* ro
initrd /initrd.img
boot
```

If your computer boots, run the boot info script as previously mentioned and we can repair the files.

Here is the community doc link to booting from the grub command line:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by m4tic on 2010-04-01
if you want to reinstall grub, try this using live cd
 
the X is your partition number which you can find by
```
sudo fdisk -l
```
 
```
[FONT=Courier New]$sudo mount /dev/sdaX /mnt[/FONT]
[FONT=Courier New]$sudo mount --bind /dev /mnt/dev[/FONT]
$sudo mount --bind /proc /mnt/proc
[FONT=Courier New]sudo chroot /mnt[/FONT]
[FONT=Courier New]#grub-install --recheck /dev/sda[/FONT]
 
[FONT=Courier New]$sudo reboot[/FONT] 

```
 
Then when it boots, go to your ubuntu partition and enter in terminal ```
 $sudo update-grub2
```

---

### Post by noxary on 2010-04-02
I fixed it I think luckily though.

I went into my BIOS and found out that my second hard drive loads first, then I booted into my Live CD, and did step thirteen
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
on that link. I just tried three differenty partitions out of the 6-7 that I had and it worked.

Thanks for the help guys!

---

