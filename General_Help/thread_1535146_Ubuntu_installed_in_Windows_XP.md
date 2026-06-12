---
title: "Ubuntu installed in Windows XP"
date: 2010-07-20
forum: General Help
---

### Post by DayLite on 2010-07-20
I installed Ubuntu 10.04 within Windows XP. I love it and want to partition my hard drive and install Ubuntu. Question:

1. How do I save my current Ubuntu, which includes Thunderbird and all my folders and mail, and my software programs that are installed. I want to copy all and move it to its own section on my hard drive.

Thanks

---

### Post by Mark Phelps on 2010-07-21
See the thread linked below:

[http://ubuntuforums.org/showthread.php?t=1512174]("http://ubuntuforums.org/showthread.php?t=1512174")

Check out the link in post #10 of that thread.

---

### Post by DayLite on 2010-07-21
> **Mark Phelps said:**
> See the thread linked below:

[http://ubuntuforums.org/showthread.php?t=1512174](http://ubuntuforums.org/showthread.php?t=1512174)

Check out the link in post #10 of that thread.

Thank you for responding.

I read the thread link. My challenge is that I already have Ubuntu taking up a lot of space on Windows. I need to 'free up' the space before I partition. How do I preserve the Ubuntu I have now, (copy) and then put it on its very own separate partition.

---

### Post by oldfred on 2010-07-21
Wubi is just a file inside the NTFS partition. You can back this up as it is your entire system. There is also a way to directly mount this from your new install if you want to copy data from it when it is in your backup.
/ubuntu/disks/root.disk

I would at least back up /home as that has all your user settings and user data. You can also list all install packages to make it easy to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by DayLite on 2010-07-21
> **oldfred said:**
> Wubi is just a file inside the NTFS partition. You can back this up as it is your entire system. There is also a way to directly mount this from your new install if you want to copy data from it when it is in your backup.
/ubuntu/disks/root.disk

I would at least back up /home as that has all your user settings and user data. You can also list all install packages to make it easy to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Thank you.

I just checked the space on my Windows XP C Drive.
  C Drive Free Space 49.8 GB
     Total Size 228 GB
  Ubuntu takes up 24.4 GB

I use an External Hard Drive to store all my photos, videos and documents

---

### Post by oldfred on 2010-07-21
windows really needs 20-30% free space to keep working well. If you are going to delete root.disk right away then you have more space. Otherwise I would suggest some housecleaning.

---

### Post by DayLite on 2010-07-21
> **oldfred said:**
> windows really needs 20-30% free space to keep working well. If you are going to delete root.disk right away then you have more space. Otherwise I would suggest some housecleaning.

I am now on my C:Drive, Windows XP and I am copying the complete Ubuntu folder to my External Hard Drive. Is there also someplace else on my C: Drive that I also have to copy to my External Drive?
I didn't use 'Simple Backup' because I didn't understand the directions. This will take another 190 minutes to copy it all.

---

### Post by oldfred on 2010-07-22
All of the Ubuntu system is in that one file. There may be another file for swap but that you do not need to back up.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

Did you separately back up /home? Or is your backup not a compressed file so you can directly mount it from your new install?

---

### Post by DayLite on 2010-07-22
> **oldfred said:**
> All of the Ubuntu system is in that one file. There may be another file for swap but that you do not need to back up.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?")

Did you separately back up /home? Or is your backup not a compressed file so you can directly mount it from your new install?

It was taking too long so I returned to Ubuntu and from there copied everything in my Home folder to my external drive. Yes, I realized I needed go to view and unhide folders:)
It appears that all my programs are in my Home folder.

They are not compressed, just 'copy and paste.

---

### Post by oldfred on 2010-07-22
The /home just has the data and configuration settings for your programs.

If you want a list of programs to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by DayLite on 2010-07-22
> **oldfred said:**
> The /home just has the data and configuration settings for your programs.

If you want a list of programs to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

I pasted the script in my terminal and nothing happened. It didn't put anything in my home folder.

Last night I removed Ubuntu from my C: drive by using 'Remove programs' in XP. I then removed temporary files etc and did a defrag. Then I ran my Ubuntu install CD. I let the CD partition the hard drive automatically, choosing ' side by side'. It took around 30 minutes. It never did ask me the size I wanted to leave for Ubuntu. Did it all for me. I then replaced everything in my 'Home' folder. Installed Wine and made a few adjustments and all is back :D. I even have my Thunderbird program, settings, folders and all.

I still don't understand how it knew how to partition without me telling it :confused:.

---

### Post by oldfred on 2010-07-22
A large portion of your install was the moving/shrinking of the XP partition. I has some logic to how small to make the XP and then allocates the space to root & swap. This is why I prefer to manually partition so I know what size everything is.

Glad you got it working.

---

### Post by DayLite on 2010-07-23
> **oldfred said:**
> A large portion of your install was the moving/shrinking of the XP partition. I has some logic to how small to make the XP and then allocates the space to root & swap. This is why I prefer to manually partition so I know what size everything is.

Glad you got it working.

I was waiting to make 'my choice' and by that time it was all over :shock:

What I don't understand is that my C: drive in Windows, now says:
    Used: 153 GB
    Free:  36.2 GB

I can't detect anything missing when I checked it. I am totally puzzled as to how the partition was made?

---

### Post by oldfred on 2010-07-23
If you have removed the wubi file from your windows it had more free space. Typically windows needs 20-30% free so the installer just shrank the XP partition down until it only had 36GB free. 

If you have 153GB in your windows partition you have a lot of data in that partition as windows can be in a 20-30GB system partition. Many windows users recommend a separate data partition so when (not if) you have to reinstall, your data is still in a separate partition. Another advantage of a separate NTFS data partition with Ubuntu is you can easily read & write the data partition from both Ubuntu and widnows. While you can read & write the windows system partition I try not to write into the system partition to avoid windows having issues.

When I first installed Ubuntu I created a 20GB shared  (now NTFS) partition to have most of my windows data like firefox profiles, thunderbird profile & photos. I then had set it up in both system to use the same data. My spouse only complained a little as all the data was the same and we were able to convert without too much hassle. I still have one app I use in window but am trying to wean myself from that.

---

### Post by DayLite on 2010-07-23
> **oldfred said:**
> If you have removed the wubi file from your windows it had more free space. Typically windows needs 20-30% free so the installer just shrank the XP partition down until it only had 36GB free. 

Before I installed Ubuntu in its own partition I went into windows and completely removed Ubuntu from Windows. Cleaned up all unnecessary files etc. How did it 'shrink' the XP partition down? I don't notice anything missing.

---

### Post by oldfred on 2010-07-23
When doing side by side it knows you need space for Ubuntu and have to shrink windows. I do not know what logic it uses, but it will shrink the free space in XP to make room for Ubuntu. If you do not have enough space it fails to install.

---

