---
title: "Can't login after installing Open office 2.4.1"
date: 2009-07-04
forum: General Help
---

### Post by rwl925 on 2009-07-04
After installing Open Office 2.4.1, I can't log in to my Ubuntu 8.04 Netbook.
 
I get the following error:
 
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space.  Try logging in with one of the failsafe sessions to see if you can fix this problem.
 
Any ideas?  What's a failsafe session?

---

### Post by blueridgedog on 2009-07-04
Do you have a "recovery mode" option on your Grub menu?  It is typically the second one.

Also, you can check for a full disk by mounting your partition while using the LiveCD or USB key.  If you need help mounting it or seeing where it is mounted, post the output of

```
sudo fdisk -l  
```

and 
```

mount
```

If there is plenty of room on the disk, then there are other issues.

---

