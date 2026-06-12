---
title: "ubuntu 12.04 errno 5"
date: 2012-05-30
forum: General Help
---

### Post by maxearing on 2012-05-30
when i try to install 12.04 on my computer it gets like 40% done with the install then i says errno 5. right now im running 12.04 but on the "try it" so i have to have the disk i. any help is appreciated.
solved- i kept trying 64bit and it didn't work. so i tried 32 bit and a fresh CD. it worked like a charm.

---

### Post by fantab on 2012-05-31
Install it from the "try it" mode from the desktop/launcher. Keep the internet connected but choose not to install updates during installation and not to install 'restricted extras' (third party codecs/software etc.)

---

### Post by davecotefilm on 2012-05-31
How are you liking 12.04?  I installed wubi 11.10 to learn android app building, as per guidance on forums.. it's WONDERFUL!!!  my next step is a full installation.  Do you have any recommendations as to what laptop I should buy that would best maximize the linux os??

---

### Post by maxearing on 2012-05-31
> **fantab said:**
> Install it from the "try it" mode from the desktop/launcher. Keep the internet connected but choose not to install updates during installation and not to install 'restricted extras' (third party codecs/software etc.)
i just tried that with no luck, im still getting errno 5

---

### Post by fantab on 2012-05-31
Check the integrity of the CD or .iso with md5sum check... [**Here**]("https://help.ubuntu.com/community/HowToMD5SUM"). 

How did you partition your HDD?
There is a possibility that you HDD could be corrupt, there could be bad sectors in it.

To get you started, use Disk Utility from LiveCD to see if there are any errors in the Hard Disk and its partitions. Try the options SMART DATA and Check FileSystem.

---

### Post by maxearing on 2012-05-31
Is there a specific kind of disk I specific type of disk I should be using?

---

### Post by fantab on 2012-06-01
> **maxearing said:**
> Is there a specific kind of disk I specific type of disk I should be using?

No, there are no special Disks or 'specific' disks for Linux, if that is what you mean to ask.

Also when you are asking for help try to give as many details about your computer and the nature of problem.

~We would like to know if its a Laptop or Desktop? 
~Are you Single Booting or Dual Booting? 
~Before Ubuntu what Operating System were you using? Are you still using it on the computer in question?
~Details about your Hard Disk [HDD]; do you have a single HDD or more? 
~How did you partition you HDD, what is your Partition Scheme?
~How are you trying to install Ubuntu, "Install Ubuntu Alongside Windows" or 'Replace Windows with Ubuntu" or 'Something Else"?

The more information you give us, better it will be for the forum to help you with.

Have you tried the suggestions from my previous post #5? What did you find?
Post the output of the following command from Terminal using LiveCD:
```
$ sudo fdisk -l
```

---

### Post by maxearing on 2012-06-01
i figured it out
solved- i kept trying 64bit and it didn't work. so i tried 32 bit and a fresh CD. it worked like a charm.

---

### Post by fantab on 2012-06-01
> **maxearing said:**
> i figured it out
solved- i kept trying 64bit and it didn't work. so i tried 32 bit and a fresh CD. it worked like a charm.

I am glad you Solved it. Mark the thread Solved using thread tools.

---

