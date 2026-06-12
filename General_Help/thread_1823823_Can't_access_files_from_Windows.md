---
title: "Can't access files from Windows"
date: 2011-08-12
forum: General Help
---

### Post by niamulqs on 2011-08-12
Hi,
I am a new users to Linux and I am using Ubuntu 11.04.
In my laptop, I have two logical drive C:\ and D:\. I have installed Windows XP in C drive and Ubuntu in D drive. From Ubuntu, I can mount the C drive and can access the files I stored there when logged in Windows. But from ubuntu, I can't access or see any files I stored in D drive when I logged in Windows. Even I can't mount the drive from Linux. Any help is appreciated.

---

### Post by raja.genupula on 2011-08-12
do you install with WUBI ?

---

### Post by Mark Phelps on 2011-08-12
Your wording is confusing ...

It appears that you CAN access your MS Windows file while logged into Ubuntu, right?

And, that you can NOT access your Ubuntu file while logged into MS Windows, right?

The second is NORMAL behaviour -- because MS Windows can't read or understand Linux filesystems.  And, even though the Ubuntu "file" is stored in an NTFS filesystem, inside, it's still a Linux filesystem.

---

### Post by raja.genupula on 2011-08-12
> **Mark Phelps said:**
> Your wording is confusing ...

It appears that you CAN access your MS Windows file while logged into Ubuntu, right?

And, that you can NOT access your Ubuntu file while logged into MS Windows, right?

The second is NORMAL behaviour -- because MS Windows can't read or understand Linux filesystems.  And, even though the Ubuntu "file" is stored in an NTFS filesystem, inside, it's still a Linux filesystem.

man i had faced one problem . i had installed ubuntu with wubi in my drive . so i have used one of my drive sapce . its already having some files . after installing ubuntu in that , when i am booting ubuntu the files in that drive will not be shown . i think this is the problem of him ,.

---

### Post by bcbc on 2011-08-12
> **niamulqs said:**
> Hi,
I am a new users to Linux and I am using Ubuntu 11.04.
In my laptop, I have two logical drive C:\ and D:\. I have installed Windows XP in C drive and Ubuntu in D drive. From Ubuntu, I can mount the C drive and can access the files I stored there when logged in Windows. But from ubuntu, I can't access or see any files I stored in D drive when I logged in Windows. Even I can't mount the drive from Linux. Any help is appreciated.

Alt+F2, /host
CTRL-D to bookmark.

You cannot see your windows files when booted into Wubi - I think that's what you mean. The D: drive will be mounted under /host.

---

### Post by raja.genupula on 2011-08-12
i think we dont have something like alt+f2 window in 11.04 . what we have to do at that time .

---

### Post by bcbc on 2011-08-12
> **raja.genupula said:**
> i think we dont have something like alt+f2 window in 11.04 . what we have to do at that time .

Alt-F2 is still there. Try it.

You can also click on the *home folder* icon (top left of Unity bar), then click *File system* on the left, and select the *host *folder.

---

### Post by raja.genupula on 2011-08-13
i do

---

### Post by Krishna Murthy on 2011-08-13
We can access all ext 2-3-4 files from Windows now. Download **ext2explore-2.2.71 (zip)** from sourceforge.net, extract and run ext2explore.exe. It works well for me in W7.

Do not forget to mark this thread as solved.

---

### Post by phuongdt3 on 2011-08-13
> **bcbc said:**
> Alt+F2, /host
CTRL-D to bookmark.

You cannot see your windows files when booted into Wubi - I think that's what you mean. The D: drive will be mounted under /host.

Im having similar problems,now it's ok.thanks

---

