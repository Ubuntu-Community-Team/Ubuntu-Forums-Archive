---
title: "need some help retrieving data from a laptop"
date: 2009-11-22
forum: General Help
---

### Post by Gatorade on 2009-11-22
ok, here's the situation.

I've got a toshiba satellite laptop that won't boot up. The thing is , this thing has windows as an OS. When I turn it on , it tries to boot but then it fails and goes back to this screen. [http://s248.photobucket.com/albums/gg197/sparrow1778/?action=view&current=dannyslaptop004.flv]("http://s248.photobucket.com/albums/gg197/sparrow1778/?action=view&current=dannyslaptop004.flv")

My question,

is there any way to use the live Ubuntu disc to get the data from the hard drive?
I stuck the disc in and it booted Ubuntu 9.04 fine , but when I tried to access the HD , it gave me this error msg that it was unable to mount the drive. I expanded it to get the details.

[http://s248.photobucket.com/albums/gg197/sparrow1778/?action=view&current=dannyslaptop004.flv]("http://s248.photobucket.com/albums/gg197/sparrow1778/?action=view&current=dannyslaptop004.flv")

its telling me to run chkdisk/f , but I don't know how to do this. can anyone lend a hand please. 

I know this is more of a windows problem , but I thought maybe there was some hope in using Ubuntu as a savior.

---

### Post by tgalati4 on 2009-11-22
The video wouldn't play on my jaunty machine, so why don't you summarize the error message in text form.

How old is the disk drive?  Is it making any strange noises?  Is it still under warranty?

The Live CD and a blank USB flash disk can be used to back up your critical files, but Ubuntu must first see the disk drive.  If the Master Boot Record or Partition table is messed up, then you can try a few repair techniques.

If the one of the drive heads failed (a common problem for laptop drives) then you won't be able to mount or repair the drive.  Your only recourse is an expensive data recovery service.

Toshiba laptops tend to have better reliability than most, so let's hope that you can repair it.  Before I can suggest the first repair step, I need to know what the error message says.  You don't want to make the problem worse.

---

### Post by Gatorade on 2009-11-22
oh, sorry man , I posted the same link to the video twice.

here's a pic I took with my camera of the error message I got when I tried to access the drive using the Ubuntu live cd


[http://i248.photobucket.com/albums/gg197/sparrow1778/dannyslaptop001.jpg]("http://i248.photobucket.com/albums/gg197/sparrow1778/dannyslaptop001.jpg")

oh , the laptop isn't that old , maybe a year and a half or so. I didn't hear anything out of the ordinary , but the owner of the laptop said he had asked someone else to look at it before me and that guy said it was making some funny noises.

I was thinking of sticking the drive in the freezer for an hour or so since I've heard that can possibly get it working long enough to pull the data off it.
have you ever tried that?

yeah , about the video, that video won't play on my Ubuntu 9.04 pc either, it freezes everything up. plays fine on my other pc with windows on it though.

---

### Post by tgalati4 on 2009-11-22
Yes, I have used the freezer technique and it did work for one drive--for a short time.  

chkdsk /f is the force flag to be more aggressive when repairing the drive.

Obviously there is a problem reading the master file table (MFT) which is caused by an ntfs read error.  This does not bode well.  Normally there are multiple copies of the the MFT.  If they don't agree, you will get a message and you can choose which one to read.

Because the error reports that it can't read the MFT, I sounds like a head failure.  Linux can work around a bad master boot record and partition table and still read the file structure and mount it.  Since it can't that gives evidence that the drive heads may not be able to read at all.

The drive may still be under warranty (many have 3 year warranties).  I would replace the drive with a new one.  Place the old one in a USB enclosure or use an adapter and plug it into a ribbon cable in a desktop machine.

Use the Live CD and run the following from a terminal window:

sudo fdisk -l

Take note of what device is your hard disk.  If inside the laptop, then probably /dev/sda

sudo fsck /dev/sda

Report what happens.

---

### Post by fluffman86 on 2009-11-23
You need to grab either your Windows Recovery CD or build a UBCD4WIN CD in order to run chkdsk /f on that drive.

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
[http://ubcd4win.com](http://ubcd4win.com)

If that doesn't work, it's probably hardware.  Stick it in the freezer for about an hour, and that may buy you about 15 minutes.  After that, the disk could quite possibly be permanently dead.  Good Luck.

---

### Post by Gatorade on 2009-11-23
ok, this is what I got when I did that.

[http://i248.photobucket.com/albums/gg197/sparrow1778/Screenshot-ubuntuubuntu_.png]("http://i248.photobucket.com/albums/gg197/sparrow1778/Screenshot-ubuntuubuntu_.png")

---

### Post by tgalati4 on 2009-11-23
I presume that you can hear the disk spin up.  That would mean that it's not a drive speed or bearing problem.

Try a google search on the exact model of the drive.  See if others are having similar issues.

The linux fsck command can't repair an ntfs drive, only FAT16/32, so you will have to find a windows boot disk to run chkdsk /f or burn yourself a copy of Ultimate Boot CD.

If the drive was mountable, you could mount it by double clicking on the drive icon on the desktop.  Then you could backup files to a USB drive.  Since it won't mount, then your only recourse is to try a windows chkdsk /f repair and hope it works.

In linux you can install testdisk (sudo apt-get install testdisk) and use photorec (part of testdisk) to try a file recovery.  You will need a large flash stick or external USB drive to dump the files to.

---

### Post by Gatorade on 2009-11-23
I pulled it out, I'm gonna try the freezer trick .


thanks for the help , I got it working.

I used the windows XP installation disc and ran chkdsk and that fixed it.
I tried it with /f after chkdsk but it was saying it didn't recognize the command , so I tried it without the /f at the end and it worked.

I was just about to give up, too. when I ran it , it was stuck at 25% for a long time so I didn't think it would work , but then it started going again so I let it finish. it booted up fine after that.

---

### Post by Gatorade on 2009-11-23
oh, just a side note about the photobucket issue.

I had posted another thread about this and apparently photobucket doesn't like linux for the upload. 

this is what another member linked me to.

[http://photobucket.com/faq?catID=57&catSelected=f&topicID=623]("http://photobucket.com/faq?catID=57&catSelected=f&topicID=623")

[http://photobucket.com/faq?catID=57&catSelected=f&topicID=739]("http://photobucket.com/faq?catID=57&catSelected=f&topicID=739")

I uploaded it using windows xp , and it plays back on my xp machine, though.
this is the first thing I've found that Ubuntu doesn't do that windows does. oh well, I think I can live with that :)

---

