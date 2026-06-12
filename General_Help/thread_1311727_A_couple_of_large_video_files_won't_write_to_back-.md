---
title: "A couple of large video files won't write to back-up?"
date: 2009-11-02
forum: General Help
---

### Post by cptrohn on 2009-11-02
This is the first time I have had this particular problem.. I have a couple of large video files (about 4GB) that I really need to get backed up, but when I go to back the files up they start to wrote to the back-up drive and then I get an error saying that the file cannot continue being written to the back-up drive and it just stops right there... Now the back-up drives have plenty of room to store these files (I am not even close to getting them full) and I tried it on 2 seperate back-up drives just in case one of them was failing.. so that isn't the case either... they are .avi files that I made with K9copy.

---

### Post by peculiar penguin on 2009-11-02
Your backup drives are probably formatted with FAT32 which doesn't support files larger than 4GB. Reformat them with a non-ancient file system to get large file support, journaling and other goodies.

---

### Post by coffeecat on 2009-11-02
Is the backup drive formatted FAT32? If so, you can't write a file of more than 4GB. The filesize limit in FAT32 is 4GB. The drive needs to be formatted either NTFS, or a Linux filesystem such as ext3/4.

---

### Post by cptrohn on 2009-11-02
And THAT would be the simple answers to the problems then eh? LOL

I never knew that...  Glad I am learning something new everyday in my old age..


Thanks for the help folks!

---

### Post by coffeecat on 2009-11-02
> **cptrohn said:**
> I never knew that...  Glad I am learning something new everyday in my old age..

It's a common gotcha. I learnt this one the hard way about 3-4 years ago. You were lucky - you got an error message. I can't remember what distro/version I was using, but I was trying to copy a 4.5GB file. It simply stopped at 4GB - no error, no message, nothing. Thinking that the USB cable/connection was faulty, I kept trying it again, but each time I was left with a 4GB file on the backup drive. It was very frustrating. I couldn't understand what was going on.

---

### Post by cptrohn on 2009-11-02
> **coffeecat said:**
> It's a common gotcha. I learnt this one the hard way about 3-4 years ago. You were lucky - you got an error message. I can't remember what distro/version I was using, but I was trying to copy a 4.5GB file. It simply stopped at 4GB - no error, no message, nothing. Thinking that the USB cable/connection was faulty, I kept trying it again, but each time I was left with a 4GB file on the backup drive. It was very frustrating. I couldn't understand what was going on.

Well I couldn't for the life of me figure out what was going on.... So know I have formatted the back-ups back to ext3 and ext4 and I will have to give the whole mkdir and sudo chown mountpoint stuff a try again....

LOL such is life!

---

### Post by coffeecat on 2009-11-02
Have fun!

Of course, you could format the drive NTFS instead and not bother with all that sudo chown and sudo chmod stuff. Such is the dubious advantage of a Microsoft filesystem. :p

---

### Post by t0p on 2009-11-02
I think it's ridiculous that so many devices come formatted to FAT32.  Seeing as how most devices are made to run with Windows OSes, why don't the manufacturers format them to NTFS?

Nowadays one of the first things I do with a new storage device is format it to ext3.  But not everyone thinks to do that.  And anyway, if you were running Vista or 7, wouldn't you want your device formatted to NTFS?  That maximum file size in FAT32 is just annoying all round.

---

### Post by coffeecat on 2009-11-02
> **t0p said:**
> I think it's ridiculous that so many devices come formatted to FAT32.  Seeing as how most devices are made to run with Windows OSes, why don't the manufacturers format them to NTFS?

Probably because the manufacturers have to consider the Apple market. MacOS will read NTFS out of the box but not write to it. FAT32 is still (unfortunately) the only filesystem that all OSs can cope with.

I'd been watching the development of ntfs-3g in MacOS over the last year - it seems to be a bit behind Linux ntfs-3g in terms of stability and bugs - and I was just steeling myself to install it on my Leopard MacMini when Snow Leopard came along. I upgraded to SL and then discovered that there was a major problem with ntfs-3g in SL. That was a month or so ago, so I may be out of date here. I'll check again. But because I've been in the habit of moving big video files between MacOS, Linux and Windows, the choice of a USB drive filesystem has been a challenge. :)

I've settled on moving them around the network (at about 1 MB/sec :( ) and having a meal while I'm waiting.

---

### Post by cptrohn on 2009-11-02
Yeah... I went with ntfs just because I didn't want to screw around with mkdir and sudo chown etc....  I would love to use ext3 or ext4 but it just seems to be too much of a hassle for a back-up device...

And I do agree with the other poster about everything being fat32... it's a hassle as well...

So I formatted everything into ntsf.. (except for 1 usb stick that could not use it at all... so I'm stuck with fat32 for that one... such as life I guess.. it's too old to be used for video anyway.. but it's 64GB and can hold LOTS of other stuff. )

But thanks for the help, things are working well now! :D

---

