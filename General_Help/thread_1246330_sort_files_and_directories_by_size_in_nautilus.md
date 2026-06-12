---
title: "sort files and directories by size in nautilus"
date: 2009-08-21
forum: General Help
---

### Post by dumblebee100 on 2009-08-21
I need to view the directories and files sorted out by size ...

when I try to arrange items by size in nautilus context menu ..I get wrong output 
I mean first folder should be low and last folder or file should be high in memory usage ..

but when I arranged files with nautilus context menu the sizes are random ..it means the function is not working for me .......

I think it works for files perfectly ..but I want to sort out directories also 

suppose if I have directories A B C  of sizes 20mb, 10mb, 35 KBb and files D E F of sizes 20kb, 100kb, 45kb

so after sorting by size I have to get output like 

D --> 20 kb
C --> 35 kb
F --> 45 kb
E --> 100 kb
B --> 10 mb
A --> 20 mb

I dont want any directories to be first before files ....I just want to sort all directories and files by size 

is there any command or any script to do this ..

I did du -sh * to get directory sizes but cant sort it ..( hey Im bit weak in commands ) 

is there any other command which we can pipe to that command and which does work correct in all cases ..for files and directories equally ...

I want to keep that script in nautilus scripts ..because default ones doesnt work correct

---

### Post by dandnsmith on 2009-08-21
I think the problem you have is your mental model of files/directories - the directory is a holder for the entries pointing to the files it 'contains' (so the size is **not** the total size of the 'contained' files).

I hope that helps somewhat.

---

### Post by dumblebee100 on 2009-08-21
> **dandnsmith said:**
> I think the problem you have is your mental model of files/directories - the directory is a holder for the entries pointing to the files it 'contains' (so the size is **not** the total size of the 'contained' files).

I hope that helps somewhat.


I get your point but when I do my work its needed that I should frequently compare sizes between folders and files .so all I need is a way to sort out files and directories equally 
this is just a example of what Im asking 

my output of directory /boot 
```
sam@sam-desktop:/boot$ du -sh * 
520K	abi-2.6.28-9-generic
96K	config-2.6.28-9-generic
220K	grub
7.3M	initrd.img-2.6.28-9-generic
124K	memtest86+.bin
1.4M	System.map-2.6.28-9-generic
4.0K	vmcoreinfo-2.6.28-9-generic
3.4M	vmlinuz-2.6.28-9-generic

```


here grub is a folder but it showed me 220kb ..which I need ..and remaining are folders ..

so I need some sorting technique to view the output in sorted way ...

---

### Post by koenn on 2009-08-21
```
du -h | sort -g
```

---

### Post by dumblebee100 on 2009-08-21
> **koenn said:**
> ```
du -h | sort -g
```

I think u forgot * in between h and | 

the command looks like du -sh * | sort -n ..its my interpretation 


anyways that gives me sorted values only in terminal ..but how can I get those in nautilus

---

### Post by dumblebee100 on 2009-08-25
Could anyone please help me with a script which sorts files and folders in nautilus by size 

```
du -sh * | sort -n
```

this code works for me in terminal but how can I do the same in nautilus

---

### Post by dumblebee100 on 2009-10-04
Im waiting for some more useful replies ...

if you people find any other extension which can sort out files and directories based on sizes then please tell me ..

its very important for me

---

### Post by dumblebee100 on 2010-01-11
> **dumblebee100 said:**
> Im waiting for some more useful replies ...

if you people find any other extension which can sort out files and directories based on sizes then please tell me ..

its very important for me

Never mind I shifted from nautilus to dolphin and it seems to do more than I ever wanted 

Long live Dolphin

---

