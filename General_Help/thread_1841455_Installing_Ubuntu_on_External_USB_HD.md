---
title: "Installing Ubuntu on External USB HD"
date: 2011-09-09
forum: General Help
---

### Post by dbkats on 2011-09-09
Hi!

I'm very new to Linux, but I liked it so much I wanted to install it on my external USB HD. 

I followed some instructions that I found [here]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html"). I got stuck, though, after deleting all partitions on my HD.

My HD now consists of about 1.36 TB of free space. I am running Ubuntu from a live CD and see this through GParted partition editor. I see the same thing under "install Ubuntu". The disk is recognized under /dev/sdb. 

What I wanted to do was to create one (or several) partitions for Linux to live on, and another partition for my data. That way, if I want to NOT boot from Linux, I can access all my files (like movies). However, I am not sure how to partition my disk in order to do so.

When I select "/dev/sdb" and click on "Install Now", I get an error message:
"no root file system is defined. Please correct this from the partitioning menu". 
I guess this means I have to partition it prior to install. Can you guys help?

---

### Post by zero2xiii on 2011-09-09
Oka, I will suggest the following:

Format the drive like this,
1 TB - NTFS    Mountpoint: /Home/<username>/My_files
50 GB - Ext 3/4    Mountpoint: /
4 GB (or Ram x 1.5) - Swap    Mount Point: Cant be selected.

What ever remains can be formated to ext 3/4 aswell and set as /home mountpoint. 

Please note that all files under the home directory of linux EXCEPT the /My_files folder will be inaccessable under windows, that is why there is a seperate ntfs partition mounted at ~/My_files that windows can access as a plain drive. If you are not going to use windows to access the drive, that can be enlarged to cover all remaining space, and set to /home instead of /home/<username>/My_files.


This should be done during install.

Hope this makes sence.. Please ask if something is unclear.

I will also reccomend you UNPLUG your internal drive before installing linux, as this might install grub to the drive, and render the computer unbootable when the external drive is not attached. To boot linux then, just hit F12 on your KB during startup (boot device key) and select the external drive.

Happy installing:popcorn:

---

