---
title: "USB Mount Script"
date: 2009-08-12
forum: General Help
---

### Post by kg87 on 2009-08-12
I wondered if someone could possibly help

Basically, I wondered if there was a chance of being able to run a script as soon as a usb flash disk was inserted into the machine?

I know this sounds like a virus creation tool.. but its not.

*A system running M$ windows has been infected by a USB virus, in which it latches files onto the removable media as soon as it is inserted. once that stick is introduced onto another system, that system then becomes infected.*

so, im thinking it's going to contain a line like

avgscan /media/disk1

but thats as far as i got :lolflag:

I thought about using Cron, but obviously, thats going to have to be a scheduled task. 

Any ideas?! I've had to Ban USB sticks in my house!!!

---

### Post by pizza-is-good on 2009-08-12
No idea really, but I'm interested in doing something similar, so I'll stay subscribed to the thread.

---

### Post by kg87 on 2009-08-13
Quick bump as still lacking the solution!

---

### Post by tgeer43 on 2009-08-13
I don't have the actual code for you, just an idea. How about a script with a looping structure that periodically checks for the existence of the mounted flash drive in /media and then acts accordingly. Not a very graceful solution but it ought to work. Technically you could do it with cron too but you'd be limited to checking at most once per minute with the possibility of a lag between insertion and discovery of up to a minute which may be too late for your purposes.

Ideally you are looking for an event which is triggered upon insertion of a USB flash drive and that can be intercepted. I'm not aware of one but there probably is something like that deep in Ubuntu's bowels.

BTW, are you concerned about a virus that has embedded itself in the flash drive via Windows infecting your Ubuntu system? Because that's just not going to happen. I, like many others don't even run an antivirus program in Ubuntu and it lives peacefully right alongside a Windows Vista installation.

tgeer

p.s. Note the title of my reply. It more accurately describes what you are looking for and is more likely to elicit a proper response. You may want to consider editing the title in your original  post. As it reads now, it looks like you're searching for a script to mount a USB drive rather than to detect its insertion.

---

### Post by Johnny B on 2009-08-13
have you guys heard of google?

[bash-script-detect-list-usb-flash-drives.html]("http://www.unix.com/shell-programming-scripting/104737-bash-script-detect-list-usb-flash-drives.html")

---

### Post by Johnny B on 2009-08-13
and after some modifications:

> #!/bin/bash

for DEV in /sys/block/sd*
do

	if readlink $DEV | grep -q usb ;then
		DEV=`basename $DEV`
		if [ -d /sys/block/${DEV}/${DEV}1 ] ;then
			echo $DEV
			echo "Has partitions " /sys/block/$DEV/$DEV[0-9]*
			MOUNT=`df | grep $DEV | awk '{print $6}'`
			echo scanning $MOUNT
			clamscan $MOUNT
		#else
		#	echo "Has no partitions"
		fi
		echo
	fi
done

im having some problems with this script detecting a phantom usb device (/dev/sde), where nothing is mounted, and i dont know why. after i solve that i can make it run on a loop

---

### Post by Johnny B on 2009-08-13
getting better, but still testing, how long do files in /tmp last?

```
#!/bin/bash

function scan {
for DEV in /sys/block/sd*
do
	if readlink $DEV | grep -q usb ;then
		DEV=`basename $DEV`
		if [ -d /sys/block/${DEV}/${DEV}1 ] ;then
			if [ ! -f /tmp/$DEV.lockfile ] ;then
				echo $DEV > /tmp/clamscan
				echo "Has partitions " /sys/block/$DEV/$DEV[0-9]* >> /tmp/clamscan
				MOUNT=`df | grep $DEV | awk '{print $6}'`
				echo scanning $MOUNT >> /tmp/clamscan
				clamscan -r  --infected $MOUNT >> /tmp/clamscan
				touch /tmp/$DEV.lockfile
				zenity --info --text="`cat /tmp/clamscan`"
			#else
				#echo " /tmp/$DEV.lockfile exists"
			fi
		#else
		#	echo "Has no partitions"
		fi
		#echo
	fi
done }

while true ;do scan ;done
```

---

### Post by unutbu on 2009-08-13
Here is an account of how to get Ubuntu to automatically run a backup script when a USB drive has been plugged into the machine.
You can obviously substitute any script you want in place of the backup script:

[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)

---

### Post by tgeer43 on 2009-08-14
kg87,

If you're still having problems after trying all of the above then post back here or send me a message. I've got another way of doing it that's easy and pretty bulletproof. Unfortunately I've got pressing matters at the moment so I'll give you the info only if you need it.

tgeer

---

### Post by kg87 on 2009-08-16
> **unutbu said:**
> Here is an account of how to get Ubuntu to automatically run a backup script when a USB drive has been plugged into the machine.
You can obviously substitute any script you want in place of the backup script:

[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)

Ok, the issue with this script is that im presuming you've got to edit the udev for each individual usb stick. Now that would be great if they were all the same, But i have at least 7-8 sticks, which to me looks like a lot of editing! (im shy, or lazy...)_

[COLOR="RoyalBlue"]Johnny B[/COLOR], your script looks very promising, however, im presuming this would have to be manually executed each time a device was inserted?!

[COLOR="RoyalBlue"]tgeer43[/COLOR], I am not worried about windows virii and cross contamination, but i dont trust the propriatry AV that my family are using on their pc's (Mcafee..) The Ubuntu machine is primarily a sheepdip test, and my main machine :P

I've given this some thought, and thinking on a sublinear plane. 
Would it make it easy to disable automount of usb, and only allow it if the user executed a script?

Once again, Thanks for the support guys!

---

### Post by unutbu on 2009-08-16
> **kg87 said:**
> Ok, the issue with this script is that im presuming you've got to edit the udev for each individual usb stick.


udev is flexible: you can define rules that affect specific USB drives, or you can define rules which affect all USB drives.

If you define a rule like
```

SUBSYSTEM=="block", SUBSYSTEMS=="usb", KERNEL=="sd??", RUN+="/usr/local/bin/test.sh"

```
Then /usr/local/bin/test.sh will run whenever a USB block device (hard drive) is inserted 
into the machine. See [http://ubuntuforums.org/showpost.php?p=6884128&postcount=11](http://ubuntuforums.org/showpost.php?p=6884128&postcount=11)

PS. Note while the above works on Intrepid, I believe some changes to udev have been introduced in Jaunty which may require some slight modification of the above rule. If you choose to give udev a try and run into trouble, plug a USB key into the machine and run
```

udevadm info -a -p $(udevadm info -q path -n /dev/sdb) > /tmp/udev.out

```
and post /tmp/udev.out. (In the above command, change /dev/sdb to the correct device name for the USB key too).

---

