---
title: "access windows partition from ubuntu"
date: 2006-02-26
forum: General Help
---

### Post by pliu59 on 2006-02-26
My windows partition is at /media/hda2. When I try to access it and view it, it says permission denied. How may I access the windows partition from ubuntu? The only way that I can access it, which is kind of weird, is by going to System --> Administration --> Disks --> Partition 2 --> Browse. Then I'm able to see the files on my windows partition. Other than that, I can't access it when I go to Computer --> hda2. It just says I don't have the permissions to access it, and it says that the owner is root, but ubuntu doesn't have a root user. Any help is appreciated. Thanks in advance.

---

### Post by bluevoodoo1 on 2006-02-26
This link might be of some use...
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by pliu59 on 2006-02-26
thanks, I got it to work =)

---

### Post by jamesr on 2006-02-26
How?
What was the problem?

---

### Post by pliu59 on 2006-02-26
I modified /etc/fstab. 

Before, there was a line like

/dev/hda1       /media/windows  ntfs    default   0       0

Then I changed it to

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

and then I rebooted and it seemed to work. I just followed the directions in the link that bluevoodoo1 had given me.

---

