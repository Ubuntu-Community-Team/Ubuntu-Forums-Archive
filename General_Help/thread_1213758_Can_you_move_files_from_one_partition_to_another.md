---
title: "Can you move files from one partition to another?"
date: 2009-07-15
forum: General Help
---

### Post by joeval on 2009-07-15
Hopefully a simple question, but can I move files from one partition to another?
I'm looking at installing Fedora 11 on a partition on my laptop, but if I did that I'd need to get plenty of files from my Ubuntu partition to the Fedora one (just to save me booting Ubuntu for one thing and fedora for another).

Cheers

---

### Post by lisati on 2009-07-15
Simople answer: YES

Longer answer: As long as there's disk space, and nothing is expecting them to be in a particular place, I don't see a problem in moving files from one partition or disk drive to another.

---

### Post by SyL on 2009-07-15
Hi Joe,

You just have to mount Fedor's partition within Ubuntu.
Typically ```
sudo mount /dev/sd<your partition>
```Have a look here for a deeper answer: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by RoestVrijStaal on 2009-07-15
Are both partitions mounted?

Then you could drag and drop files like if they are in one folder.

You simply go to /media/<the_name_of_the_ubuntu_partition>/home/<your_account_name_in_Ubuntu>
grab / copy the files you want and paste them to your home directory of Fedora 11 :)

---

### Post by coffeecat on 2009-07-15
Aha! But there's a gotcha.

Are you talking about your own personal files or root owned files? If your own personal files, you're going to run into ownership problems between Fedora and Ubuntu. It's all down to UID (user identity number) and GID (group identity). Ubuntu sets the UID of the first-created user to 1000; Fedora to 500. If you try a drag and drop from your Fedora home folder to your Ubuntu home folder (or vice versa), you'll get a permission denied error.

A couple of ways round this:

Use root powers to copy. Trouble is, you'll probably end up with the files owned by root and you'd have to chown them each time. A bit tedious.

Set up a shared data partition for your personal files with a filesystem that **doesn't** support Linux permissions and ownerships. I.e a Microsoft one such as FAT32 or NTFS. This is one of those rare occasions when Microsoft things are useful! :wink: When you mount a FAT32 or NTFS partition from Ubuntu or Fedora, you'll get access to files without these problems. (Actually, if you look at files in an NTFS partition mounted from Linux, you'll see they're all apparently owned by root. Don't worry, this is just a quirk of the NTFS-3g driver and the way it has to mount a non-Linux filesystem. You can still work on/copy these files.)

---

### Post by joeval on 2009-07-15
Cheers for that lot guys.

Fedora isn't yet installed, so no problems with it just yet.
I think, just save the hassle, I'll move all the files (only 5gb or so) over to somewhere else and copy them back across to Fedora.  Got an old computer I can temporarily store them on.

I'm probably going to be using fedora for pretty much everything anyway, just for a change!

---

