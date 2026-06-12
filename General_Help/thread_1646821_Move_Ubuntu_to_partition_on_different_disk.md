---
title: "Move Ubuntu to partition on different disk"
date: 2010-12-16
forum: General Help
---

### Post by TTGRULES on 2010-12-16
Ok, so about 6 months ago, I decided to try running ubuntu as a server for my website. I was so impressed, that I kept the test-computer i had cobbled together as my main computer instead. It currently boots off an old 40GB IDE hard drive. I have upgraded everything else in the computer, and the drive has suddenly started making noise. I have several other drives in there that are fine, but ive got them all allocated to different things. I have 140GB of extra space on one which I can partition as I like. How can I migrate my ubuntu install to that partition??? It would take me weeks to reinstall everything... Thanks!!!

---

### Post by MrFaler on 2010-12-16
You can go with dd, just be careful with it, as it can easily wipe your drive clean if you do one thing wrong. In the following guidelines I will assume that you can only have 1 disk attached to the machine and that you will put the image.img on usb to later apply it.

Unmount the partition you want to copy. Then type:

```
dd if=/dev/hda1 of=/image.img
```

Where /dev/hda1 should be substituted with the partition you want to copy. And where /image.img should be substituted with the location you want your image to be. Now put the image.img on your USB stick.

Swap the drives and boot into a livecd. Now plug in your USB again and copy the .img to your ./ (working directory). Create the partition you would like to image Ubuntu on, write down which one it is (ie. /dev/sda0, /dev/sda1 etc.). Now lets go to the final steps.

```
dd if=/path/to/image.img of=/dev/sda(n)
```

Where /path/to/image.img is the location of your image and where /dev/sda(n) should be substituted with the partition you just wrote down.

After updating your bootloader you should now have a fully working OS. Remember that dd is a very powerful tool and you can whipe your drive with just one typo, always double check your syntax!

Good luck :-)

---

### Post by tredegar on 2010-12-16
Another way to do it:

Format the spare partition as **ext4** or **ext4**
Boot from a live cd (you do not want to copy a running installation).

Mount your old linux partition somewhere as **oldroot**
Mount your new, empty partition somewhere else as **newroot**
copy the files over, preserving permissions etc
```
cp -a /mnt/oldroot/* /mnt/newroot/
```
Now you will have to fix up **/mnt/newroot/etc/fstab** because the entry for / will be wrong (wrong UUID or wrong **/dev/sdxy**).
It is a good idea to **touch /mnt/newroot/NEWROOT** so when you next boot you can easily check which partition you have booted into.

Shutdown, remove the CD and reboot to your OLD installation (which is where grub lives).

Make sure you will be able to see the grub screen at boot (it'll be easier)
```
sudo update-grub
```

Cross your fingers, and reboot. You might, at first, find you have booted to your old partition, in which case reboot and try the other (same) kernel number in the list. You should then be running from your new partition.

Now, all you have to decide is which disk's MBR (probably the one your new partition is on) you'd like to install grub to. See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) for how to do this.

Once you have done this you can remove and, later, safely dispose of your old HDD.

If you have problems, come back here or search on **move root to new disk**

---

### Post by TTGRULES on 2010-12-18
Thanks Guys!!!! It worked great! My main filesystem now has more room and makes less noise! I used dd to copy it over, and then edited /etc/fstab... Its better to remove the main disk first, then boot with a live cd, because It would revert back to the old disk no matter what I chose at first... Thanks!!!!!!!!

---

