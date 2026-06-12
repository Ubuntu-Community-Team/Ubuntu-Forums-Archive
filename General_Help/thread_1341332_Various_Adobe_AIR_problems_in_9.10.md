---
title: "Various Adobe AIR problems in 9.10"
date: 2009-11-29
forum: General Help
---

### Post by Leonasha on 2009-11-29
I've been trying to reinstall Adobe Air after Disk Janitor wiped out some of it's dependencies. (my bad). I am having a whole slew of problems here, for example: saved the .bin file to my home folder and tried to install it, and things looked good until installation stopped halfway through; after that I went straight to Tweetdeck and tried to install the whole kit and kaboodle that way, but ended up with a half-dozen zombie Airs; restarted and tried to install from terminal but the process stopped at 49% repeatedly citing some sort of error [[null]] - I can't seem to replicate that situation today; finally decided to try Air 2.0 beta, only to get this message once download finished: "/tmp/air2_b1_sdk_lin_111709.tbz2 could not be opened, because the associated helper application does not exist. Change the association in your preferences." 

Air and Tweetdeck were problem-free for me in Intrepid ... 

Any help would be much appreciated.

Edit: just got this message on terminal while installing something else: 

```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  adobeair1.0: Depends: adobe-certs but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
gena@gena-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
gena@gena-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobeair1.0
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 180180 files and directories currently installed.)
Removing adobeair1.0 ...
dpkg: warning: while removing adobeair1.0, directory '/var/opt/Adobe AIR/Shared' not empty so not removed.
dpkg: warning: while removing adobeair1.0, directory '/var/opt/Adobe AIR' not empty so not removed.
dpkg: warning: while removing adobeair1.0, directory '/var/opt' not empty so not removed.

```

---

### Post by Leonasha on 2009-11-30
I had a look at the wget log - here is what happened when I tried to install Air in terminal.

```
--2009-11-29 01:45:17--  (try: 4)  http://airdownload.adobe.com/air/lin/download/1.5/AdobeAIRInstaller.bin
Reusing existing connection to airdownload.adobe.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 13553300 (13M) [application/x-macbinary]
Saving to: `AdobeAIRInstaller.bin'



2009-11-29 01:52:42 (29.7 KB/s) - Read error at byte 13745012/13553300 ((null)). Retrying.
```

Since then I have sucessfully downloaded the files and run chmod on them ... but when I try to install I get the message "you do not have permission to install this".

I would appreciate any feedback on this problem. 

Should I maybe just reinstall Karmic? Please save me from doing something drastic.

---

### Post by Leonasha on 2009-11-30
hmm ... been trying to delete this reply but can't figure out how.

---

### Post by kostkon on 2009-11-30
Why not try to install Air 2 again, but this time using [the deb]("http://download.macromedia.com/pub/labs/air/2/b1/air2_b1_runtime_lin_111709.deb") instead of the tbz2 file, which by the way is for the SDK and not for the runtime.

---

### Post by Leonasha on 2009-11-30
ok ... not sure exactly what that means but I will go ahead and see what happens. thanks.

---

### Post by Leonasha on 2009-11-30
result was "File not found: You tried to install a file that does not (or no longer) exist."

---

### Post by kostkon on 2009-11-30
Try to right-click on the link for the .deb and select *Save Link As* and then save the deb file, for example, on your desktop. Then, find the file and double click on it to install it.

---

### Post by Leonasha on 2009-11-30
awesome, that worked!  thanks for your help ... & forgive my ignorance ;D

---

