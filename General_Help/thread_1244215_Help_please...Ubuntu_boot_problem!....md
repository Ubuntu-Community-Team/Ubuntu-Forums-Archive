---
title: "Help please...Ubuntu boot problem!..."
date: 2009-08-19
forum: General Help
---

### Post by all_tair on 2009-08-19
First of all thanks to help me. I'm new linux user. Yesterday i format all of my laptop and install XP than Ubuntu and today i installed Fedora 10 when i installed fedora i had boot problem with ubuntu and VistaRecovery(My computer(Asus F3SG240DV) has a original Vista Recovery). When i choose VistaRecovery first it start and then gives ERROR i dont understand anything because only i see whith huge fonts error. And when i choose the ubuntu it didnt work. Then i choose XP it works correctly but than i restarted the computer and i didnt see the boot options i only see black screen it writes "grup>" i typed help but i didnt understand anything. So i couldnt open computer. Than i format all the computer with the XP and install xp then i install ubuntu. This time i didnt install Fedora. XP working correctly and Ubuntu working correctly but i cant access VistaRecovery. And The recovery partition was hidden but now not hidden i can see. And at the first time Recovery partition title was F, and XP C, Ubuntu D but now Recovery is C, Xp is D and ubuntu E how can i fixed this situation??? And how can i access VistaRecovery again???(Because vista recovery has a original copy i dont want to lose it...) :confused::confused::confused:

---

### Post by all_tair on 2009-08-20
While i research ubuntuforums i see this and i think it may be help other new ubuntu users to...

For the most common GRUB error, what you need to know here is that at the very start of every HDD is a small piece of data called the "Master Boot Record" (MBR). It holds the information about all the partitions, their size, location etc.. For GRUB to work it needs to two things 1.to be written to the MBR 2. know where the file "menu.lst" is located on the HDD. menu.lst holds all the data that GRUB needs and is located on the same partition as Linux, this is because the MBR has a small, unchangeable size. Unfortunately, the GRUB data is static i.e. it doesn't get updated with the rest of the MBR data when you move, resize or otherwise change any partitions.

(in this example, partition three is the Linux partition, you can check what partition yours in on by installing the "gparted" program, or burn the gparted liveCD from here: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php))
So say I have 3 partitions, numbered as 0, 1 and 2 (GRUB starts counting from zero). I then install Ubuntu to partition 2 (the third one). All works fine. Now say I decide to delete partition 1 (the second partition) to make more room for Linux, well, all of the partition data is updated in the MBR, but the GRUB data is static and only a purpose-built program will know what to do to change it. Buy deleting the middle patition, partition 2 technically becomes partition 1. As the GRUB data is static it still states that "menu.lst" is on partition 2, but now there is no partition 2! All GRUB can do in this situation is give you an error message, and you can't start any OS that is on the HDD.

One option is to undo the partition change/rearrangement buy recreation the middle partition in the same position. It doesn't have to be the same size, just as long as Linux becomes the third partition again.

If we really want to only have two partitions though we actually have to update the MBR GRUB data to state that menu.lst file is now located on the second of two partitions. If you installed Ubuntu you probably know how to boot Ubuntu from the liveCD, if not see here:[https://help.ubuntu.com/community/Bo...9%7C%28boot%29]("https://help.ubuntu.com/community/BootFromCD?highlight=%28from%29%7C%28boot%29"). Now that Ubuntu is loaded we can run the GRUB program from a the command-line to update it on the MBR.

1. start Terminal (Applications>Accessories>Terminal)
2. type "sudo grub" (ignore all quotation marks)
3. type "find /boot/grub/stage1". The output should look similar to this: hd0,5
4. type "root (hd?,?)". The contents of the brackets should correspond to the previous output (the brackets must be typed as well).
5. type "setup (hd0)"
6. type "quit"
7. restart

The GRUB menu should now be recovered. I've done this many many times, but I don't know it by heart, so if you get an error in the command-line then try google to resolve the error.

Well I hope this guide has fixed your problem and taught you a little about the workings of the MBR. If it has then you might like to spend a few minutes to point other people with this problem to this guide (it's a very common beginners problem). Just do a search of the latest forum threads with the keywords "GRUB" and/or "boot.

HOPE YOU CAN ENJOY UBUNTU TOO!  ([BrownCoal]("http://ubuntuforums.org/member.php?u=392722"))

---

### Post by beacon on 2009-08-20
If I can add my problem to this thread, I have followed the steps above, but when I use the wording of the third step I get the message: error 27, unrecognised command, and can go no farther.

---

