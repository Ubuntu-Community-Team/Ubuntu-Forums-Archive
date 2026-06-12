---
title: "After Reinstalling windows how 2 boot ubuntu i.e installed via Wubi perviously on win"
date: 2010-03-17
forum: General Help
---

### Post by piyushchandrakar on 2010-03-17
After Reinstalling windows how 2 boot ubuntu i.e installed via Wubi perviously on win
I love UBUNTU....i dont wanna lose it...

After Reinstalling windows how 2 boot ubuntu i.e installed via Wubi perviously on windows 7.

I am running Ubuntu 9.10 on my Laptop, where it installed via Wubi on Windows 7.

[windows 7 (Cand ubuntu on the different drive(U(NTFS)*its not a dual boot as installed via wubi].

For some reason My Windows needs a reinstall but in this case i think i will also lost ubuntu because its installed via Wubi.

Part 1 -
****I need to back up all the data that is installed in ubuntu i.e. SMplayer,Graphical GTK theme,Compiz,Emerald. and its setting,means the whole ubuntu system. So that after installing windows and ubuntu as a dual boot (not wubi again)i do not need to configure and install the whole ubuntu data/software again. Its pain for me to downlad again and again the data for ubuntu [Coz low speed connection ]

Part 2 -
****if it is possible that after Reinstalling windows i can boot into ubuntu that is previously installed via Wubi on different drive that please tell me, how could i do that.
****if it is not possible than please show me the way to do backup all the data,software,plugin that is downloaded.etc.

I need to back up the whole Ubuntu because after installing windows i am goin 2 format the ubuntu drive and make it to Ext4 that is currently NTFS and then i will install the Fresh 9.10 on that.

---

### Post by oldfred on 2010-03-17
All your settings are in your /home usually as hidden files and folders. All the files and folders that start with . are your settings. That is why it is most important to regularly backup /home.

Most of the debs you have downloaded are in this location unless you have housecleaned.
/var/cache/apt/archives

You can from synaptic or command line create a list of installed apps but you still have to redownload them.
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Info on mounting wubi:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

You can directly boot your wubi install, adjust this entry to your drive and partitions in 40_custom in your new install:

wubi direct boot
menuentry "Wubi" {
    insmod ntfs
    set root=(hd0,2)
        loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /initrd.img
}

---

