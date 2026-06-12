---
title: "How to get access to root after breaking sudo"
date: 2011-10-10
forum: General Help
---

### Post by nk.krishnak on 2011-10-10
hello all,
 
            i am a newbie to ubuntu.Without knowing the consequences i executed the following command,

chmod -R 777 /

then when i accessed the command
 sudo su 
it says permission denied and i finally googling the modes i changed the modes of /etc/sudoers.d/README to 0440 by going to recovery mode.

here comes the real problem,
even after changing the /etc/sudoers.d/README to 0440 it says permission denied.

when i changed to other modes it says /etc/sudoers.d/README should be 0440 mode ,but now it is in other mode.

i have tried with different modes,i get messages only these two,

1.permission denied ---when /etc/sudoers.d/README is in 0440 mode
2.sudoers.d/README is in some other mode, should be 0440 mode -------when README mode is changed 

please help me to get out of this problem.Due to this problem i am not able to go to root.[not able to execute sudo su command]:(:(:(

for ur information when i tried to access sudoers.d/readme file , it shows 0 bytes ,does that mean the readme file is corrupted or its content is deleted.



thank you.

---

### Post by nothingspecial on 2011-10-10
If you did chmod -R 777 /

then your installation is broken and you need to reinstall.

In theory it is possible to put it right but a fresh install takes about 20 minutes and putting that mess right would take a very long time.

---

### Post by nk.krishnak on 2011-10-10
thanks for ur reply, is there any way to reinstall ubuntu without losing my data.

---

### Post by mikejonesey on 2011-10-10
use a live cd to edit the sudoers file... in future if you don't know the root users password then verify the sudoers file compiles before you exit a root terminal... if you knew the root password you could have just used su but ubuntu hides that by default...

---

### Post by nothingspecial on 2011-10-10
You should have a backup anyway. Do you have a removeable drive or some cd/dvds?

You can boot a live cd and copy your data to some sort of removeable media.

---

### Post by nk.krishnak on 2011-10-10
> **nothingspecial said:**
> You should have a backup anyway. Do you have a removeable drive or some cd/dvds?

You can boot a live cd and copy your data to some sort of removeable media.



yes,i am having usb ports ,from which i can boot ubuntu.

will upgrading the os ,because i am using 10.4 will upgrading has anything to change the modes or do any good to my problem

---

### Post by nk.krishnak on 2011-10-10
> **mikejonesey said:**
> use a live cd to edit the sudoers file... in future if you don't know the root users password then verify the sudoers file compiles before you exit a root terminal... if you knew the root password you could have just used su but ubuntu hides that by default...


thanks mikejonesey , but how to edit sudoers file , because i can just open it using 

visudo command.

after that what is the content that is to be edited in the sudoers file.

---

### Post by nothingspecial on 2011-10-10
> **nk.krishnak said:**
> 

will upgrading the os ,because i am using 10.4 will upgrading has anything to change the modes or do any good to my problem

That's a good question, to which I'm afraid I don't know the answer. But please do make a copy of your data.

---

### Post by nk.krishnak on 2011-10-10
> **nothingspecial said:**
> That's a good question, to which I'm afraid I don't know the answer. But please do make a copy of your data.

thank u for u answers.

---

### Post by mikejonesey on 2011-10-10
I can write you a bash script if you like that will from a liveCD fix the permissions...

the sudoers file can be edited from any other partition or liveCD it's not encrypted and other partitions will ignore foriegn permissions...

all you need to do is mimic the permissions back, script would take about 10-20min to run...

---

### Post by nk.krishnak on 2011-10-10
> **mikejonesey said:**
> I can write you a bash script if you like that will from a liveCD fix the permissions...

the sudoers file can be edited from any other partition or liveCD it's not encrypted and other partitions will ignore foriegn permissions...

all you need to do is mimic the permissions back, script would take about 10-20min to run...

yes mike , but i am not sure about whether the script is going to help me.

will just making the sudoers content the same as the normal will solve the problem.just like copying the sudoers file content from a system and editing it on my system by booting it from live cd.will it work ???? 

if not ,,then if u believe the scripts gonna work,then we shall give a try..
thanks mike.

---

### Post by mikejonesey on 2011-10-10
apoligies for the wait...

```

#!/bin/bash

echo "What is your ubuntu partition? (/dev/sd??)"
read -p"/dev/sd" deviceID

mkdir /media/temp4567
sudo mount /dev/sd$deviceID /media/temp4567

find /etc -maxdepth 20 | while read filename; do
    if [ -a "/media/temp4567/$filename" ]; then
        curPerm=$(stat --format=%a $filename)
    sudo chmod $curPerm "/media/temp4567/$filename"
    fi
done

```

will mount your ubuntu partition into a temp dir in the /media dir, then it will check for the existance of files in the ubuntu/etc dir that exist in the liveCD's /etc dir, if it finds a match it will atain the permissions for the file from the liveCD and set the same permissions on the ubuntu/etc file...

you may need to tweek for other dirs... i have limited it to 20 as the search depth...

hope this helps...

---

### Post by nk.krishnak on 2011-10-10
> **mikejonesey said:**
> apoligies for the wait...

```

#!/bin/bash

echo "What is your ubuntu partition? (/dev/sd??)"
read -p"/dev/sd" deviceID

mkdir /media/temp4567
sudo mount /dev/sd$deviceID /media/temp4567

find /etc -maxdepth 20 | while read filename; do
    if [ -a "/media/temp4567/$filename" ]; then
        curPerm=$(stat --format=%a $filename)
    sudo chmod $curPerm "/media/temp4567/$filename"
    fi
done

```

will mount your ubuntu partition into a temp dir in the /media dir, then it will check for the existance of files in the ubuntu/etc dir that exist in the liveCD's /etc dir, if it finds a match it will atain the permissions for the file from the liveCD and set the same permissions on the ubuntu/etc file...

you may need to tweek for other dirs... i have limited it to 20 as the search depth...

hope this helps...

Thank u very much for ur efforts.I am going to try this and let u know the result.....

---

### Post by nk.krishnak on 2011-10-10
> **mikejonesey said:**
> apoligies for the wait...

```

#!/bin/bash

echo "What is your ubuntu partition? (/dev/sd??)"
read -p"/dev/sd" deviceID

mkdir /media/temp4567
sudo mount /dev/sd$deviceID /media/temp4567

find /etc -maxdepth 20 | while read filename; do
    if [ -a "/media/temp4567/$filename" ]; then
        curPerm=$(stat --format=%a $filename)
    sudo chmod $curPerm "/media/temp4567/$filename"
    fi
done

```

will mount your ubuntu partition into a temp dir in the /media dir, then it will check for the existance of files in the ubuntu/etc dir that exist in the liveCD's /etc dir, if it finds a match it will atain the permissions for the file from the liveCD and set the same permissions on the ubuntu/etc file...

you may need to tweek for other dirs... i have limited it to 20 as the search depth...

hope this helps...



AWESOME :o Mike ,, the code worked and i am now able to work with root ....but during the execution of the script it said some files like /etc/fsta../ ---permission denied.

but the permission of the  main file sudoers has been changed successfully..

now i am able to work with sudo commands..

Thanks mike ,, i really appreciate your efforts..Need to learn lot from u...
 `

---

### Post by matt_symes on 2011-10-10
Hi

I like the script mikejonsey however i am a bit concerned about the security implications of running it.

Even if the script was run for all the files on the cdrom to change permissions back on the hard drive, any updates and installed software would still have permissions of 777.

ssh would also, of course,  be broken.

This may not matter so much on a home PC but the system will still have lost some of the security that sudo gives.

Your thoughts ?

Kind regards

---

### Post by mikejonesey on 2011-10-10
yes if it's a server I'd recommend a reinstall...

if you want to reinstall all packs n updates, restored with original permissions...

```
#!/bin/bash

dpkg -l | tail -n +6 > ~/temp-dpkg.log
cat ~/temp-dpkg.log | while read packDada; do echo $packDada | cut -d " " -f 2 > ~/temp-pak.log; done

function reinstallPack(){
    while read packName; do
        sudo apt-get install --reinstall $line
    done
} < ~/temp-pak.log

rm ~/temp-pak.log
rm ~/temp-dpkg.log

```

will get a list of all installed paks and reninstall them, note a list is generated first to prevent getting stuck in a loop...

---

