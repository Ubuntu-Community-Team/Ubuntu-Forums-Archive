---
title: "Clamav antivirus"
date: 2009-08-12
forum: General Help
---

### Post by karthick87 on 2009-08-12
I have recently installed clamav antivirus and fresh clam...Clamav  works fine...But i dont know  to update the virus definitions,it shows me that my virus definitions are 7 days older...How to update the virus definitions???Thanks in advance...

---

### Post by vladi11 on 2009-08-12
Here it is : [http://ubuntufs.wordpress.com/2008/02/14/update-clamav-in-ubuntu/](http://ubuntufs.wordpress.com/2008/02/14/update-clamav-in-ubuntu/)

---

### Post by XCan on 2009-08-12
I believe you can update them directly using ```
 sudo freshclam 
```

---

### Post by karthick87 on 2009-08-12
Thank you so much,i have updated my virus definitions and they are up2date now..But still it shows the following output..

karthick@karthick:~$ clamscan -r /media
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) ***
LibClamAV Warning: ***********************************************************
/media/.hal-mtab: Empty file
/media/.hal-mtab-lock: Empty file

----------- SCAN SUMMARY -----------
Known viruses: 608632
Engine version: 0.95.1
Scanned directories: 2
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Data read: 0.00 MB (ratio 0.00:1)
Time: 0.886 sec (0 m 0 s)

But when i give sudo freshclam it gives the following output,
karthick@karthick:~$ sudo freshclam
[sudo] password for karthick: 
ClamAV update process started at Wed Aug 12 23:01:18 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.95.1 Recommended version: 0.95.2
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cld is up to date (version: 51, sigs: 545035, f-level: 42, builder: sven)
daily.cvd is up to date (version: 9684, sigs: 64237, f-level: 43, builder: ccordes)

---

### Post by Wiebelhaus on 2009-08-12
[This is much better]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") in my opinion!

---

### Post by jman6495 on 2009-08-12
Don't Worry About It,
That Is The Version That Is In The Reposotories , It Is not saying that
your definitions are old but the version of the program is,
if it is really important to you then you should download the version from their website,or find the clamwin repos

---

### Post by karthick87 on 2009-08-12
Okay fine,and finally one more question..After scanning the result says tat some of my files are infected..How to remove the infected file??

---

### Post by Marti68 on 2009-08-15
Hi Weibelhaus,

Just loaded Clam AV via Ubuntu's Synapitc PM and....ERR...can't find it :-0  Found the down-loadable EXE  on their site but, as a Linux newbie, I was under the impression that apps were best installed via Synaptic.

Can I ask, why you rate the Bitdefender over Clam and can I load it in the recommended way?

Suggestion to other newbies.  DON'T blame the guys trying to help when you get stuck.  I'm sick of newbies blaming the OS not their skills and then being rude about it - rant over :-(

EDIT - sorrry should have mentioned; it's just a generall view, not specific to this thread but it bugs me.

---

### Post by karthick87 on 2009-08-18
After scanning my files,the results shows that some of my files were infected..How to delete the infected files???

---

