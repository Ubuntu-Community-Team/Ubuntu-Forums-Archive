---
title: "Understanding RAM"
date: 2010-02-08
forum: General Help
---

### Post by onamattuphere on 2010-02-08
Please help me to understand how RAM works in the following scenario:

When I grep a huge text file (about 20MB), does the entire file get loaded into my 2GB of RAM? (I am running ubuntu in the terminal and have not loaded Xorg/GDM.)

In this scenario I am only working with this 20MB text file, with the odd exception of writing some other text file in NANO.
How do I make sure that the text file stays loaded in the RAM, so my disk will not spin up again in order to reload the file?

---

### Post by JackRock on 2010-02-08
Generally, as long as you have enough RAM to hold the entire file (you should, unless your computer's 20+ years old), the entire file will load into the RAM.

Computers/CPUs don't actually access the HDD directly.  They access RAM, which pulls from the HDD.

---

### Post by Cabs21 on 2010-02-08
RAM stands for Random Access Memory.  It can be read and written to very fast, but once the data is read it is typically forgotten or over written soon after.  Also if you have files on the RAM they are lost when power is turned off.  RAM is the only way your computer can go as fast as it does and can multitask.  Without it you would have to wait for your computer hard drive to find the data you want and read it while displaying it at the same time.  If the data was in two places on your hard drive you would be screwed.  Thus RAM is filled with the data you want so your computer can read the data quickly and linearly.  Check out [This Site]("http://en.wikipedia.org/wiki/Random-access_memory") for more info.

---

### Post by onamattuphere on 2010-02-10
Thanks for replies.
However I am trying to understand how RAM works in my specific situation.

Is there a command that would load a file onto the RAM and make it stay until I manually unload it?

---

### Post by john newbuntu on 2010-02-10
What you might want to do is to use the RAM as a ramdisk.  This is a filesystem that actually exists in RAM.  So any operation you do it is on the ram.  When all your operations are complete, you could save it to your local drive.  Caveat: If there is a powerloss or a system crash or RAM+Swap is not big enough for your file operations, you will lose your information.  Here is an outline of how to create a 1MB ramdisk:

sudo dd if=/dev/zero of=/dev/ram0 count=1440 bs=1024
sudo mke2fs /dev/ram0
sudo mkdir ~/mnt
sudo mount /dev/ram0 ~/mnt
sudo ls -al ~/mnt

//Now copy and manipulate files into ~/mnt.  /dev/ram0 becomes a disk for all practical
//purposes.  Finally,
umount ~/mnt

//Dump the filesystem to a file:
dd if=/dev/ram0 of=~/myramfile count=1440 bs=1024

Once you reboot, your ramdisk created this way is gone.  Also, this 1MB from your RAM can not be used by any other application.

Now, in your scenario, the entire 20MB may/maynot be sucked into the RAM depending on the implementation.  In a stream based operation,
only a certain amount of buffers may be used to fill the RAM. Just imagine how 20MB can get into the RAM when I have only 10 MB free(swap included)

---

### Post by onamattuphere on 2010-02-24
Thank you very much for helping me out. The fact that this can 
be done is simply amazing. Thanks to people like you, I am slowly 
learning more and realizing the tremendous powers that are available 
in Linux. However, I do have some follow ups:

When I restart my computer or umount it, the file I copied to the 
ramdisk still remains in the mounted directory (~/mnt). I thought it 
would be removed. Is this normal?
How can I make a loop where the 'if' command checks whether the ramdisk 
exists or not?
I followed your template exactly except for bs=20480, this gave me a 
ramdisk with 62MB. My goal was just 20MB although I might need 22MB to 
be on the safe side. I could always try other values until I got the 
desired effect, but that wouldn't give me a true understanding of how Linux works. Can you please explain why you get 1MB when bs=1024 and 62MB when bs=20480?

Also; I have plenty of free RAM, so I'm not worried about about that.

---

