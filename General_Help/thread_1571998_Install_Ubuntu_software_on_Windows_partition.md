---
title: "Install Ubuntu software on Windows partition"
date: 2010-09-10
forum: General Help
---

### Post by KingNeil on 2010-09-10
Let's say I was about to install a Windows-Ubuntu dual boot. 

From Ubuntu, is it possible to install Ubuntu software on the Windows partition? I know you can mount the Windows partition from Ubuntu, so I was wondering if you can install software on it, and then, obviously run the software.

And if you can, do you expect this will slow things down at all? Or is reading/writing the other partition just as quick as with the Ubuntu partition?

This would allow me to install Ubuntu and all necessary software without deleting/backing up files from my Windows installation.

---

### Post by dandnsmith on 2010-09-10
Not sure if you would consider [this](http://wubi-installer.org/) to meet your needs.
It allows you to install into Windows, as if installing an application, but creates a (Windows) boot menu addition which allows the (effective) dual-boot.

---

### Post by oldfred on 2010-09-10
No, part of the reason Linux is more secure than windows is permissions & ownership. NTFS does not support the Linux file structures so you cannot install on NTFS other than the previous post with wubi which creates a linux file structure inside a NTFS file.

How much space do you have, or is it time to houseclean anyway?

---

### Post by KingNeil on 2010-09-10
> **oldfred said:**
> NTFS does not support the Linux file structures so you cannot install on NTFS 

OK. Thank you for the informative response.

---

### Post by KingNeil on 2010-09-11
I just re-read oldfred's post, and I just want to be clear of something..

I want to install Ubuntu software, like, GIMP, Firefox, for example, on the Windows partition, from Ubuntu. I'm not looking to install Ubuntu itself on the Windows partition.

---

### Post by cgroza on 2010-09-11
No, NTFS has a total different structure. And even so the application wont be able to write output files on ntfs because they are not made for this.

---

### Post by coffeecat on 2010-09-11
> **KingNeil said:**
> I want to install Ubuntu software, like, GIMP, Firefox, for example, on the Windows partition, from Ubuntu. I'm not looking to install Ubuntu itself on the Windows partition.

No you cannot install Ubuntu (Linux) software on the Windows partition. Why would you want to do that? To run it in Windows, or to use the hard disk space in the Windows partition?

You can't run Linux executables in Windows because Linux executables won't run in Windows. I know that's a circular statement, but it's true. Besides the Windows directory structure is entirely different to a Linux one. Where would you put the executables?

Or if you mean to use the hard disc space in the Windows partition, you've already been given the answer. The Windows NTFS filesystem doesn't support the Unix permissions necessary for the apps to work.

But if you want GIMP and Firefox in Windows, there are Windows version for both. Also for OpenOffice, Abiword, VLC and a few other apps you may have got used to in Ubuntu.

---

### Post by oldfred on 2010-09-11
While you cannot install the same programs, many will share the same data. I have a separate NTFS data partition and have my firefox & thunderbird profiles in that partition. Both windows and linux versions then use that same data.

---

### Post by corncob on 2010-09-11
> **KingNeil said:**
> I just re-read oldfred's post, and I just want to be clear of something..

I want to install Ubuntu software, like, GIMP, Firefox, for example, on the Windows partition, from Ubuntu. I'm not looking to install Ubuntu itself on the Windows partition.

I'm not clear on what you want to do but if its running GIMP and Firefox in Windows, there are Windows versions for both these apps.

---

### Post by KingNeil on 2010-09-11
> **coffeecat said:**
> 
Or if you mean to use the hard disc space in the Windows partition, you've already been given the answer. The Windows NTFS filesystem doesn't support the Unix permissions necessary for the apps to work.

OK.

[quote=oldfred]While you cannot install the same programs, many will share the same data. I have a separate NTFS data partition and have my firefox & thunderbird profiles in that partition. Both windows and linux versions then use that same data. [/quote]

Yup. I will certainly be doing that, and I knew that was possible. 

Thank you to everyone for the useful answers.

---

