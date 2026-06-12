---
title: "Not seeing all files on NTFS partition"
date: 2010-09-11
forum: General Help
---

### Post by McTricks on 2010-09-11
I just got a new laptop and am dual booting Windows 7 and Ubuntu 10.04. I tried mounting the Windows partition to access some files (such as documents), but they won't show up in Nautilus. I double checked their location from inside Windows, but they're not where they should be.

Any idea on what to do?

---

### Post by Lukas666 on 2010-09-12
> **McTricks said:**
> I just got a new laptop and am dual booting Windows 7 and Ubuntu 10.04. I tried mounting the Windows partition to access some files (such as documents), but they won't show up in Nautilus. I double checked their location from inside Windows, but they're not where they should be.

Any idea on what to do?

How about using the command line or any other file manger (e.g. midnight commander)? Can you see them then?

---

### Post by Mark Phelps on 2010-09-12
> **McTricks said:**
> Any idea on what to do?

If you're looking for "Documents and Settings" and the like, that vanished when Win7 came on the scene.

In Win7, things are now stored in C:\Users\<username>\Documents.

Also, it's best NOT to make changes to your Win7 files from inside Ubuntu.  Runs the risk of corrupting your Win7 OS should you encounter an unclean shutdown of the partition.

---

### Post by coffeecat on 2010-09-12
> **McTricks said:**
>  I double checked their location from inside Windows, but they're not where they should be.

Actually they are probably exactly where they are shown in Nautilus. Windows has now got up to the Apple trick of showing you a folder hierarchy which isn't exactly the same as the way directories are really arranged in the filesystem. That's to protect the system from unwary users - or to make it easy for ordinary users to find their way around the parts of the filesystem they do need to explore.

What was the path in Windows of the files/folders you were trying to find?

---

