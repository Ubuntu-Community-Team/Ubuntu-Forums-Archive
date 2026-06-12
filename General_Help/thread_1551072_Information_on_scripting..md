---
title: "Information on scripting."
date: 2010-08-11
forum: General Help
---

### Post by DeanMc on 2010-08-11
Hi all,

I am completely new to Ubuntu and Linux in general. I have gotten my pc set up but in order to get the wireless working I had to complete procedure A in the following link.

[http://www.backports.ubuntuforums.org/showthread.php?t=1353044](http://www.backports.ubuntuforums.org/showthread.php?t=1353044)

This worked fine I simply substituted the downloads directory to /home/user/supportfiles and changed the kernel version to the one my installation uses. I recently updated the kernel and had to perform step B to update my driver references, this again worked a treat.

If you are familiar with that link you will see the information is repetitive in nature and looks like it could be achieved using a script of some sort. The only differences I need to worry about are the change of kernel number.

I have read that Linux has a more powerful terminal than the windows command prompt and can have scripts acted upon it. Is this the sort of redundancy that can be solved using scripted.

Do note that I am only following part b in that tutorial and even at that it is only the later steps that need to be followed given that most of the have already been done (The tutorial points out which to skip and which to do.)

---

### Post by DeanMc on 2010-08-12
Humpity bumpity bump :)

---

### Post by earthpigg on 2010-08-12
hi,

could you translate those directions into terminal commands that can be run in order without having to click anything thing?

```
#!/bin/bash

command1
command2
command3
etc
```

save it as script.sh.

that's basically what a shell script is.

to run it, type this:
```
sh /path/to/script.sh
```


so, it looks like you only need to do this stuff?

> Step 9

Code:
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0

Code:
make && make install



Step 10

Code:
mkdir /lib/modules/2.6.31-15-generic/updates



Step 11

Code:
cp -p /lib/modules/2.6.31-15-generic/kernel/drivers/net/wireless/rt3070sta.ko /lib/modules/2.6.31-15-generic/updates/


Step 12

Code:
depmod -a


Code:
cp -f /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat



Step 14

Code:
echo "ifconfig ra0 inet up" >> /etc/init.d/rc.local


1) make a text file, make the first line of it be "#!/bin/bash", and start copying/pasting those commands in order.

2) double check that the commands are all correct.

3) triple check that all the commands are correct.

4) save it in your home directory as "superman.sh" or whatever you want to call it.

5) instead of typing 'sudo -i' for step 1, we are going to gain root by typing "sudo sh ~/superman.sh" when we run the script.


because "2.6.31-15" is a kernel version, and this needs to be run when we update the kernel (right?), you will need to edit those lines of the script manually before you run it each time with the new/current kernel version. it is possible to pipe uname -a into the script and replace the old kernel version with the new one at the start of the script, if you want to google that. it's beyond what i know off the top of my head.

---

### Post by DeanMc on 2010-08-12
Legend, that is pretty much all I needed to know! I will look up piping as I want this to be an non issue as I update kernel to kernel!

My friend, you are a legend!

---

### Post by earthpigg on 2010-08-12
take a look at the command "sed".

you know about man pages, right?

```
man sed
```

make sure you back up the script while your working, cuz you will likely erase the entire a file a few times while playing with sed.

---

### Post by DeanMc on 2010-08-13
They're like built in manuals that explain who commands etc work and there usage right?

---

### Post by aeiah on 2010-08-13
you shouldnt need to manually set your current kernel, you should be able to do it in your script

the command ```
uname -r
``` gives you your current kernel. this is untested, but you should be able to do something like this, for example:

```

mkdir /lib/modules/`uname -r`/updates

```

note the funky apostrophes. for me they're located next to the number 1 key. ` is not the same as '
'`'`'`'`'`

---

### Post by aeiah on 2010-08-13
> **DeanMc said:**
> They're like built in manuals that explain who commands etc work and there usage right?

yea. and sed has crazy syntax, so you might need to google for examples as well as read the manual, heh.

---

### Post by DeanMc on 2010-08-13
Cool, I'l try this all out before the next kernel update. As for the funky apostrophe its ` not ' right? I call it a fada but I don't know its real name :)

---

