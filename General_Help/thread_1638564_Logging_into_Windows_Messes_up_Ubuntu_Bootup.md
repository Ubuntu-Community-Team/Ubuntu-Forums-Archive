---
title: "Logging into Windows Messes up Ubuntu Bootup"
date: 2010-12-05
forum: General Help
---

### Post by TheDunn on 2010-12-05
Hello,

I installed Ubuntu through wubi on my laptop (which has Windows Vista) about 6 months ago. Up until a few days ago, it has worked fine.

A few days ago, the laptop ran out of battery in sleep mode while I was logged into windows. After that, whenever I chose Ubuntu on the Windows Boot-loader (only 2 options, Windows Vista and Ubuntu), the computer would just flash the message "Try 0 (hd, 0): NTFS:" (or something like that) and then restarts. After searching online, I found that I should run chkdsk /r or /f on the hard disk in windows and see if that fixes the problem.

Running chkdsk does allow me to boot into Ubuntu if I immediately boot into Ubuntu right after chkdsk runs (since chkdsk restarts the computer after it finishes), however, if I log into Windows, make a clean shutdown of Windows, and try to boot into Ubuntu again, I get the same problem I was getting before. Also, I have checked for a found.000 folder in Windows, and it doesn't show up, so I don't think that's the problem.

Therefore, it seems like each time I log into Windows, it's doing something to my Ubuntu partition that makes it so it can't boot. 

I would like to fix this problem without having to reinstall wubi or ubuntu since I have a fair amount of packages installed that I would have to deal with again. Also, it would be a major pain to have to run chkdsk before each time I want to switch to Ubuntu.

Any help anyone could give me with this problem would be greatly appreciated, 
Thank you, 
Matt

---

### Post by bcbc on 2010-12-05
> **TheDunn said:**
> Hello,

I installed Ubuntu through wubi on my laptop (which has Windows Vista) about 6 months ago. Up until a few days ago, it has worked fine.

A few days ago, the laptop ran out of battery in sleep mode while I was logged into windows. After that, whenever I chose Ubuntu on the Windows Boot-loader (only 2 options, Windows Vista and Ubuntu), the computer would just flash the message "Try 0 (hd, 0): NTFS:" (or something like that) and then restarts. After searching online, I found that I should run chkdsk /r or /f on the hard disk in windows and see if that fixes the problem.

Running chkdsk does allow me to boot into Ubuntu if I immediately boot into Ubuntu right after chkdsk runs (since chkdsk restarts the computer after it finishes), however, if I log into Windows, make a clean shutdown of Windows, and try to boot into Ubuntu again, I get the same problem I was getting before. Also, I have checked for a found.000 folder in Windows, and it doesn't show up, so I don't think that's the problem.

Therefore, it seems like each time I log into Windows, it's doing something to my Ubuntu partition that makes it so it can't boot. 

I would like to fix this problem without having to reinstall wubi or ubuntu since I have a fair amount of packages installed that I would have to deal with again. Also, it would be a major pain to have to run chkdsk before each time I want to switch to Ubuntu.

Any help anyone could give me with this problem would be greatly appreciated, 
Thank you, 
Matt

Chkdsk needs to restart to run. And doesn't restart once it's complete. Unless you're booting to a command prompt to run it, I suppose. Instead, go to My computer, right click on drive, Properties, Tools, Check disk for errors, Fix automatically. Reboot to complete, boot into windows so the check disk can run.

Ubuntu can't run if the ntfs volume isn't clean. So I am guessing it has something to do with that. I can't think of any other reason for intermittent boot up failures with Ubuntu - at least no reason why windows could be interfering in this way, if it wasn't simply an unclean ntfs volume.

The found.000 doesn't always show up when you run chkdsk but they are hidden. It doesn't sound like there's any problem with any of the ubuntu files, so no reason they should be moved or fixed.

---

### Post by fedu on 2010-12-06
I am having the exact same problem as you are, only the problem didn't start until the update manager ran a couple of days ago.

---

### Post by bcbc on 2010-12-06
> **fedu said:**
> I am having the exact same problem as you are, only the problem didn't start until the update manager ran a couple of days ago.

Your problem sounds more like the buggy grub update that's affecting 10.04 installs: [http://ubuntuforums.org/showpost.php?p=10183394&postcount=87](http://ubuntuforums.org/showpost.php?p=10183394&postcount=87)

---

### Post by dcstar on 2010-12-06
> **TheDunn said:**
> 
.........
Running chkdsk does allow me to boot into Ubuntu if I immediately boot into Ubuntu right after chkdsk runs (since chkdsk restarts the computer after it finishes), however, if I log into Windows, make a clean shutdown of Windows, and try to boot into Ubuntu again, I get the same problem I was getting before. Also, I have checked for a found.000 folder in Windows, and it doesn't show up, so I don't think that's the problem.

Therefore, it seems like each time I log into Windows, it's doing something to my Ubuntu partition that makes it so it can't boot. 
.........

Chances are your Windows Anti-virus "program" has decided that the Ubuntu system is not worthy of existance, and every time you boot Windows it decides to rewrite the nasty Ubuntu boot area so you don't harm yourself.....  :rolleyes:

---

### Post by wilee-nilee on 2010-12-06
> **dcstar said:**
> Chances are your Windows Anti-virus "program" has decided that the Ubuntu system is not worthy of existance, and every time you boot Windows it decides to rewrite the nasty Ubuntu boot area so you don't harm yourself.....  :rolleyes:

Lol that is funny and scary to.

---

### Post by dcstar on 2010-12-06
> **wilee-nilee said:**
> Lol that is funny and scary to.

I have seen it before, some Windows program checks the boot sector and sees that it is not the Windows boot loader that it expects, so it replaces it - sometimes without telling the user!

It is a "feature" of some Windows AV/Spyware programs.

---

### Post by bcbc on 2010-12-06
> **dcstar said:**
> I have seen it before, some Windows program checks the boot sector and sees that it is not the Windows boot loader that it expects, so it replaces it - sometimes without telling the user!

It is a "feature" of some Windows AV/Spyware programs.

Wubi doesn't use the bootsector or MBR. If you are referring to programs that overwrite parts of the MBR then that's a known issue with grub2 bootloader when used in the MBR.  [http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)

---

