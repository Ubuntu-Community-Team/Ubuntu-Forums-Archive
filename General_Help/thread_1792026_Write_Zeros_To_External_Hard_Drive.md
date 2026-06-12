---
title: "Write Zeros To External Hard Drive?"
date: 2011-06-27
forum: General Help
---

### Post by golfnut324 on 2011-06-27
Sorry if I missed a thread on this but I can't find it. I have an external hard drive connected via usb cable - /media/New Volume - and mounted in Ubuntu 10.04. How can I "write zeros" to this drive or maybe write random characters in an effort to wipe data on this disk?

Thanks!

---

### Post by nothingspecial on 2011-06-27
You want the dd command.

You can read about it here

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

or many other places on the internet.

Be absolutely sure you understand exactly what the command is going to do and that you have no typos or you could destroy your system.

---

### Post by coffeecat on 2011-06-27
You can also use shred. Check man shred for details, but the syntax for simply zeroing a whole drive, assuming it's sdb, is:

```
sudo shred -vzn 0 /dev/sdb
```

Obviously, change sdb to something else depending on what the external drive is detected as, and just as with nothingspecial's caution about dd, be sure you understand what it is going to do before you run the command. I zeroed the partition table in my main drive through a careless error once - an error I won't be doing again in a hurry!

The drive doesn't have to be mounted for shred to work, neither do you have to unmount it - so be very careful!

The logic behind those options are:

v = verbose. It takes a long time. You want to know what is going on. There is no verbose option with dd.

n 0 = no passes at all which sounds bizarre, except that the z option...

z = adds a final overwrite with zeroes. The combination of -z and -n 0 gives you one pass of zeroes only.

**EDIT**: I just noticed that you might want to write random data.

```
sudo shred -vzn 1 /dev/sdb
```

... will give you one pass of random data, and one of zeroes.

```
sudo shred -vzn 2 /dev/sdb
```

... will give you two passes of random data and one of zeroes. Increasing n to above 2 will include set patterns of non-random characters.

---

### Post by golfnut324 on 2011-06-27
I think I'll use shred per coffecat. Sorry for this stupid question, but I'm just trying to be double/triple sure, am I correct that my external drive is /dev/sdb? That is how it shows in disk utility.

Thanks again!

---

### Post by coffeecat on 2011-06-27
> **golfnut324 said:**
> I think I'll use shred per coffecat. Sorry for this stupid question, but I'm just trying to be double/triple sure, am I correct that my external drive is /dev/sdb? That is how it shows in disk utility.

Thanks again!

Yes, be double/triple sure! I can't say without seeing what disk utility shows and without knowing the size of your external hdd, but if the size and make correspond, you should be OK. If you have only one internal drive, sda, then the first external plugged in will likely be sdb. But check this every time you need to run a destructive command such as dd or shred. If you plug other USB drives in, they will be allocated sdb, sdc, sdd, etc device descriptors in the order in which they are detected by the system.

---

### Post by WorMzy on 2011-06-27
If that's what disk utility is showing, then yes. The identifiers aren't program specific, they're set by the operating system at boot time. (Or when you plug a new one in, of course)

---

### Post by golfnut324 on 2011-06-27
Thanks all. I'm good to go and shred is working!

---

