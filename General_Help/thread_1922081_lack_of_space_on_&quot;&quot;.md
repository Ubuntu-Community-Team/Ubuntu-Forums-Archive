---
title: "lack of space on &quot;/&quot;"
date: 2012-02-08
forum: General Help
---

### Post by sagesunil on 2012-02-08
I want to upgrade my current OS.When i am try to upgrade  my current OS then i am getting massage that  there is no enough space on "/".
Let me know hot to manage space on root folder if i am going out of space.


Thanks

---

### Post by Herman on 2012-02-08
The easiest and fastest way to clear yourself a little space on / is to get rid of downloaded copies of software packages that accumulate in /var/cache/apt/archives.

You can take a look at how many you have by running this command,
```
ls /var/cache/apt/archives/
```

You can run df -h to see how much room you have before cleaning,
```
df -h
```

Then run this command to get rid of all the stored .deb files,
```
sudo apt-get clean
```

Then when you run the first two commands again you will be able to see how much difference cleaning your apt cache has made.

---

### Post by Herman on 2012-02-08
Another good way to reduce the amount of disk space your operating system needs is to install a program called localepurge.
```
sudo apt-get install localepurge
```
Ubuntu is an operating system that is made to be useable in as many languages as possible, and to be prepared for that requires a lot of extra files. If you only speak one or two languages and if you're the only user of the computer, you can set Localepurge up to screen out files specific to all other languages except the ones you will use.
It will run automatically every time you install software or get updates, so it is no trouble at all to use.

---

### Post by Herman on 2012-02-08
Most people install Ubuntu with a swap area in a separate partition and it's normally not needed very often by modern computers with the amount of RAM we have nowadays.

If you hibernate your Ubuntu instead of shutting it down you may still need a large swap area. 
If you prefer to shut down instead you probably have a swap area that's not used very much and is wasting a significant amount of your disk space.
If your swap area is right after your /, you could reclaim valuable disk space by installing [Dynamic Swap Space Manager]("http://pqxx.org/development/swapspace/")        instead.
```
sudo apt-get install swapspace
```
Then you may boot a Live CD or USB and delete the swap area. (You'll need to click 'swapoff' first if you use GParted in a Ubuntu Live CD, or use a Parted Magic Live CD or USB as it doesn't mount your swap).
You'll also need to edit your /etc/fstab and comment out the line telling your OS to look for a swap area. (It might slow your computer down if you don't disable that line).

Expand your Ubuntu / to occupy the free space you just made by deleting the swap area. Dynamic Swap Space Manager will save you a lot of space without sacrificing performance by creating the required number of swap files dynamically on the flie, only as many as you need or just a little more. I like to use it especially in flash memory because I believe it will also help to randomize and wear of the flash memory. So we get three benefits, speed, space savings and wear levelling all at the same time. :)

---

### Post by dragonfly41 on 2012-02-08
Also .. install **bleachbit** to help in tidying up

---

