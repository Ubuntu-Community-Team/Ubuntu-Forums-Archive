---
title: "Cyber Cafe Monitoring"
date: 2009-06-30
forum: General Help
---

### Post by Cyber Spot on 2009-06-30
Hi I have a cyber cafe in monterrey, mexico. I have 12 computers running ubuntu 8.10.

I wonder if there is a command or software, that can be used for knowing how many times did the cd-rw was used for burning a cd/dvd.

I want to control the usage of the cd burner, so that the employess cant steal from me by not recording the cd&#347; burned.

best wishes Joseluis Cantu

---

### Post by jpeddicord on 2009-06-30
Moved to General Help.

---

### Post by t4thfavor on 2009-06-30
Make the cdrom only usable bu a certain group, and then watch the auth.log for that group. This should get you started as I am not sure how one would accomplish these things.

---

### Post by 3rdalbum on 2009-06-30
If you have SSH login access to these machines, and can use the 'sudo' command, you can stop user accounts from being able to write to the CD device.

Let's say that the CD device is /dev/cdrom (it might be /dev/scd0 or something similar though):

```
sudo chmod a-w /dev/cdrom
```

Will stop any writing to CDs on that drive.

Explanation:

sudo means "run this as root"
chmod means "change the access permissions"
a means "for all users"
- means "remove the following permission"
w means "write permission"

And, of course, you can bring back the ability to write to CDs using the same command, but change the - to a +.

---

### Post by t4thfavor on 2009-06-30
then you can give the cdrom group w permissions, and only allow people you trust to burn cd's I thought something like a sudoers entry and then running through the log to see when it was used. butt like I said I am not too sure how to accomplish that.

---

