---
title: "how to kill an app gently before a shutdown?"
date: 2010-02-27
forum: General Help
---

### Post by BrJohn on 2010-02-27
Hi, people

Recently bought a nobreak APC to turn it to my desktop that has installed Ubuntu 9.10.

 This computer runs almost the entire day using the torrent program Transmission.

 When the power goes out and starts nobreak it has a range of about 15 minutes to keep the desktop running, after this period the nobreak sends a signal to shutdown the Ubuntu off safely.

 The problem is that the shutdown signal that nobreak sends to Ubuntu does not close the applications that are running, such as Transmission, for example. This ends up causing problems because when it not explicitly terminated each time starts again Transmission have to check a database of torrents that are running, and it may take several hours.

 Is there any way to configure the Ubuntu's shutdown to force the closing of applications that are running BEFORE the system is turned off?

---

### Post by BrJohn on 2010-02-27
Seems that a bug is already known: [https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/307684](https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/307684)

 While this bug is not officially fixed, is there any way to run a script or something that close a specific program running before shutdown?

---

### Post by tgalati4 on 2010-02-27
I presume that you are running apcupsd.  If so, then there is a script:

tgalati4@tubuntu2:/etc/apcupsd$ cat killpower
#!/bin/sh
#
# This shell script if placed in /etc/apcupsd
# will be called by /etc/apcupsd/apccontrol before
# apcupsd kills the power in the UPS. You probably
# need to edit this to mount read-only /usr and /var,
# otherwise apcupsd will not run.

# Choose one of this solution
#mount -n -o ro /usr
#mount -n -o ro /var
#
#mount | awk '/ext2/ { print $3 }' | while read line; do
#	mount -n -o ro,remount $line
#done
#mount | awk '/ext3/ { print $3 }' | while read line; do
#	mount -n -o ro,remount $line
#done
#mount | awk '/reiserfs/ { print $3 }' | while read line; do
#	mount -n -o ro,remount $line
#done

exit 0

----------------------

You could add:

killall -s 15 transmission

---

### Post by kostkon on 2010-02-27
A simple way to do it could be to create a *.bash_logout* file in your home that tells transmission to quit, e.g.:
```
transmission -q
```
or you can even check first if transmission is running before issuing the cmd.

I am not sure if it works but you could give it a try.

---

### Post by BrJohn on 2010-02-27
Thank you, guys!

**tgalati4:**
Yes, you are right, I am running apcupsd. 
I'll try to add the line ***killall-s 15 transmission*** and return with what happened. 
But another question came up: In order to test, I ran this line (***killall-s 15 transmission***) in the terminal and nothing happened (not even an error message). But, if I type ***s****udo killall-s 15 transmission*** followed by my password then the Transmission is actually finalized. How should I add the line in the killpower file aware of this situation? 

**kostkon:**
the command ***transmission-q*** should work in the terminal? Here it did not work ... comes an error message saying that the option -q is unknown.

---

### Post by kostkon on 2010-02-27
> **BrJohn said:**
> **kostkon:**
the command ***transmission-q*** should work in the terminal? Here it did not work ... comes an error message saying that the option -q is unknown.
it works for me, even with a much older version of Transmission (1.22).

You could try the --quit option, i.e.
```
transmission --quit
```

---

### Post by tgalati4 on 2010-02-28
apcupsd normally runs with root privilege.  You can verify with:

ps -ef | grep apcupsd

So you don't need to put "sudo" in any script file that runs with root privilege.

I would actually put the killall command in the onbattery script, since you want it to shut down cleanly.  The killpower script may or may not get executed depending on the condition of your batteries and what you have set in apcupsd.  If you loose power and go on-battery, then chances are that your network will get disrupted as well, so you might as well shut down transmission during the onbattery period.

---

