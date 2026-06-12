---
title: "Difference between Tilda and forward slash?"
date: 2010-09-12
forum: General Help
---

### Post by Alzafas on 2010-09-12
I am accessing a VPS via PuTTY that is running Ubuntu 10.04 LAMP i386 (32bit).

My problem is that when you connect, after you login, you get this:

root@nomorons:/#

If you type in cd at any point, even subdirectories it will go to this:

root@nomorons:~#

The only way to get it back to the forward slash is to type in:

cd ..

I'm wondering what is the difference between the two... you can only access certain files on both, so it's really a hassle.

---

### Post by dcstar on 2010-09-13
> **Alzafas said:**
> I am accessing a VPS via PuTTY that is running Ubuntu 10.04 LAMP i386 (32bit).

My problem is that when you connect, after you login, you get this:

root@nomorons:/#

If you type in cd at any point, even subdirectories it will go to this:

root@nomorons:~#

The only way to get it back to the forward slash is to type in:

cd ..

I'm wondering what is the difference between the two... you can only access certain files on both, so it's really a hassle.

One signifies the absolute root folder "/", the other signifies the relative user account home folder "~".

---

### Post by VCoolio on 2010-09-13
In addition: the 'cd' command without a specified target will get you to your home folder, which is '~', and 'cd ..' will get you to the parent folder of the one where you currently are, whereas 'cd -' will get you back to where you were last time after you did a 'cd /some/other/folder'. For example:
/folder/number/one
cd /folder/number/two
/folder/number/two
cd -
/folder/number/one
cd ..
/folder/number
cd ../dumber
/folder/dumber

---

