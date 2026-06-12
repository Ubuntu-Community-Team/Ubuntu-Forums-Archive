---
title: "How do I know if Back in Time is working?"
date: 2012-06-22
forum: General Help
---

### Post by MarjaE on 2012-06-22
I've been doing an incremental update. According to the gui, backintime has been creating hard links for the past six hours. At one point everything else was crashing [including the system monitor], I quit backintime, I restarted the computer, and I started backintime up again.

At which point the GUI status said 'Create hard-links' The log doesn't show any more activity.

I'm not sure how to stop this and start another backup attempt.

---

### Post by MarjaE on 2012-06-22
I'm pretty sure it's not working... I stopped everything, restarted, and tried restarting backintime from scratch, but can't get it to work.

---

### Post by MarjaE on 2012-06-23
I tried running it from the terminal, and so far got a bunch of "failed to stat" errors and "Input/output error (5)"

---

### Post by MarjaE on 2012-06-23
Back in Time crashes the computer. I can restart, and resume backintime, but then it gives an error about being unable to delete the new folder. I've spent the past twelve hours trying to use backintime, and I'd like to know how to get it working again.

---

### Post by blackbird34 on 2012-06-23
Maybe you could do the following:
```
sudo apt-get purge backintime
``` (uninstalls and purges all the settings so you can  start over again)
```
sudo apt-get install backintime
```Then configure it to do its backups somewhere else in the settings and remove the old backup folder (I assume from what you're saying that you haven't had Back in Time for very long ?? otherwise park the old backups somewhere for safekeeping):
```
rm -rf /old/backup/folder
``` --Be quite sure to get the folder path right!!!  (plus you may need sudo at the start of the command, depending on the folder location).

Then attempt a new (fresh) backup.

---

### Post by robert shearer on 2012-06-23
> **MarjaE said:**
> I'm pretty sure it's not working... I stopped everything, restarted, and tried restarting backintime from scratch, but can't get it to work.

Are you still running a Wubi install or have you moved to a full Ubuntu system now...?

---

### Post by MarjaE on 2012-06-23
Full Ubuntu system. I've been using backintime for almost a year but it's just stopped working now. it hasn't successfully backed up since the 10th.

---

### Post by MarjaE on 2012-06-23
> **blackbird34 said:**
> Then configure it to do its backups somewhere else in the settings and remove the old backup folder (I assume from what you're saying that you haven't had Back in Time for very long ?? otherwise park the old backups somewhere for safekeeping):

Like I said, I've been using it for most of the past year. I have a couple old hard drives which might have enough space, I doubt it, but I haven't been able to sort out the permissions problems. So nowhere else to park the backups. Any suggestions?

---

### Post by MarjaE on 2012-06-24
I made another attempt last night. Everything froze up, so I shut down. I restarted this morning and restarted backintime. It's in that interminable "Create hard links" phase which just lasts hours and hours with no sign whether it's making progress.

---

### Post by ElSlunko on 2012-06-24
Creating hard links takes an incredible amount of time for me, too. Maybe 12 hours? Something ridiciulous for an incremental change. Also saving permissions takes a good amount of time as well. I had been using BIT for years and I think this issue started up as soon as I bought a NAS to store my files on.

I assumed it was something related to NFS or the NAS unit itself, what are you backing up to?

---

### Post by MarjaE on 2012-06-24
> **ElSlunko said:**
> Creating hard links takes an incredible amount of time for me, too. Maybe 12 hours? Something ridiciulous for an incremental change. Also saving permissions takes a good amount of time as well. I had been using BIT for years and I think this issue started up as soon as I bought a NAS to store my files on.

I assumed it was something related to NFS or the NAS unit itself, what are you backing up to?

A 1-terabyte USB hard drive using NTFS.

---

### Post by ElSlunko on 2012-06-26
Might be a bug with BIT and not related to my NAS then. 

Maybe this one? [https://bugs.launchpad.net/backintime/+bug/581614](https://bugs.launchpad.net/backintime/+bug/581614)

---

### Post by MarjaE on 2012-06-26
Yeah. I created my own bug report: [https://bugs.launchpad.net/backintime/+bug/1017195](https://bugs.launchpad.net/backintime/+bug/1017195)

But aside from that I don't know what I can do.

---

### Post by MarjaE on 2012-06-27
I let it run all day yesterday and a few hours so far today. Luckily it didn't crash the computer yesterday, but how long is it supposed to spend on "create hard-links"?

---

### Post by MarjaE on 2012-06-27
I started it again, it started with "create hard-links" and I have let it run all day ... everything else froze for a while a few hours back, but the computer hasn't crashed.

It's been well over twenty-four hours so far, although I've had to stop and shut down the computer twice in the middle. How is this supposed to work?

---

### Post by ElSlunko on 2012-06-28
It's not suppose to take very long at all. It's not functioning correctly and unfortunately it's beyond my ability to troubleshoot BIT.

---

### Post by MarjaE on 2012-06-28
I started over.

Five hours in. Everything's running badly. LibreOffice crashed a few hours back, and I'm not sure if I'll be able to salvage what I was writing. System Monitor crashed. I'm not sure why Firefox didn't crash when I opened it.

---

### Post by MarjaE on 2012-06-28
Twelve hours in. LibreOffice is still broken, but I'm not going to give up on the work I was trying to save when it froze. Firefox is erratic. Backintime is still on "create hard-links."

---

### Post by MarjaE on 2012-06-29
At thirteen hours, the desktop crashed, I rebooted, and I lost the work I was doing. :(

groan... this has been one long exercise in frustration.

---

### Post by HermanAB on 2012-06-29
Howdy, just mindlessly retrying the same thing over and over, is not going to get you anywhere.  

It sounds like you have a disk file system problem, but Linux is not Windows, meaning that you cannot repair a NTFS using Linux.  So, you first need to boot Windows and do a check disk process to repair NTFS, then repair Backintime and resume what you were doing.

Alternatively, reformat the disk with a Linux file system.

---

### Post by MarjaE on 2012-06-29
> **HermanAB said:**
> Howdy, just mindlessly retrying the same thing over and over, is not going to get you anywhere.  

It sounds like you have a disk file system problem, but Linux is not Windows, meaning that you cannot repair a NTFS using Linux.  So, you first need to boot Windows and do a check disk process to repair NTFS, then repair Backintime and resume what you were doing.

Alternatively, reformat the disk with a Linux file system.

Well, people were suggesting I needed to give it more time. Because of the setup limitations, that meant letting it resume - after shutting down and restarting, BackinTime claims to resume the backup. Then people were suggesting I needed to start over, without interrupting the backup. So I tried that once. So it wasn't the same thing over and over again, I was working on the suggestions I got and pointing out that the suggestions weren't working.

---

### Post by MarjaE on 2012-06-29
Okay, I started chkdsk as suggested.

I did not know it would take several hours. I did not know it would delete the names of all my files - but once it started, I figured I had to let it run until it could salvage the orphaned files. I do not know any way to stop the process.

Then, we had the thunderstorm and the power outage.

Now what do I do?

Has chkdsk destroyed my backups?

---

### Post by Elfy on 2012-06-30
Please stop with the incessant bumping.

If you need to add information then use the edit button.

---

### Post by MarjaE on 2012-07-07
Went back into Windows, ran chkdsk again, and ran backintime today. Back in Time finally worked, smoothly, and much faster than I can remember.

I would like to know of linux-based alternatives to chkdsk, and preferably ones which can be paused overnight so I can get some sleep.

---

### Post by cottfcfan on 2012-07-07
> **MarjaE said:**
> 
I would like to know of linux-based alternatives to chkdsk, and preferably ones which can be paused overnight so I can get some sleep.

Gnome-Disk-Utility..
I think its installed by default.

---

### Post by MarjaE on 2012-07-07
> **cottfcfan said:**
> Gnome-Disk-Utility..
I think its installed by default.

It was one of the first things I tried. It didn't find anything wrong with the disk.

---

### Post by cottfcfan on 2012-07-08
Running chkdsk in windows should not affect your linux partition.
I checked in my Windows 7, and chkdsk only scans my windows NTFS partition not my Linux EXT4.
 So the reason gnome-disk-utility found nothing wrong, could well be that there's nothing wrong with your Linux partition.
 As for your backintime problem, I too had issues with that program so switched to Luckybackup.
 While the first backup takes ages, after that your talking 1-2 minutes, plus you get a graphical output of what its doing. Never had a problem in 6 months.

---

