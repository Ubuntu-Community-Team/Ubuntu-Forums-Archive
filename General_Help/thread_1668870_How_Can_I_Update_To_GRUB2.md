---
title: "How Can I Update To GRUB2?"
date: 2011-01-16
forum: General Help
---

### Post by sKRiBEL on 2011-01-16
I want to replace GRUB, i currently have GRUB-legacy, but i want to upgrade, last time i used GRUB2 i found it seemed cleaner, but ya, is there any simple tutorials, or anyone who could help me install GRUB2?

---

### Post by bruno9779 on 2011-01-16
Grub2 is much more complex and complete than grub-legacy and many changes have been implemented, so you will need more than a quick workaround to make use of it.

You'll find all you need to know (and some more) in this thread:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by sKRiBEL on 2011-01-16
> **bruno9779 said:**
> Grub2 is much more complex and complete than grub-legacy and many changes have been implemented, so you will need more than a quick workaround to make use of it.

You'll find all you need to know (and some more) in this thread:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Thanks man, ya i kinda figured it would be difficult to install, but I'll look into it.

---

### Post by bruno9779 on 2011-01-16
It isn't difficult to install at all, but many options have been changed, some things work differently than before.
It is better if you read at least some parts of that thread than posting back because your machine isn't booting anymore :)

---

### Post by oldos2er on 2011-01-17
It isn't difficult to install. ```
sudo apt-get update && sudo apt-get install grub-pc
```

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by wilee-nilee on 2011-01-17
Are you trying to upgrade the openSuse install to grub2.

---

### Post by sKRiBEL on 2011-01-17
> **wilee-nilee said:**
> Are you trying to upgrade the openSuse install to grub2. No It's Ubuntu, I actually read into it some more, and i actually want to upgrade from, GRUB2 1.98 to GRUB2 1.99. I kind of gave up on openSUSE because I cant get my wireless working on it, I've been trying all day. Though I have my system sorted out now. So ya I just want to upgrade to GRUB2 1.99, I'm not sure if it's worth my time or the risk, but I like the customisability I see that it has. 
Basically I want it to look like this: [http://www.jasonernst.com/wp-content/uploads/2010/05/graphical-grub.jpg](http://www.jasonernst.com/wp-content/uploads/2010/05/graphical-grub.jpg) 
Instead of this: [http://tipsfromgeek.com/wp-content/uploads/2009/11/GRUB.jpg](http://tipsfromgeek.com/wp-content/uploads/2009/11/GRUB.jpg)
It Just looks alot more sorted out, my GRUB is a jumbled mess, and im not sure how to sort it or clean it up, I guess I'll look into it more before i do decide to start playing with it, I'm not in a real rush to do it anyhow.

---

### Post by wilee-nilee on 2011-01-17
> **sKRiBEL said:**
> No It's Ubuntu, I actually read into it some more, and i actually want to upgrade from, GRUB2 1.98 to GRUB2 1.99. I kind of gave up on openSUSE because I cant get my wireless working on it, I've been trying all day. Though I have my system sorted out now. So ya I just want to upgrade to GRUB2 1.99, I'm not sure if it's worth my time or the risk, but I like the customisability I see that it has. 
Basically I want it to look like this: [http://www.jasonernst.com/wp-content/uploads/2010/05/graphical-grub.jpg](http://www.jasonernst.com/wp-content/uploads/2010/05/graphical-grub.jpg) 
Instead of this: [http://tipsfromgeek.com/wp-content/uploads/2009/11/GRUB.jpg](http://tipsfromgeek.com/wp-content/uploads/2009/11/GRUB.jpg)

So I suspect you have grub2 already unless you downgraded run this command in any Ubuntu or linux install. If you see .97=grub-leagacy 1.98 and above is grub2.


It Just looks alot more sorted out, my GRUB is a jumbled mess, and im not sure how to sort it or clean it up, I guess I'll look into it more before i do decide to start playing with it, I'm not in a real rush to do it anyhow.

What ever that image is looks like burg probably, is not grub exactly, if burg, it is grub, a earlier version with the graphic addition.
[http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing-more-gets-even-easier-with-burg-manager-app/](http://www.omgubuntu.co.uk/2010/07/burg-boot-loader-installation-themeing-more-gets-even-easier-with-burg-manager-app/)

Run this command in any of the Linux installs and post the results. This will identify the grub type. .97=grub-legacy, 1.98 or above is grub2.
```
sudo grub-install -v 
```

---

### Post by mac4rfree on 2011-01-17
One Noob question, so can we use the Burg for the Grub2 also????,, my Grub is 1.98....

---

### Post by wilee-nilee on 2011-01-17
> **mac4rfree said:**
> One Noob question, so can we use the Burg for the Grub2 also????,, my Grub is 1.98....

Yes use with caution though, grub can be reloaded from a live cd but burg would require a chroot to get into the OS from a live cd I think.

---

### Post by mac4rfree on 2011-01-19
Now i have updated the BURG.. Can i return back to GRUB2???? any guidance??

---

### Post by wilee-nilee on 2011-01-19
> **mac4rfree said:**
> Now i have updated the BURG.. Can i return back to GRUB2???? any guidance??

There appears to be a remove burg tab in BURG-Manager. I haven't used this manager but I think your safe.

If you haven't removed the original grub just reload it to the mbr with. 
sudo grub-install /dev/sda
If you have removed grub run.
sudo apt-get install grub-pc

After running either run.
sudo update-grub

I used sda assuming it is the sda hard drive, run this command to confirm the HD as sda. No numbers just the first three letters.
sudo fdisk -l

---

