---
title: "Can't access windows files"
date: 2010-11-02
forum: General Help
---

### Post by jatz_77 on 2010-11-02
I have dual boot. Windows XP and Ubuntu 10.04 LTS. 

I don't have a partition. I have formatted the disk to NTFS then installed XP first. After that I have installed Ubuntu 10.04 LTS under Windows.

I have decided to access Windows files from Ubuntu. 

I have used Gparted to know where my windows is. 
Then I have found this.
```
/dev/sda1 
```So I made...

```
mkdir /mnt/windows
```Then

```
mount -t ntfs /dev/sda1 /mnt/windows -o "umask=022"
```When I browse Places->Computer.  I have found the disk where supposed to be my windows files are there.  I can't access it.  

Error : Cannot mount 

However, when I browse through

**/mnt/windows**

I see all windows files there.  I can copy it if I want to. But what I want is directly access it through 
**Places->Computer**

After I restart.  I cannot anymore see the files at [B]/mnt/windows.

[/B]So I have to do it this all over again if I what to access windows files.

Do I made something wrong? Or maybe because Ubuntu is under Windows?

Any ideas...

Thank you.

---

### Post by ardunarda on 2010-11-02
you can make  [B]/mnt/windows your bookmark folder. But it is shown in place forever
[/B]

---

### Post by veggen on 2010-11-02
Just search the repo for something called "NTFS Configuration Tool". Install that, and you're done.

---

### Post by jatz_77 on 2010-11-02
Ok. Thanks for the reply guys....I try your suggestions.

---

### Post by arpanaut on 2010-11-02
From:  [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> **How do I access the Windows drives?**

 The  Windows partition where you installed Wubi is available as /host within  Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media 

---

### Post by TroN-0074 on 2010-11-02
> **jatz_77 said:**
> 

I don't have a partition. I have formatted the disk to NTFS then installed XP first. After that I have installed Ubuntu 10.04 LTS under Windows.

  I think if you did the WUBI installation your windows files will show encripted I dont really know how to change that when running ubuntu.

---

### Post by jatz_77 on 2010-11-02
@veggen

not working

@arpanaut

do I need to install wubi?

That link is intended only for issues directly related to the Wubi installer.

---

### Post by TroN-0074 on 2010-11-02
> **jatz_77 said:**
> @veggen

not working

@arpanaut

do I need to install wubi?

That link is intended only for issues directly related to the Wubi installer.

What did you see in Places>Computer>Host??

---

