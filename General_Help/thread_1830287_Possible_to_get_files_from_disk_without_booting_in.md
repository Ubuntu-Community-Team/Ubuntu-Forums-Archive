---
title: "Possible to get files from disk without booting into it?"
date: 2011-08-21
forum: General Help
---

### Post by A Traveller on 2011-08-21
Hi all.

Is there any way of being able to access data/files from a disk with Ubuntu operating system on it with another disk running Ubuntu? Don't worry, I'll give an example of what I mean, haha. For example, I used to use hard disk 1 as my main drive with the Ubuntu operating system on it. I removed that drive a long time ago and am now using hard disk 2 with Ubuntu on it. Is there any way that I can just retrieve files from hard disk 1 without having to boot into it, ie, treat hard disk 1 like a data drive and be able to copy and paste files from there onto my now main drive, hard disk 2?

If possible, would the process be more complicated if hard disk 1 used a password to log in?

Thanks.

---

### Post by dave01945 on 2011-08-21
you can just boot into a live cd/usb and access files from the disk the only issue you might have is if the files you want are encrypted and you dont have the unlock passphrase

login passwords are not a problem to bypass but encryption is technically impossible

---

### Post by A Traveller on 2011-08-21
Thanks for your reply, dave01945.

So can't I just access the contents of the old disk from my new disk? Can it be only done by booting into a live CD?

With the live CD method, how do I copy and paste the files from the disk? Do I go to the screen which checks the CD for defects, etc and choose an option there or just let the temporary Ubuntu desktop fully load and then choose an option within that? I have no idea as to what steps need to be taken.

None of my old disks are encrypted, however, they do have passwords set for logging in. I used various usernames and passwords in the past and may not have written them all down or remembered them all. Hopefully, I'll remember most of them, however, if there are one or two which I don't remember, how would I access the data on those drives? Will I need to remember my usernames also?

Thanks.

---

### Post by Nytram on 2011-08-21
You should be able to do what you're asking, although you'll probably need to be root user to avoid permission problems.

To run nautilus as root hit Alt-F2 and type **gksu nautilus**

Bear in mind it's easy to bork your system when running nautilus like this, if you make a mistake.

---

### Post by dave01945 on 2011-08-21
yes that will work you will just need to mount the second disk and browse the files

as nytram said you will have to do this as root to avoid permission problems

if you do use the live cd just choose try ubuntu then you will be on the desktop the process is the same as doing it from an installed copy

just mount the disk browse for the files you want if you have an installed copy of ubuntu on the other hdd might aswell just use that

---

### Post by hansdown on 2011-08-21
Hi  A Traveller.

To avoid not having the necessary permissions for the files,while using the live medium, open a terminal, and enter

gksudo nautilus

Hit enter, and drag and drop the files to a usb.

---

### Post by A Traveller on 2011-08-21
Thanks for the helpful replies, Nytram/dave01945/hansdown.

I attached an old disk and was able to access the files ok. Thanks for the help.

---

### Post by hansdown on 2011-08-21
Glad you got it sorted, A Traveller.

---

### Post by A Traveller on 2011-09-17
Hi all.

Unfortunately, the problem has returned!

I am able to attach my older OS disk and simply access the files on it, including those that I had on my desktop, however, I tried attaching my Ubuntu 9.10 disk and am not able to access my desktop files?

If I go to the Home folder, there are 2 folders there (Myname folder and .ecryptfs folder). I am 200% certain that I have not encrypted ANY folder or file, even by accident! I did NOT choose 'Require a password to log in and to decrypt your home folder' during installation. The Myname folder contains a file called 'Access-Your-Private-Data.desktop'. If I click it, I get an error message 'The Link "Access-Your-Private-Data.desktop" is Broken. Move it to the Rubbish Bin? This link cannot be used, because its target "/usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop" doesn't exist.'

In the Home folder, there is also another folder called '.ecryptfs'. It's contents include the following files:-

auto-mount
auto-umount
Private.mnt
Private.sig
.wrapped-passphrase.recorded
wrapped-passphrase

In the Home folder, there is also another folder called '.Private'. It contains SEVERAL folder and files, mostly starting with 'ECRYPTFS_FNEK_ENCRYPTED.etc.etc'.

I have tried using gksu nautilus and gksudo nautilus, but when I go into the Home folder and then Myname folder with these, I still get the 'Access-Your-Private-Data.desktop' file with the same error message if clicked.

Is there any way of accessing my files or will I have to re-assemble my entire pc, which I have dis-assembled and attach the disk as the main OS drive again?

I do not want to damage anything, so I am asking first. What would happen if I attach the disk to my current pc as the main OS disk and try booting into it? (The hardware has changed)

Any help would be VERY appreciated!!

Thanks.

---

### Post by cryptotheslow on 2011-09-17
Clearly you encrypted your home folder/partition on the previous install (old disk).

I believe to get into it when running your OS from the new drive, you have to chroot (change root) to the old install then you can access it using your passphrase.

Bodhi.Zazen from these forums has a good guide to doing it from a LiveCD on his site here:

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)

Scroll down to the: Access your encrypted data from a live CD  section.


Alternatively, yes you should be able boot from the old drive. Ubuntu mostly auto-detects hardware at boot so you should be fine. Only caveat would be if you had installed specific video drivers on the previous install that won't work with your new hardware - that is possible to workaround though. Once booted - provided you remember your password on the old install then you would be able to login and copy your files out to a USB drive or whatever.


In either scenario, if you have forgotten the password / passphrase from the previous install you are SOL. There is no known way to crack the encryption.

---

### Post by A Traveller on 2011-09-17
Hi cryptotheslow. Thanks for taking the time to offer your help, I really appreciate it.

I will try booting into it as per your suggestion. I just hope it doesn't cause any damage of any kind to my hardware/system. Yes, I do remember my password for logging in and I never created any 'passphrase' for any sort of encryption.

Thanks.

---

### Post by A Traveller on 2011-09-17
Hi cryptotheslow.

Thank you for your help. I booted into the disk and it all came up fine! Phew!!!!

---

### Post by cryptotheslow on 2011-09-17
Great stuff. :D

What you probably did on the previous install was take the encrypted home option during the install process. The encryption is then done using your user's password. Then every time you logon the system automatically uses your password to unencrypt with. I believe it can be slightly problematic if you subsequently change your password in certain ways - I think the gotcha is if you use "sudo passwd" you have to then manually update the encryption keys manually.... or something to that effect!

Don't ask me to explain it any better than that...  I kinda know how it works, but that's not the same as understanding how it works. If you want any more info on encryption post up in the Security section. One day I'll get around to reading up on it :D

Anyway - glad you got it sorted.

---

### Post by A Traveller on 2011-09-17
Thanks cryptotheslow.

It would have been MUCH more convenient if I didn't have to boot into the drive and could have just made the files appear, but I'm just thankful that I haven't lost my data!

I didn't change the password or use sudo passwd. Don't know where Ubunutu would have expected me to find a passphrase from if that's what would have been required!

Thanks for your advice.

---

