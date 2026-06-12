---
title: "Difference  between cd installation and windows installation of  ubuntu?"
date: 2012-06-01
forum: General Help
---

### Post by David728 on 2012-06-01
What is the difference between installing ubuntu via a cd or a usb and installing ubuntu via windows installer? Why is it safer to install using the windows installer? When you use a cd, are you partitioning the hard drive and the windows installer doesn't partition the hard drive? 

If you install ubuntu using the windows installer, can you access the files made by windows, make changes and save the changes? Next time you boot into the computer using windows, will windows recognize those changes made in the files? 

Ubuntu comes with firefox. I prefer to use google chrome browser. If I install ubuntu via the windows installer, do I have to download and install google chrome browser one more time.

If I install via the windows installer, and boot into ubuntu, can I play the pc video games, and use the appplication softwares already installed in the hard drive before installing ubuntu?

Can someone suggest websites that explain how to install and use computers that have both windows and linux operating systems?

---

### Post by Paqman on 2012-06-01
> **David728 said:**
> When you use a cd, are you partitioning the hard drive and the windows installer doesn't partition the hard drive?

Correct. Using Wubi (**W**indows **Ub**untu **I**nstaller) creates a virtual partition that's actually just a big file sitting on the Windows filesystem, then installs Ubuntu into that.

> If you install ubuntu using the windows installer, can you access the files made by windows, make changes and save the changes? Next time you boot into the computer using windows, will windows recognize those changes made in the files? 

Yes. When you're booted into Ubuntu the Windows files can be found under /host.

> Ubuntu comes with firefox. I prefer to use google chrome browser. If I install ubuntu via the windows installer, do I have to download and install google chrome browser one more time.

Yep.

> If I install via the windows installer, and boot into ubuntu, can I play the pc video games, and use the appplication softwares already installed in the hard drive before installing ubuntu?

Nope. The two systems are completely separate, just like if you'd installed to an actual partition. You can access files on the other system, but you won't be able to run any of the applications.

> 
Can someone suggest websites that explain how to install and use computers that have both windows and linux operating systems?

This one! We can answer any problems you have. You can also try:
[http://askubuntu.com/](http://askubuntu.com/)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by Mark Phelps on 2012-06-02
> **David728 said:**
> ... 
If you install ubuntu using the windows installer, can you access the files made by windows, make changes and save the changes?

Generally a BAD idea to make any changes to the Windows filesystem while running Ubuntu.  Win7 is especially sensitive to such changes and you can end up with a corrupted filesystem, which will prevent Win7 from booting.

>  Next time you boot into the computer using windows, will windows recognize those changes made in the files? 
It will ... but NOT if you hibernate Win7 and then boot into Ubuntu.

---

### Post by sgage on 2012-06-02
> **Mark Phelps said:**
> Generally a BAD idea to make any changes to the Windows filesystem while running Ubuntu.  Win7 is especially sensitive to such changes and you can end up with a corrupted filesystem, which will prevent Win7 from booting.

Do you mean just from WUBI installs? I have been dual booting Linux with Windows for years, and with Windows 7 since it was in beta, and I've never had a problem accessing or creating or changing files in Windows from Ubuntu. The fuse drivers for ntfs strike me as rock solid.

---

### Post by Cheesemill on 2012-06-02
No, not just for Wubi installs, for any installation.

Having a separate NTFS data partition is no problem but I have had several occasions where accessing the Windows NTFS system partition from Ubuntu has left me with an un-bootable Windows.

If you must access your Windows C: drive from Ubuntu then I would highly recommend mounting it as read-only.

---

### Post by Mark Phelps on 2012-06-03
> **sgage said:**
> Do you mean just from WUBI installs? I have been dual booting Linux with Windows for years, and with Windows 7 since it was in beta, and I've never had a problem accessing or creating or changing files in Windows from Ubuntu. The fuse drivers for ntfs strike me as rock solid.

Then, you're been very fortunate ...

Unfortunately, we've also got lots of posts from other folks who have made changes to files in their Win7 OS partitions -- and then not been able to reboot into Win7.

Which is why we recommend only sharing NTFS "data" partitions.  Those don't have boot issues, so using them is not a problem.

---

### Post by Luca.es on 2012-06-03
I wouldn't recommend Wubi, it is very slow. Installing skype for example on the real deal install takes a few seconds, for me on wubi several minutes. 

if you have free space, shrink the partition in Windows, and leave it as unallocated space. Then boot the ubuntu cd, and choose install alongside windows 7. It will automatically install in the unallocated space. 

In theory I was told the uninstaller should also be be able to shrink partition but that didn't work for me.

---

