---
title: "Booting issues"
date: 2009-09-15
forum: General Help
---

### Post by slerk9 on 2009-09-15
Hello all,

I am new at these forums and also new at ubuntu!  I just installed it not too long ago and like it very much.

I am installing it, partitioned, with windows vista.  I tried installing it within windows, but it was sluggish, now it is fine.

Now, when I tried to boot up, I got 2 listings of ubuntu and vista at the bottom.

Later, I got 4 entries of ubuntu, and vista is the bottom.  I have to press down many times to get to vista.

Because other users of this computer prefer vista, how can i change it sothat vista automatically boots in 3 seconds, and not ubuntu?

thanks so much!

---

### Post by enriqueaf on 2009-09-15
You have to edit **/boot/grub/menu.lst**. For do that run this command in your terminal: 
```
sudo gedit /boot/grub/menu.lst
```
Then you have to edit this:
```
default		0
```
to:
```
default		5
```
I am just guessing that you have six entries, you have to count the one which says: Other operanting systems, or if the Windows entry have the flag savedefault, at the botton of the file should be something like this:
```
title		Windows 
rootnoverify	(hd0,0)
**savedefault**
makeactive
chainloader	+1
```

So if it is there Savedefault it is better that you change the line to:
```
default		saved
```

I hope it helps, by the way the next time search and you will find all the information.

---

### Post by enriqueaf on 2009-09-15
upss

---

### Post by slerk9 on 2009-09-15
Thanks, it works fine now.

Also, I have a question about why i have 5 different ubuntu entries.

they are all ubuntu 9.05 kernel 2.6.28 15, or 11, and recovery mode.

what's the difference between 15 and 11...can i delete 11? how?

---

### Post by abyrne on 2009-09-15
Running
```
sudo apt-get autoremove --purge
```
will get rid of those entries.

---

### Post by slerk9 on 2009-09-16
Thanks everyone,

when I changed the savedefault to save default, vista would not boot up so i am reverting that.

Also, if I run the Purge command, do i need to change the default number again?

---

### Post by slerk9 on 2009-09-17
Ok, I tried to run the Sudo autoremove purge command line from terminal.  It still does not work, as there are about 5 or 6 entries of ubuntu in the boot screen.
 
Can anybody help?

---

### Post by oldfred on 2009-09-17
If you want Windows to be the normal default it may be better to make it first not last in your menu. You have to move the window stanza above the automagic line as everything inbetween gets rewritten with every new kernel. 

Find these lines nearer the top of menu.lst
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=Red]Put windows stanza here[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

You then can make the default as 1 since windows is first.

You can also limit the number of kernels to show. This will not houseclean old kernels just not show them as default to load. You should keep at least 2
Find these lines and add an uncomment one:

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
howmany=2

---

