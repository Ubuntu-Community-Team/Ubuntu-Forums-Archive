---
title: "Saving issue on external drives"
date: 2012-05-30
forum: General Help
---

### Post by Greenstar110 on 2012-05-30
Hi, and I feel I must apologise if this is a basic question, but it's driving me crazy, and it seems very obvious, ie, I cannot understand why it arises and the process is not more intuitive.
I've had several versions of Ubuntu, and found it has been the same in each.  Also Fedora.
On one occasion I lost months of files because I needed to change machine and couldn't copy files, and a friend with far more nous and experience was also foxed.
I have just installed lubuntu 11.10, and upgraded to the current version.

The problem is in writing to external drives. Whereas I can write to a USB stick, I cannot to my 1Tb back up hard drive, which appears to be read only.  I have just read an faq regarding permissions, and attempted to change via right clicking a file within, and changing 'group' to read and write. I did not have the option to change so the entire drive, which is not very convenient, nor of course open a new file in it, as  i am not allowed to write. 'Owner' is shown as already being read and write. Having done so and trying to save in the changed file I got 'cannot open file'.
Previously a second IDE drive was similarly marked read only, so I could not get my files off.

Please, this seems a very obvious glitch which means the whole install is of limited use. Is there some way to change without yards of command line? I like Ubuntu, but this is a real pain.
Tony

---

### Post by agrayray on 2012-05-30
I had a similar issue come up for me recently as well...you can see my post here

[http://ubuntuforums.org/showthread.php?t=1981448](http://ubuntuforums.org/showthread.php?t=1981448)

are you accessing this from nautilus...based upon my tests its actually nautilus that is setting the drive to ready only...you can try to remount like in my post (in my case my 1TB drive was named JEDEN)..

 sudo mount -o remount,rw '/media/JEDEN'

from the command line and see if you can save and write to it..

would be curious...

for me this worked but then when i ran nautilus on it..it becomes read only...?

---

### Post by Zimmer on 2012-05-30
> **Greenstar110 said:**
> .....

Please, this seems a very obvious glitch which means the whole install is of limited use. Is there some way to change without yards of command line? I like Ubuntu, but this is a real pain.
Tony

The simple solution I use (with external USB drives and enclosures) and it is not the 'correct' one.. involves opening Nautilus from a Terminal with gksudo nautilus , navigating to the drive and creating a folder (or two) while you have root privileges and then giving those folders the correct permissions for any user and group to create and delete files..

Files can then be written to those folders by all and sundry.

(There is a 'correct' way using commands in FSTAB to mount external drives, so I gather, but then if you try and access the drive using a different install you could hit the same problem and need to amend that FSTAB file too and reboot...) there's probably a nice page on that in the documentation...

---

### Post by deadflowr on 2012-05-30
On the external hard drive, who is the owner?
Is it root?
I asked this because, typically moving files to an area owned by root need special privleges, aka sudo.

What might be a simple solution would be to create a directory inside your external hard drive and then change the ownership to you.
First thing is you'll need to mount the drive. I mount it through nautilus, by clicking on the icon in the side pane.
Next I copy the path of the drive eg: /media/whateverthedriveiscalled.
then I open a terminal and type:

```
sudo mkdir /media/whateverthedriveiscalled/newdirectoryiammaking
```

then I change the ownership with

```
sudo chown -R myname:myname /media/whateverthedrive is called/newdirectoryiammaking
```

then you can change permisssions as you see fit.
This should give you read/write to that directory.

---

### Post by Greenstar110 on 2012-06-01
Thanks for your thoughts folks.  My 1Tb drive is partitioned into several sections. These appear here on the Linux box as separate drives filled with files. On these I have my documents, photographs, and mac stuff, like operating systems, etc. All my backups. So it's rather precious, you will appreciate, and I've done it this way because through several linux installs I have had this problem with this 1Tb and others, including secondary IDE's. My mac has always worked, drag'ndrop or just save, so this is rather puzzling for a nonce like me.
So I don't know who 'owns' it. It's just a drive with all my stuff on it, which if this Lubuntu install is to be any real use I need to access (possible now) and save to. 
I really don't want to risk losing stuff or being unable to access with my mac, which although now slow and old works 100% and has saved my neck many times! 
In my last Linux install (Fedora, which would crash on start up and closing, and finally refused to start|) I used dropbox to transfer files to the mac, where I saved them, but this is laborious and inconvenient when, for example, reviewing Gigs of images. 
The odd thing is, Dropbox and USB sticks, set up in just the same way, with pre existing files from both mac and Fedora,  read and write perfectly - so why doesn't my 1Tb? Surely this is an issue to be addressed?
thanks for your patience.

---

