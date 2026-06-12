---
title: "Writing an image to floppy"
date: 2009-11-26
forum: General Help
---

### Post by unplugged23 on 2009-11-26
Hey there,

I've been having some trouble writing an image file to a floppy disk of mine. Since I know your wondering why I'm using a floppy, it's because I need to boot a computer with an old bios from a floppy as opposed to a cd. I've been trying to use dd but please let me know if there are any simpler apps with a GUI. I'm still pretty new to linux so bear with me here. I've been typing ```
dd if=/sbminst/ of=/dev/fd0/
``` The file I'm using here "sbminst" is on the desktop, which is also the default location of the terminal so I'm assuming I don't need to me anymore specific than this. Any ways the response I get from this is ```
dd: opening `/sbminst/': No such file or directory
``` Hopefully someone can tell me what I'm doing wrong :) 

**Happy Thanksgiving!**

---

### Post by dcstar on 2009-11-26
> **unplugged23 said:**
> Hey there,

I've been having some trouble writing an image file to a floppy disk of mine. Since I know your wondering why I'm using a floppy, it's because I need to boot a computer with an old bios from a floppy as opposed to a cd. I've been trying to use dd but please let me know if there are any simpler apps with a GUI. I'm still pretty new to linux so bear with me here. I've been typing ```
dd if=/sbminst/ of=/dev/fd0/
``` The file I'm using here "sbminst" is on the desktop, which is also the default location of the terminal so I'm assuming I don't need to me anymore specific than this. Any ways the response I get from this is ```
dd: opening `/sbminst/': No such file or directory
``` Hopefully someone can tell me what I'm doing wrong :) 


"/sbminst/" is specifying a file in the root directory, use a correct path and it will work.

---

### Post by unplugged23 on 2009-11-26
> **dcstar said:**
> "/sbminst/" is specifying a file in the root directory, use a correct path and it will work.

I moved the file to the home folder and then tried 

```
dd if=/home/sbminst/ of=/dev/fd0
```

And the return was

```
dd: opening `/home/sbminst/': No such file or directory
```

From what I can figure I must be typing in the path incorrectly..

---

### Post by unplugged23 on 2009-11-26
Any suggestions??

---

### Post by akakingess on 2009-11-26
> **unplugged23 said:**
> I moved the file to the home folder and then tried 

```
dd if=/home/sbminst/ of=/dev/fd0
```And the return was

```
dd: opening `/home/sbminst/': No such file or directory
```From what I can figure I must be typing in the path incorrectly..

The ~ symbol is the equivalent of home folder. In other words, my documents folder is in 
   ~/Documents.  See if that helps you some.

---

### Post by unplugged23 on 2009-11-26
> **akakingess said:**
> The ~ symbol is the equivalent of home folder. In other words, my documents folder is in 
   ~/Documents.  See if that helps you some.

Ok, at first I entered

```
dd if=~/sbminst/ of=dev/fd0
```

Which returned 

```
dd: opening `/home/moe/sbminst/': Not a directory
```

The I tried

```
 ~/sbminst of=dev/fd0
```

Which returned

```
dd: unrecognized operand `/home/moe/sbminst'
Try `dd --help' for more information.

```

I must be missing something pretty obvious..
Any more help?

---

### Post by unplugged23 on 2009-11-26
This doesn't need to be done from the terminal. Any program with a GUI is also welcome :D

---

### Post by iponeverything on 2009-11-26
```
dd if=~/Desktop/sbminst of=/dev/fd0

```


Where sbminst is the name of image on your desktop that your writing to the disk.

---

### Post by unplugged23 on 2009-11-26
> **iponeverything said:**
> ```
dd if=~/Desktop/sbminst of=/dev/fd0

```


Where sbminst is the name of image on your desktop that your writing to the disk.

The file is in the home folder, not on the desktop. (Sorry for the confusion) and the files name is sbminst.

However, seeing your suggestion I moved the file to the desktop and ran ```
dd if=~/desktop/sbminst of=/dev/fd0
```

Only to get

```
dd: opening `/home/moe/desktop/sbminst': No such file or directory
```

Thanks for all the help guys, I know it must seem kind of simple, but I'm just not getting it :(

---

### Post by dcstar on 2009-11-27
> **unplugged23 said:**
> The file is in the home folder, not on the desktop. (Sorry for the confusion) and the files name is sbminst.

However, seeing your suggestion I moved the file to the desktop and ran ```
dd if=~/desktop/sbminst of=/dev/fd0
```

Only to get

```
dd: opening `/home/moe/desktop/sbminst': No such file or directory
```

Thanks for all the help guys, I know it must seem kind of simple, but I'm just not getting it :(

Use capitals when people tell you to. Linux is case sensitive.

---

### Post by unplugged23 on 2009-11-27
Problem solved!! Thanks so much for bearing with me!! ::D

---

### Post by running_rabbit07 on 2009-11-27
Unplugged23, I am curious to know what file you are using to make a boot file on a floppy, I have a laptop with non-working cd-rom, but it does have a floppy drive. Are you doing this to make a boot floppy for a net boot?

Thanx for your time.

---

### Post by plucky on 2009-11-27
> **running_rabbit07 said:**
> Unplugged23, I am curious to know what file you are using to make a boot file on a floppy, I have a laptop with non-working cd-rom, but it does have a floppy drive. Are you doing this to make a boot floppy for a net boot?

Thanx for your time.

Checkout [Smart Boot Manager](http://sourceforge.net/projects/btmgr/)


Good Luck

---

