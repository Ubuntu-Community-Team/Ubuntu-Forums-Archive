---
title: "Add hard drive"
date: 2010-09-23
forum: General Help
---

### Post by nojstevens on 2010-09-23
I've searched the forums and whilst I can find similar questions to this I can't find a definitive answer or how to....

I have set up ubuntu on a 1TB hard drive, I let the installer do the partioning as it wanted to. All is working well. I have another 1TB drive in there that is not being used.

I would like to expand my main partion to add the spare 1TB

Is this possible without destroying my existing installation, and if so, how do I go about doing it?

Jon

---

### Post by Chame_Wizard on 2010-09-23
You have to format the new HDD to EXT4.

With Gparted.:guitar:

---

### Post by Gillingham on 2010-09-23
Yes it should be no problem at all.

What you'll need to do is when you have connected the drive is tell the computer where the drive is mounted and how it is formatted.  There is a file /etc/fstab which tells the computer which partitions to mount and where you'll need to edit this either directly or there may be other indirect methods.

I have done a quick search for "mount drives ubuntu" and come across this how-to [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux") which seems to be fairly comprehensive although does use the command line.

There might be a more graphical way using the the disk utility under system> Administration. I've only used this to check on my drives rather than to add new ones.

David

---

