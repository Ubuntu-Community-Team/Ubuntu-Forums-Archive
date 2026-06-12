---
title: "Can't write files to Kindle"
date: 2011-12-28
forum: General Help
---

### Post by yogaman on 2011-12-28
My Kindle auto-mounts when plugged in. It mounts from drive /dev/sdc1. However, I can't write any files to it. I can read its entire directory structure but can't write anything. I am able to unmount it successfully using:

sudo umount /dev/sdc1

After doing the above, I can't see sdc1 to mount it again. 

I am really confused as to what's going on. When the device is mounted, all the Kindle's subdirectories show that I have rwx permissions. What gives??

thanks.

---

### Post by yogaman on 2011-12-28
Oh one more thing...

I saw on another thread a suggestion to install mtpfs since that is the protocol Kindle uses for mass storage devices. I did that and still don't have any luck.

---

### Post by lindsay7 on 2011-12-28
Try installing Calbre which is a ebook management program.  It works with Kindle and you can load books to your ereader with it.

---

### Post by rng on 2011-12-28
The 'mount' command output should show the options. What is the output of mount command?

---

### Post by yogaman on 2011-12-28
> **lindsay7 said:**
> Try installing Calbre which is a ebook management program.  It works with Kindle and you can load books to your ereader with it.

I can't write ANY files to the Kindle - not even through Calibre. In fact, Calibre can't read the device either. They recommend I reset the Kindle to factory settings or use another USB port/cable. I will try both of those.

---

### Post by yogaman on 2011-12-28
> **rng said:**
> The 'mount' command output should show the options. What is the output of mount command?

Here is the output of the mount command:

/dev/sdc1 on /media/Kindle type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

---

### Post by oldos2er on 2011-12-28
Which Kindle do you have?

> sudo umount /dev/sdc1 You should unmount from the mount point, not the device: > umount /media/Kindle

---

### Post by rng on 2011-12-28
Try 'sudo nautilus' . In nautilus, choose kindle disk and try to make new folder or empty document. Or try 'sudo gedit' and try to make and save a text file on kindle disk.

---

### Post by oldos2er on 2011-12-28
> **rng said:**
> Try 'sudo nautilus' . In nautilus, choose kindle disk and try to make new folder or empty document. Or try 'sudo gedit' and try to make and save a text file on kindle disk.

Both Nautilus and gedit are graphical programs, so they should be started with either **gksudo** or **gksu** instead of sudo.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

At any rate there should be no reason to have to use root privileges to access the Kindle.

---

### Post by yogaman on 2011-12-28
> **rng said:**
> Try 'sudo nautilus' . In nautilus, choose kindle disk and try to make new folder or empty document. Or try 'sudo gedit' and try to make and save a text file on kindle disk.

Well I'm getting closer (farther??). I used nautilus as recommended to get into the Kindle as root. I can create a folder and file of zero bytes. However, if I try and copy a file into the Kindle I get the attached screen shot.

I can't link to the Kindle via Windows either. Sheesh... Amazon doesn't know what the problem is either.

---

### Post by dandnsmith on 2011-12-28
Just in case there's any lingering doubt:
- no special protocols are involved
- I just copied a book file from my desktop PC to my Kindle, using the second pane facility in Nautilus
- you need to copy to the documents folder, for books
- I didn't do anything to mount the Kindle except to insert it's usb lead into a socket
- I'm certainly not using sudo or gksudo to get things done.

HTH

---

### Post by fragos on 2011-12-28
I seem to remember reading about most of Kindel's storage is allocated for media purchased from Amazon. Could the OP's problem be where they were trying to store their media. dandnsmith did mention success copying books to the "documents" folder. Is that the area Kindel reserves for non-Amazon media?

---

### Post by yogaman on 2011-12-28
> **fragos said:**
> I seem to remember reading about most of Kindel's storage is allocated for media purchased from Amazon. Could the OP's problem be where they were trying to store their media. dandnsmith did mention success copying books to the "documents" folder. Is that the area Kindel reserves for non-Amazon media?

I can't seem to write any files into the Kindle from USB. I have tried writing a free book with no DRM into the Documents directory and also an MP3 music file into the Music directory. It won't let me do either one. 

Since I can't write files into the Kindle using USB with either Windows or Ubuntu, I am left to conclude that something is wrong with the Kindle drive. I have hard reset the device three times and that hasn't fixed the problem either. WhisperSync only works to download books.

I tried to upload an MP3 file to the cloud and download it through WhisperSync but the Kindle 2 doesn't support that function (I guess it is only available for the Kindle Fire). So it seems I am stuck with a partially functional device. Anyone have any other ideas??

Thanks to all for the help thus far. ](*,)

---

### Post by dandnsmith on 2011-12-29
The documents folder is where the Kindle expects to find the ebooks - whether purchased from amazon or not (I've tried at least 3 other sources).
There are other areas, used for 'audible content' and 'music', inaddition to the 'system' content.

If a different usb lead, different usb ports, and different OS (especially Windows) all show the same, erroneous behaviour, then we have to assume the device is faulty and needs 'repair'.

Did amazon ask about the release of the Kindle software?

---

### Post by oldos2er on 2011-12-29
If your Kindle's not working properly in either Windows or Ubuntu, I'd contact Amazon about a replacement. Is it still under warranty?
[http://www.amazon.com/gp/help/customer/display.html/ref=kinw_myk_lnav_help?ie=UTF8&nodeId=200127470](http://www.amazon.com/gp/help/customer/display.html/ref=kinw_myk_lnav_help?ie=UTF8&nodeId=200127470)

---

### Post by yogaman on 2011-12-29
> **oldos2er said:**
> If your Kindle's not working properly in either Windows or Ubuntu, I'd contact Amazon about a replacement. Is it still under warranty?
[http://www.amazon.com/gp/help/customer/display.html/ref=kinw_myk_lnav_help?ie=UTF8&nodeId=200127470](http://www.amazon.com/gp/help/customer/display.html/ref=kinw_myk_lnav_help?ie=UTF8&nodeId=200127470)

No, its not under warrenty. I guess I have to just live with this or get another device.Thanks for the help guys.

---

