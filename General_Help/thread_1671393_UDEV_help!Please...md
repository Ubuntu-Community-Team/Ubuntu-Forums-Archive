---
title: "UDEV help!Please.."
date: 2011-01-20
forum: General Help
---

### Post by phanie on 2011-01-20
I'm so frustrated that my last thread mysteriously vanished. I have been going through UDEV for a couple of weeks now. I wanna ask you guys if you could help me. Well, i create a rule a script and make the rule run the script. I also know how to put the matching keys. All of my researches and discovered solutions doesn't seem to solve  anything. So, could you guys please help me understand the UDEV of Ubuntu 9.10?please don't give me the "Writing a UDEV rule" link. Please guys. I really need this and i am so tired going on and on with it without any good result.

---

### Post by phanie on 2011-01-20
the following is the output of the udevadm info of my flash drive.

> looking at device '/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sdb/sdb1':
    
KERNEL=="sdb1"    
SUBSYSTEM=="block"
DRIVER==""
ATTR{partition}=="1"
ATTR{start}=="8192"    
ATTR{size}=="3936256"
ATTR{alignment_offset}=="0"
ATTR{stat}=="     213     4307     5360      912        0        0        0        0        0      584      912"

looking at parent device'/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0/block/sdb':

KERNELS=="sdb"    
SUBSYSTEMS=="block"
DRIVERS==""
ATTRS{range}=="16"
ATTRS{ext_range}=="256"
ATTRS{removable}=="1"
ATTRS{ro}=="0"
ATTRS{size}=="3944448"
ATTRS{alignment_offset}=="0"
ATTRS{capability}=="53"
ATTRS{stat}=="     224     4359     5864     1040        0        0        0        0        0      704     1040"
  
looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host6/target6:0:0/6:0:0:0':
    
KERNELS=="6:0:0:0"    
SUBSYSTEMS=="scsi"
DRIVERS=="sd"
ATTRS{device_blocked}=="0"
ATTRS{type}=="0"
ATTRS{scsi_level}=="3"
ATTRS{vendor}=="JetFlash"
ATTRS{model}=="Transcend 2GB   "
ATTRS{rev}=="8.07"
ATTRS{state}=="running"
ATTRS{timeout}=="30"
ATTRS{iocounterbits}=="32"
ATTRS{iorequest_cnt}=="0x134"
ATTRS{iodone_cnt}=="0x134"
ATTRS{ioerr_cnt}=="0x2"
ATTRS{modalias}=="scsi:t-0x00"    
ATTRS{evt_media_change}=="0"    
ATTRS{queue_depth}=="1"    
ATTRS{queue_type}=="none"    
ATTRS{max_sectors}=="240"

The follwing is my rules for the flash drive.

> ACTION=="add", ATTRS{vendor}=="JetFlash", SUBSYSTEM=="block", RUN+="/usr/bin/draft.sh"


The code for draft.sh is just is q query code which performs an action given that the detected device is a mass storage device.

> #!/bin/bash

for udi in $(/usr/bin/hal-find-by-capability --capability storage)
do
    if [[ $(hal-get-property --udi $udi --key storage.bus) = "usb" ]]
    then
        gnome-session-save --kill --silent
    fi
done


Well,all of this dont work and i dont know why. Please if you see any anomaly in the codes please tell me. And could anybody teach me how to know if the given rule is being run?Thank you guys.

---

### Post by phanie on 2011-01-20
Does UDEV require any command after the creation of a new code?
Just so you guys know, I place my rules in lib/udev/rules.d and my script in /usr/bin/.

---

### Post by phanie on 2011-01-20
wow,tons of views but no replies?LOL..even ubuntu people cant answer this?haha!

---

### Post by phanie on 2011-01-20
guys,please just a quick reply..it wont cost you a cent..jut tell me if i should continue this or what..

---

### Post by JKyleOKC on 2011-01-20
Have you read the "man" page at "man 7 udev" to learn the syntax for a rule?

The one time I've written a rule, I simply took an existing rule as a template and edited it to do what I wanted, which was to rename three network card interfaces to match the names I already had set up in all of my configuration files. I didn't try to run any script from the rule, so I can't help you much there except to note that the path you used for the script in the rule doesn't seem to match the path where you say it's actually stored...

Since the main purpose of udev is to create a node in /dev or to rename a network interface, your script appears to be a bit superfluous unless the device actually requires some action, though. You might study the existing rules in both rules.d directories (the one in /etc and the one in /lib) to see how they are written.

---

### Post by phanie on 2011-01-21
thanks a lot for the reply!alas!Dude,can you keep me posted if ever you encounter something that might help me?i think mu rule is fine because i tried symlink and some nodes were renamed. My only prblem now is the running of the script. Thanks again.

---

### Post by phanie on 2011-01-22
dude,i saw the error in my path. I already changed it. LOL. typo

---

### Post by JKyleOKC on 2011-01-22
Did changing it fix the problem?

You may not see any output from your script, because it will be running at the same time that the login screen is being set up. If you do need to see output from it, try adding redirection (in the /etc/rc.local command line) to a text file located in your home directory (with full path since it will run as root) that you can examine after logging in...

---

### Post by phanie on 2011-01-22
the path is really not the problem. I just made a mistake in typing it here. Thanks again dude,i'll try that. I think I am getting closer to solving this. I tried using the PROGRAM assignment and put in a path to the command which locks the desktop. I saw something in UDEV test about the PROGRAM and the command and I am surprised because I never saw that before. Only problem is,it still doesnt work.

---

### Post by phanie on 2011-01-26
I already solved this problem. Well, I used the match keys from this part except for the stat and magically it worked.

> KERNEL=="sdb1" 
SUBSYSTEM=="block"
DRIVER==""
ATTR{partition}=="1"
ATTR{start}=="8192" 
ATTR{size}=="3936256"
ATTR{alignment_offset}=="0"
ATTR{stat}==" 213 4307 5360 912 0 0 0 0 0 584 912"

The only problem is the script which I placed there to be run after adding the device. During a udev test,it runs the rule,it sees the path to the script but it wont execute the command in the script so i think this is up to another thread. Thanks for the help JKyleOKC!!

---

