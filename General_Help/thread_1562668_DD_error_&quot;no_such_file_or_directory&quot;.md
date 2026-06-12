---
title: "DD error &quot;no such file or directory&quot;"
date: 2010-08-27
forum: General Help
---

### Post by Keypel on 2010-08-27
Can somebody tell me what went wrong?

[IMG]http://img832.imageshack.us/img832/9550/61436625.gif[/IMG]

I'm trying to make a raw image (everything... including the first 512) of a usb hard drive and save it as a compressed file on my local hard drive (sda5 ntfs partition)

---

### Post by sidzen on 2010-08-27
As a guess, did you remember to add the slash after the directory name  (/etc/ );
enter what you typed to get the errror -- it is hard to tell if it is a permissions issue or one of not typing the command correctly.
If via a GUI,  the issue is most likely one of permissions.

---

### Post by Keypel on 2010-08-27
> **sidzen said:**
> As a guess, did you remember to add the slash after the directory name  (/etc/ );
enter what you typed to get the errror -- it is hard to tell if it is a permissions issue or one of not typing the command correctly.
If via a GUI,  the issue is most likely one of permissions.

I am confused as to whether or not you can see the picture I posted as it shows any mistakes I may have made.

Here is a direct link

[http://img832.imageshack.us/img832/9550/61436625.gif](http://img832.imageshack.us/img832/9550/61436625.gif)

---

### Post by Seq on 2010-08-27
> **Keypel said:**
> Can somebody tell me what went wrong?

I'm trying to make a raw image (everything... including the first 512) of a usb hard drive and save it as a compressed file on my local hard drive (sda5 ntfs partition)

Two questions:

[LIST=1]
[*]Is /mnt/sda5 mounted properly?
[*]Does your user have permissions to write to /mnt/sda5? Remember, you're running dd with sudo, but you're running gzip and the redirect as your user.
[/LIST]

---

### Post by Keypel on 2010-08-27
> Is /mnt/sda5 mounted properly?I don't know if it's mounted or not. sda6 is where ubuntu is installed and it's the same hdd so I assume sda5 is mounted?

> Does your user have permissions to write to /mnt/sda5? Remember, you're running dd with sudo, but you're running gzip and the redirect as your user.I have no idea, how do I find out?

I also tried

sudo dd if=/dev/sdb conv=sync,noerror bs=64K | gzip -c  > /media/86B07B8CB07B820B[COLOR=Red]$[/COLOR]/sdb.img.gz

but get the same **no such file or directory **error.

===================================

EDIT:

I think I got it

sudo dd if=/dev/sdb conv=sync,noerror bs=64K | gzip -c  > /media/86B07B8CB07B820B/sdb.img.gz

There was a $ I had to take out.

I couldn't get /mnt/sda5/blahblah.img.gz to work but I used the mount name of 86B07B8CB07B820B like this "/media/86B07B8CB07B820B/blahblah.img.gz" and that seems to work.

---

