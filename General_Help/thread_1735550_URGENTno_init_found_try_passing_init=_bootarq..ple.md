---
title: "URGENT::no init found try passing init= bootarq..please help"
date: 2011-04-21
forum: General Help
---

### Post by vivek.pandey on 2011-04-21
hey everyone
    i started my laptop and terminal was not working properly  i was just getting a white screen instead of black terminal....then i restarted ubuntu and i get following errors... obviously these are last few lines of the long bunch of lines
```

mount: mounting /dev on /root/failed no such file or drectory  
mount: mounting /sys on /root/sys no such file or drectory  
mount: mounting /proc on /root/proc no such file or drectory
No init found .Try  passing init= bootarq


``` 
please help as i cant even boot into ubuntu and i have some urgent work to do... thanx to all

---

### Post by vivek.pandey on 2011-04-21
please anybody help

i tried using 
```

ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda6: clean, 133717/557056 files, 626986/2211840 blocks

ubuntu@ubuntu:~$ sudo fsck /dev/sda8
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda8
Filesystem mounted or opened exclusively by another program?


```

where sda6 is my root directory and sda8 and home directory

---

### Post by josephmills on 2011-04-21
hi there I am real new to all of this but go into your bios and run mem test and disk check do they all pass? also do you have any live cd around?

---

### Post by vivek.pandey on 2011-04-21
> **josephmills said:**
> hi there I am real new to all of this but go into your bios and run mem test and disk check do they all pass? also do you have any live cd around?

 first of all thanx for replying
i am booting from live cd and executed those commands from live cd.. i dont know whats the problem with /dev/sda8 ..its my home directory.. its not encrypted even ..  checking from gparted gives errors..

---

### Post by josephmills on 2011-04-21
do you have a smart linux cd laying around? [http://www.asrdata2.com/](http://www.asrdata2.com/)

---

### Post by vivek.pandey on 2011-04-21
> **josephmills said:**
> hi there I am real new to all of this but go into your bios and run mem test and disk check do they all pass? also do you have any live cd around?
i did the memory test too,,  all past .... also i dont have a smart cd..its just a live ubuntu cd 10.10

---

### Post by drs305 on 2011-04-21
If you boot the LiveCD and download the boot info script we can check to see if any of the boot files aren't being found. A 'white' screen doesn't sound like a boot issue, but we can take a look.

Run the script, then please post the contents of RESULTS.txt within 'code' tags. You generate the tags in the post by pressing the # icon.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by vivek.pandey on 2011-04-21
> **drs305 said:**
> If you boot the LiveCD and download the boot info script we can check to see if any of the boot files aren't being found. A 'white' screen doesn't sound like a boot issue, but we can take a look.

Run the script, then please post the contents of RESULTS.txt within 'code' tags. You generate the tags in the post by pressing the # icon.
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)
thanx for your help
i downloaded the bootscript copied on desktop ran the command but terminal gets hang ... even pressing ctrl+c doesnt do anything...
it simply remains in same condition
```

ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ sudo bash boot_info_script055.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 


```
i dont get a RESULT.txt file on desktop

---

### Post by drs305 on 2011-04-21
There is definitely a problem with sda8. 

I have seen other users unable to run the e2fsck check because of the 'busy' error successfully do so from the SLAX LiveCD.

[http://www.slax.org/]("http://www.slax.org/")

The command you would want to run once you have booted (with sda8 still unmounted):
```
e2fsck -f -y -v /dev/sda8
```
I assume you would use "sudo" with the above command.

---

### Post by vivek.pandey on 2011-04-21
> **drs305 said:**
> There is definitely a problem with sda8. 

I have seen other users unable to run the e2fsck check because of the 'busy' error successfully do so from the SLAX LiveCD.

[http://www.slax.org/](http://www.slax.org/)

The command you would want to run once you have booted (with sda8 still unmounted):
```
e2fsck -f -y -v /dev/sda8
```I assume you would use "sudo" with the above command.

as soon as i opened this thread, i ran the command i get this 
```

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda8
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda8
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

```

---

### Post by drs305 on 2011-04-21
> **vivek.pandey said:**
> as soon as i opened this thread, i ran the command i get this 
```

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda8
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda8
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

```

Yes, I read that. 

I have seen multiple users who were unable to run the fsck/e2fsck check from the Ubuntu LiveCD who were nevertheless able to run the same command from the SLAX LiveCD. 

I don't know why it would work from SLAX and not Ubuntu, but the fact is that it has, at least for some users. The SLAX ISO is about 200MB.

---

### Post by vivek.pandey on 2011-04-22
i am downloading slax..... but can  anybody still give an other solution...?

---

### Post by vivek.pandey on 2011-04-22
so finally i solved my problem... and i guess this solution is gonna help many a lot... i downloaded slax but was unable to burn it on cd as there was some checksum problem.. mostly because of corrupted down load .. i have a bt4 live cd.. i booted with it and then ran 
```

fsck /dev/sda6
fsck /dev/sda8

```

one by one , where sda6 was my file system and sda8  home directory.. there were a lot of errors in home directory . bt4 found and fixed.. really happy to get my system back

thanx to all who helped.. esp drs305

---

### Post by earlf on 2011-06-23
Despite being late to this tread and this issue marked as solved, I thought I'd add my experience with this sort of booting error because of the similar nature and solution to the problem.

After a hard reboot, (i've no SysRq key) my partition with 10.10 would not boot, but gave me the intimidating ```
(initramfs) _ no init found try passing init=bootarg 
```
I stared blankly at the screen, with a rising feeling of panic. I searched the forums and found similar problems and answers. In short, drs305's suggestion to boot off of the [Slax LiveCD]("http://www.slax.org/get_slax.php") and run ```
e2fsck -f -y -v /dev/sda3
``` concisely solved my problem. (Ubuntu resides on my sda3 partition). I am quite relieved. 

Strangely, attempting to run a similar fsck using a 10.10 LiveCD did keep giving me a similar #device busy# error. I tried running the bootinfoscript using the same LiveCD, but gawk was not installed and it said it would use BusyBox instead. When it did, the script hung when it reached my corrupted partition, much like vivek.pandey's results in comment #8.( I was using bootinfoscript060.sh)
Even though the script hung, it kicked out some results to a the LiveCD's /tmp/ location.

These additional points may help further troubleshooting, or could indicate other problems. For the record, I am dualbooting OSX 10.4 and Ubuntu 10.10 usring the [rEFIt]("http://refit.sourceforge.net/") boot menu.

Strange problem probably caused by yours truly, but helpful solution. Thanks for the comments and tips vivek.pandey and drs305.

---

