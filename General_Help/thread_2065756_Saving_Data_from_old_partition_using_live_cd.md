---
title: "Saving Data from old partition using live cd"
date: 2012-10-02
forum: General Help
---

### Post by OraStendar on 2012-10-02
Hello, I recently installed Windows 7 on my laptop which was previously just Ubuntu 11.10. However, to my dismay after using gparted to partition I found the Ubuntu partition was unbootable. Whenever I tried booting it it would go to a black screen and none of the recovery mode options would work. 

Putting on a live cd for 11.10 allowed me to view the partition with Linux on it titled 462 GB Filesystem.  And even though I can read and write files in there, is there any solution of recovering my files short of buying and external hard drive?

---

### Post by deadflowr on 2012-10-02
You can try boot-repair first.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

And see if repairing that  first helps.

---

### Post by daslinkard on 2012-10-02
Did the Boot-Repair work for you?

---

### Post by OraStendar on 2012-10-02
No, I already tried that and still get the black screen, but thanks for the suggestion.

---

### Post by Bashing-om on 2012-10-02
OraStendar; 
As your ubuntu partitions are good. Here are a couple of links with info to get grub re-installed; 1st link has to do with the balck screen: 

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)

Post back with your results.[INDENT]try'n to help <==BDQ

[/INDENT]

---

### Post by sidzen on 2012-10-02
If you simply want to recover files, I suggest burning Puppy to a CD, booting to it and then using it to burn files to a DVD with Pburn, perhaps;  or simply reinstalling, say, Xubuntu 12.04.1 where ubuntu 11.10 was (same partitions) and not formatting /home.

---

### Post by oldfred on 2012-10-02
Post link to BootInfo report, if Bashing-om suggestions do not work:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

