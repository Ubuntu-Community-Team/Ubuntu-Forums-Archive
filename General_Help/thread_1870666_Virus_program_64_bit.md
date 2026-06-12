---
title: "Virus program 64 bit"
date: 2011-10-27
forum: General Help
---

### Post by sammiev on 2011-10-27
Hi good folks. I'm running 11.10 64 bit and last week after the new updates bitdefender stop working and avast is only good for the x86. So I'm looking for a new virus program that will do the job on a 11.10 running 64 bit. What do you fine folks suggest as I was sold on either the 2 virus programs posted above. I do work on Windows computers often and like to scan my files I move to those Window machines before doing so. 
Thanks Sammiev :)

---

### Post by wolfen69 on 2011-10-27
I'm running 64bit, and the only one I see in the repos is ClamAV. It may not be the best, but it should be OK.

---

### Post by wolfgar on 2011-10-27
I had the same issue with ESET antivirus for linux.
I just went to Clamav, as well.

---

### Post by sammiev on 2011-10-27
Many thanks folks but I know ClamAV can give false positives and that is why I started this thread to see what people are using now. Hope to get a few more replies before I make my move.

Thanks folks! :)

---

### Post by oldtimer7777 on 2011-10-27
I'm using Bitdefender on 10.10..  Did updates, and NO problems.  I think it is 11.10 and some kind of incompatibility.

One of the best out there for Ubuntu. You should let Bitdefender team know.

ClavAv on Ubuntu is unreliable and it is never the latest version they have available from source on ClamAv web site.  Just saying. I always have issues with ClamAv and updates..  Bitdefender just works for me on 10.10. Period.

> **sammiev said:**
> Many thanks folks but I know ClamAV can give false positives and that is why I started this thread to see what people are using now. Hope to get a few more replies before I make my move.

Thanks folks! :)

---

### Post by guestolo on 2011-10-29
> I think it is 11.10 and some kind of incompatibilityI think so also, my BitDefender worked up to about 4 days ago
Thought about installing ClamAV, but didn't want to go that route
Used Avast a couple years back, it works alright
Thought I might give it a try again

I have 64bit architecture also sammiev, on 11.10 64bit install
So downloaded the 32bit install and force installed it on my machine
In terminal changed to directory I saved the download to
Then ran 
```
sudo dpkg -i --force-architecture avast4workstation_1.3.0-2_i386.deb
```Afterwards, went and registered with Avast!, can't run the program without inputting the registration in Avast 4 edition, unlike ver. 5 and 6
Took about 5 minutes for them to send me the key
Here's the registration link
[http://www.avast.com/registration-free-antivirus.php](http://www.avast.com/registration-free-antivirus.php)

When I went to fire up Avast!, it started, then Updated, at the end of the update I got an error, something like
"Error occurred, Invalid arguement....."
I remember that happened a couple years ago also, found this thread
Which fixed me up
[http://ubuntuforums.org/showpost.php?p=9512526&postcount=9](http://ubuntuforums.org/showpost.php?p=9512526&postcount=9)



Rebooted afterwards and that fixed the problem, hope that helps

---

### Post by sammiev on 2011-10-30
> **guestolo said:**
> I think so also, my BitDefender worked up to about 4 days ago
Thought about installing ClamAV, but didn't want to go that route
Used Avast a couple years back, it works alright
Thought I might give it a try again

I have 64bit architecture also sammiev, on 11.10 64bit install
So downloaded the 32bit install and force installed it on my machine
In terminal changed to directory I saved the download to
Then ran 
```
sudo dpkg -i --force-architecture avast4workstation_1.3.0-2_i386.deb
```Afterwards, went and registered with Avast!, can't run the program without inputting the registration in Avast 4 edition, unlike ver. 5 and 6
Took about 5 minutes for them to send me the key
Here's the registration link
[http://www.avast.com/registration-free-antivirus.php](http://www.avast.com/registration-free-antivirus.php)

When I went to fire up Avast!, it started, then Updated, at the end of the update I got an error, something like
"Error occurred, Invalid arguement....."
I remember that happened a couple years ago also, found this thread
Which fixed me up
[http://ubuntuforums.org/showpost.php?p=9512526&postcount=9](http://ubuntuforums.org/showpost.php?p=9512526&postcount=9)



Rebooted afterwards and that fixed the problem, hope that helps

Hi guestolo, and thanks it worked like a charm! :)

---

### Post by jim_deadlock on 2011-10-31
This thread intrigued me so I installed BitDefender on my 11.10 64-bit and it did indeed crash when trying to run a scan, so I contacted their tech support and after several exchanges I have a fix.

This all needs to be run as root:

```
cat /opt/BitDefender-scanner/var/lib/scan/versions.dat.* |awk '/bdcore.so.linux/{print $3}'|while read bdcore_so;do touch /opt/BitDefender-scanner/var/lib/scan/$bdcore_so;bdscan --update;ln -s /opt/BitDefender-scanner/var/lib/scan/$bdcore_so /opt/BitDefender-scanner/var/lib/scan/bdcore.so;done

rm /opt/BitDefender-scanner/var/lib/scan/bdcore.so
ln -s /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64 /opt/BitDefender-scanner/var/lib/scan/bdcore.so

```

---

### Post by sammiev on 2011-10-31
> **jim_deadlock said:**
> This thread intrigued me so I installed BitDefender on my 11.10 64-bit and it did indeed crash when trying to run a scan, so I contacted their tech support and after several exchanges I have a fix.

This all needs to be run as root:

```
cat /opt/BitDefender-scanner/var/lib/scan/versions.dat.* |awk '/bdcore.so.linux/{print $3}'|while read bdcore_so;do touch /opt/BitDefender-scanner/var/lib/scan/$bdcore_so;bdscan --update;ln -s /opt/BitDefender-scanner/var/lib/scan/$bdcore_so /opt/BitDefender-scanner/var/lib/scan/bdcore.so;done

rm /opt/BitDefender-scanner/var/lib/scan/bdcore.so
ln -s /opt/BitDefender-scanner/var/lib/scan/bdcore.so.linux-x86_64 /opt/BitDefender-scanner/var/lib/scan/bdcore.so

```

Hi Jim and Thank You for the fix. Works great! :)

---

### Post by christopher.wortman on 2011-10-31
> **sammiev said:**
> Hi good folks. I'm running 11.10 64 bit and last week after the new updates bitdefender stop working and avast is only good for the x86. So I'm looking for a new virus program that will do the job on a 11.10 running 64 bit. What do you fine folks suggest as I was sold on either the 2 virus programs posted above. I do work on Windows computers often and like to scan my files I move to those Window machines before doing so. 
Thanks Sammiev :)
Odd I can't seem to crash it on Kubuntu 11.10 64, must be either a GTK or Unity related bug.

Glad you were able to get it working!

---

### Post by hailtothethief on 2011-10-31
> **christopher.wortman said:**
> Odd I can't seem to crash it on Kubuntu 11.10 64, must be either a GTK or Unity related bug

Same here on Kubuntu 11.10 32bit

---

### Post by guestolo on 2011-10-31
Thanx Jim for digging deeper, fix works great
I'll keep both BitDefender and Avast installed for a bit

But BD is my favorite :)

---

### Post by GlammaGeek on 2012-02-25
This worked for me too!  Thanks!

---

