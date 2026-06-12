---
title: "Cannot Copy Unreadable Folder"
date: 2009-10-25
forum: General Help
---

### Post by Seth92 on 2009-10-25
Unfortunately, my Ubuntu 9.04 crashed.  Once it reaches the desktop after booting it freezes every time.  I had been using Mozilla Thunderbird as my email client.  I decided to boot from a live disk in order to retrieve the .mozilla-thunderbird folder which contains all of my emails and accounts.  I am unable to copy that folder since Ubuntu renders it "unreadable".  How can I copy this folder as a 'live session user' or is there any other way to retrieve this folder?

---

### Post by Old *ix Geek on 2009-10-26
There are so many variables here! How are you planning to remedy this? Fresh installation? New drive? New computer?

If the hard drive crashed and is no longer bootable, but the area containing your mail is not affected, you can retrieve it by sticking it in an external drive enclosure and attaching it to a working box. That's exactly what I did a few months ago when faced with just what you're describing, and I managed to salvage about 99% of the old drive's contents.

If it's a corrupted installation [not likely--this isn't windoze!] AND you installed separate partitions for different purposes, you should be able to just do a fresh install.  I always install the OS on /, user directories on /home, and a big common partition for storage on /data, and, of course, swap space.  When I upgrade I like to do it cleanly; I format the root partition and install the new version; when I boot all my data on the other partitions are intact.

---

