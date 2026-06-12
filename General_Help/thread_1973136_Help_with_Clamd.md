---
title: "Help with Clamd"
date: 2012-05-02
forum: General Help
---

### Post by TZSnowboardfreak on 2012-05-02
Thanks for the answers!
Now I tried bit defender, but there is no live scan. 
Then I tried avast, but live scan is only in the avast4server packet available. (I cant download that because its not free)
Then I found the ClamAV (daemon). With the program "clamdtop" I am able to see the performance and activity of the daemon. Now my new problem - The running ClamAV daemon is doing nothing :confused:

Is this correct. I edited the /etc/clamav/clamd.conf but i can't find especially configs for live scan or what happened when a infected file is found.   

Thanks in advance!

---

### Post by SeijiSensei on 2012-05-02
> **TZSnowboardfreak said:**
> Now my new problem - The running ClamAV daemon is doing nothing

How do you know this?  Have you tried downloading an infected file?  The easiest method for testing AV is to use the "eicar.com" file.  All AV scanners include this in their signature lists.

Download eicar.com from here: [http://eicar.org/download/eicar.com](http://eicar.org/download/eicar.com)

---

### Post by TZSnowboardfreak on 2012-05-03
> How do you know this?  Have you tried downloading an infected file?  The  easiest method for testing AV is to use the "eicar.com" file.  All AV  scanners include this in their signature lists.Exactly, i tried it with this file. I duplicated it in many folders and copied the folders additional fulfilled with other files on many places on my hdd.

I think I've to see in clamdtop which file is currently scanned and it has to stop me duplicating the file or better delete this file. If I am duplicating large files, clamav has to open more threads  or use CPU etc ...

 It is all time looking like this :(

[IMG]http://image-upload.de/image/mCnbsB/4deed35628.png[/IMG]

---

### Post by SeijiSensei on 2012-05-03
Well clamd is exactly what it says it is, a daemon.  You'd need a piece of client software that intervenes when you download a file and passes it to clamd for scanning.  Clamd by itself doesn't do anything but wait for scanning requests.

Now how you'd implement the client side of this, I don't know.  Clamd is usually used to provide [user-level scanning for email]("http://www.linuxquestions.org/questions/linux-general-1/how-to-connect-between-procmail-and-clamav-736906/#post3592917") with procmail and clamdscan.  

I've never used AV software on Linux except to scan email with MailScanner and web objects with SquidClamAV.  Neither of these is a solution designed for ordinary workstations. You could set up a cron job that scans your drives with clamscan periodically and emails you a report.

I've been using Linux for over fifteen years and have never had a problem with viruses or malware. Of course, I know what I'm doing, and I don't visit dodgy sites or download random stuff off the Internet.  ClamAV offers an on-demand scanner for Windows and new product for OS X.  I don't see anything similar for Linux.

---

### Post by TZSnowboardfreak on 2012-05-04
Of course ...  I didn't have a virus or something else on my linux machine and a scanner on this doesn't make scene. This is for an for an Server which is a samba gateway between 2 networks and user can transfer files by dropping it on an samba share. Additional it shall be possible to drop files via usb stick in this network. 

All this work is done but i have to ensure that known virus can not be transfered between the networks or usb ...

---

### Post by SeijiSensei on 2012-05-04
Other than frequently scanning the share with clamscan from Linux and deleting infected files, I don't think there's a way to implement that.  Anyone using the share from Windows would need a Windows-based virus scanner on his or her own machine to implement on-the-fly scanning.

If the share is relatively small, and the delay between when files are uploaded and when they are accessed by others is long enough, scanning from cron every few minutes might be a decent kludge.  A more sophisticated solution would use the find command to identify newly-uploaded files and just scan them.  An even more sophisticated solution would create a write-only quarantine area to handle uploaded files.  You'd then periodically run clamscan against files in the quarantine and release those found to be clean to a read-only share, while notifying the admin of any that have viruses.

On my (relatively fast) machine, I scanned my entire Win7 partition from Linux.  It took 28 minutes to scan 18 GB even with a lot of executables (exe's, dll's, etc.).  You're unlikely to have anywhere near the ratio of executables to total files as a complete Windows installation has, so I'd bet you could scan a gigabyte in less than a minute even without any limitations to the list of files to scan.

---

### Post by CharlesA on 2012-05-04
> **SeijiSensei said:**
> Other than frequently scanning the share with clamscan from Linux and deleting infected files, I don't think there's a way to implement that.  Anyone using the share from Windows would need a Windows-based virus scanner on his or her own machine to implement on-the-fly scanning.

I have BitDefender set to run a scan via cron at night and email me the results, so I can deal with any infected files as I see fit. I know it's not clamav, but it might give the OP some ideas.

---

### Post by TZSnowboardfreak on 2012-05-07
Hi,

on my other server i am scannning via cron at night and this is totally adequate, but in this case users will copying files to my share and read it perhapst in less a minute.

Now I have a good answer! Antivir Personal / Workstation v.3 (incl. Dazuko3). This is the live guard and (if i understand it correct) it will scan each touched file. This is exactly what i am looking for. \\:D/

Now new problems appeared  ](*,) I found only an Antivir with dazuko3 for kernel version 2.6.18, 2.6.20, 2.6.22, 2.6.24,2.6.26 or 2.6.27). Now i am looking for an ubuntu / debian with this kernel or much better an Antivir (incl. Dazuko3) for ubuntu 11.04 or 12.04 :P

---

