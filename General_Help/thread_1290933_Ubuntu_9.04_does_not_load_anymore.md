---
title: "Ubuntu 9.04 does not load anymore"
date: 2009-10-14
forum: General Help
---

### Post by N3tMast3r on 2009-10-14
Hi Everyone,
  I was playing with my Ubuntu 9.04, as usual, when the OS suddenly froze. I restarted it by holding the power button and push it again and now it does not get into ubuntu anymore. I am stuck at the GRUB thingy.
  I have both ubuntu and Windows Xp installed on the same HD (two different partitions). When I select Windows xp I get no problems, but if I select ubuntu.... it does not load anymore. Any option I select does not work and if I type “boot” I get this error: “ubuntu error 8 kernel must be loaded before booting.” I really do not know what went wrong. I did not do anything in particular! I hope someone will be able to help me.
  Thank you.

---

### Post by bruno9779 on 2009-10-14
It may be your grub messed up, but the info is not conclusive....

Do you dual boot with Wubi? If so I am not too sure I can help (the boot process of wubi is different, i think)

anyway, [here]("http://ubuntuforums.org/showthread.php?t=224351") is a good tutorial on restoring grub.

If that does not work post back

---

### Post by arrange on 2009-10-14
Or - to give us more info - post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here.

([how to run the script]("http://sourceforge.net/docman/display_doc.php?docid=137292&group_id=250055"))

---

### Post by N3tMast3r on 2009-10-14
I thank you guys for the quick reply.
Unfortunately I am also unable to boot ubuntu through the live cd. If I insert the ubuntu cd (downloaded from the ubuntu official site) and restart my computer(setting the bios to boot first from the cdrom), the computer just asks which operating system I want to boot (ubuntu or xp). If i choose ubuntu the grab thingy opens up again. I really do not know how to do.

Furthermore, how am I supposed to post the output of boot_info_script? I am writing  to you guys using windows.

I thank you for your help.

---

### Post by arrange on 2009-10-14
> **N3tMast3r said:**
> I thank you guys for the quick reply.
Unfortunately I am also unable to boot ubuntu through the live cd. If I insert the ubuntu cd (downloaded from the ubuntu official site) and restart my computer(setting the bios to boot first from the cdrom), the computer just asks which operating system I want to boot (ubuntu or xp). If i choose ubuntu the grab thingy opens up again. I really do not know how to do.

Furthermore, how am I supposed to post the output of boot_info_script? I am writing  to you guys using windows.
If you see the Grub menu (ubuntu or XP) it means that you did not boot from LiveCD, but from your HDD again. Check your BIOS settings again, or burn another LiveCD (in case the first is somehow corrupted and cannot be booted from).

---

### Post by N3tMast3r on 2009-10-14
Ok thanks, I will download an other copy of ubuntu and I will burn it again.
I will keep you post it. In the meantime if somebody else knows how can I fix this problem without the ubuntu live cd... please let me know.
Thank you everyone.

---

### Post by N3tMast3r on 2009-10-14
Ok I boot ubutntu using the live cd. now i follow the guide to restore the grub, but when I enter "find /boot/grub/stage"  an error shows up "Error 15: File not found". =( Any help guys?

---

### Post by N3tMast3r on 2009-10-14
So I figured out that hte partition with ubuntu should be (hd0,1). Now when I type setup (hd0) i get this error: "Error 17: Cannot mount selected partition". The same error is given if I type kernel (hd0,1)/boot/
Do you guys have other suggestions?
Thank you

---

### Post by mungiki on 2009-10-14
Hi,

dont mean to interupt, but I had sort of a similar issue and the iso downloads were not working for me kept getting errors that the files are corrupt etc.  this is how i solved it see this [post]("http://ubuntuforums.org/showthread.php?t=1290651") probably not the ideal thing to do but it works perfect for me as unfortunately I rely very heavily on windows and i would rather have a slow ubuntu than no windows at all.  just my 2c worth....

---

### Post by N3tMast3r on 2009-10-14
I had ubuntu installed and working fine. That is not my problem. Now ubuntu does not load anymore. There is something wrong with the GRUB, but I do not know what. I tried to rescued it with the ubuntu live cd but nothing :( Now I am trying to save my personal data on the ubuntu partition (also some files that I had when I log in as root) but I cant figure out how to do it. =( Help me please

---

### Post by cwbar_1 on 2009-10-14
If it is a Grub problem, try this.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by ezsit on 2009-10-14
> Now I am trying to save my personal data on the ubuntu partition (also some files that I had when I log in as root) but I cant figure out how to do it. =( Help me please

Boot with the live CD and while running Ubuntu live, mount your partition with the files you want to save, mount a flash drive, and start copying what you want. Unmount the drives before removing the flash drive, and you are done.

---

### Post by N3tMast3r on 2009-10-14
It does not let me see the files. In the partition where I have ubuntu I can see a folder called "found.000" and inside of it there are othr folders.. there is also a boot folder. I can see a file named "root.disk" which is 8gb. My files should be inside that file since my partition only is 13gb or so. Ubuntu does not let me open that file =(

---

### Post by N3tMast3r on 2009-10-14
nope. Tried eerything but nothing. I think I am going to format =(

---

### Post by arrange on 2009-10-15
If you see a *root.disk* file it may mean that you had Ubuntu installed inside Windows (Wubi). Is that right? If so, you should have told us right from the beginning, because this makes it a very different matter.

---

### Post by N3tMast3r on 2009-10-15
Thanks guys, I just formatted and I installed everything again. It does not matter if I lost my data.
The only oprogram I could not installed because I was unable to find it since i do not remember its name, is a program that it is used for wardriving. It was a program similar to kismet but much better (in my opinion) and easier to use since it has a nice GUI. I remember I installed it from the terminal writing "get-apt...." Can anybody help me to find this program? I know, it is hard to understand what program  I am referring to, but if anybody has any idea... just say it ;p
Thank you

---

