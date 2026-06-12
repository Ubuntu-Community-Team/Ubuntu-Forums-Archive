---
title: "Installing Windows 7"
date: 2010-12-06
forum: General Help
---

### Post by jonnyhtfc90 on 2010-12-06
I am trying to install windows 7 over Ubuntu.
However as I try and start the install, I get a message something like "Windows cannot be installed on this hard disk". I need to reformat to NTFS. Could someone please tell me how to do this?

Ta

---

### Post by karthick87 on 2010-12-06
Format it using Gparted,

Install gparted:
```
sudo apt-get install gparted
```

Launch it by running (Alt+F2)and type the following there

```
gksu gparted
```

Or you can find Gparted under System>>Administration>>Gparted

---

### Post by sp-1070 on 2010-12-06
What you should do is stop now,
you'll regret it believe me i have been there.
If you thought about it real good and you still wanna do it.
smh...
yeah use gparted like he said

---

### Post by wilee-nilee on 2010-12-06
If you choose custom from the install dvd booted you can delete the Ubuntu and make a NTFS there. Gparted works fine as well.

---

### Post by jonnyhtfc90 on 2010-12-06
I have got as far as installing and launching gparted, however I am unsure where to go from here.
Choosing the custom option on the W7 installer did not allow me to reformat, so I am still unable to install that way.

---

### Post by wilee-nilee on 2010-12-06
> **jonnyhtfc90 said:**
> I have got as far as installing and launching gparted, however I am unsure where to go from here.
Choosing the custom option on the W7 installer did not allow me to reformat, so I am still unable to install that way.

You need to be using a Ubuntu live cd that has gparted already on it to delete the operating system.

So you just installed gparted to the Ubuntu you want to remove is this correct?

Then click on the empty partition space and make at least one ntfs but 2 is probably better the first should have boot flag added with a right click on (sda1 it should be) then manage flags-click boot.

Also to delete from the Ubuntu live cd right click on the swap and turn it off.

---

### Post by jonnyhtfc90 on 2010-12-06
I can't appear to make partitions, pretty much every option is greyed out.

---

### Post by TheAnachron on 2010-12-06
Make sure to run as root.

Open terminal and type "sudo gparted"

---

### Post by Mark Phelps on 2010-12-06
If you're running using an Ubuntu LiveCD, it may have mounted the swap partition -- which will prevent you from deleting it.

You need to run the Partition Editor app and confirm that NONE of the partitions are mounted.  Only then will you be able to remove them.

---

### Post by pricetech on 2010-12-06
Your Windows 7 install disk will allow you to delete any and all existing partitions on the disk, then just let Windows 7 do it's own partitioning.

If you insist upon deleting it with Ubuntu, which is fine, use the Live CD, not the booted OS, but let Windows 7 do its own partitioning.

---

### Post by Mark Phelps on 2010-12-07
Furthermore ... if you have questions on Win7 after or during installation ... go to a Win7 forum to get answers.

Highly recommend sevenforums.com -- one of the premier Win7 forums.

---

