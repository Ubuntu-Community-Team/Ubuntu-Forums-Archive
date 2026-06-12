---
title: "How to use to OS - Ubuntu &amp; Mac"
date: 2010-02-09
forum: General Help
---

### Post by naparker77 on 2010-02-09
Hope someone can help.

I own a Mac and love it - but I also want to run Ubuntu.   How do I switch between the two Operating Systems.    

I currently start up in Ubuntu since installing it - how do I get back to my Mac OS ?

Please enlighten ...
Cheers and Thanks in Advance.

---

### Post by jamesisin on 2010-02-09
How did you set up your system?

If you created a dual-boot system you can only switch between the two operating systems at boot time.

Hopefully you didn't install Ubuntu over the top of your Mac OS because then it would be gone.

---

### Post by naparker77 on 2010-02-09
No option ever came up there - would I have lost everything ?

---

### Post by jamesisin on 2010-02-09
Did you install using a Live CD?

One of the installation options should have been something like "install along side your current operating system" (though I have not tried this on a Mac OS machine).

If you formated your OS drive then, yes, you formated over your Mac OS installation.  You may be able to recover your data using some Linux tools you have available within Ubuntu, but this depends upon a number of (slim) factors.

---

### Post by wsonar on 2010-02-09
to or two?

---

### Post by naparker77 on 2010-02-09
Two

---

### Post by naparker77 on 2010-02-09
> **jamesisin said:**
> Did you install using a Live CD?

One of the installation options should have been something like "install along side your current operating system" (though I have not tried this on a Mac OS machine).


Yes I used a Live CD - and I installed it next to my Mac OS    .....  Not over top.

---

### Post by jamesisin on 2010-02-09
Let's take a look.  What is the output of this command:

```
blkid
```

You can make a fancy code box like mine by copying this [NOPARSE]```
and pasting your code here
```[/NOPARSE].

---

### Post by naparker77 on 2010-02-09
```
  Blkid 
```

---

### Post by naparker77 on 2010-02-09
Is that the code you're talking about ?

---

### Post by nikwasi on 2010-02-09
I am running Ubuntu using VirtualBox. Its open source, runs great on my mac. You would not need to dual boot it! You can download from this site:  [http://www.virtualbox.org/](http://www.virtualbox.org/)

Once you have this installed. You'll want to install an ubuntu guest inside of the virtualbox. 
 [http://helpdeskgeek.com/linux-tips/how-to-install-ubuntu-in-virtualbox/](http://helpdeskgeek.com/linux-tips/how-to-install-ubuntu-in-virtualbox/)

good luck
nikwasi

---

### Post by jamesisin on 2010-02-09
> **naparker77 said:**
> Is that the code you're talking about ?

I want you to enter blkid into a terminal window and report back the output of that command ( Applications --> Accessories --> Terminal ).

---

### Post by jamesisin on 2010-02-09
> **nikwasi said:**
> I am running Ubuntu using VirtualBox.... You would not need to dual boot it!

Though I generally prefer virtualization over dual-booting, if the OP already has a dual-boot in place I see no reason to confuse the matter by moving to virtualization *at this time*.

---

### Post by naparker77 on 2010-02-14
> 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="92e6d58f-db05-42cc-b107-7e1780f878eb" TYPE="ext3" 
/dev/sda2: UUID="ea136d71-e1d6-42f6-aec4-54f9f80d1a80" TYPE="swap"

There you go ...

---

### Post by Jpenguin on 2010-02-14
I dualboot kubuntu and Leopard.  To switch- hold down'option' at startup.  Or better yet, install [http://refit.sourceforge.net/]("http://refit.sourceforge.net/")

---

### Post by naparker77 on 2010-02-14
> **Jpenguin said:**
> I dualboot kubuntu and Leopard.  To switch- hold down'option' at startup.[]("http://refit.sourceforge.net/")

Holding Option did not work - an option came up that said Windows and when I clicked it - I returned to Ubuntu.

---

### Post by flippo on 2010-02-14
Thats because you deleted your mac partition, if it was there it would have popped up on your blkid command, but all that poped up was a sqashfs, your root partition and your swap partition, none of which are mac.  You can try to recover your data, but I doubt you'll have much luck, and I don't know how once you've overwritten the filesystem.

---

### Post by naparker77 on 2010-02-14
Thanks,    Not a big deal.

Where can I get Adobe ?

---

### Post by jamesisin on 2010-02-14
Here:

[http://www.adobe.com/](http://www.adobe.com/)

---

