---
title: "deleting wubi installed ubuntu"
date: 2011-08-08
forum: General Help
---

### Post by nichos on 2011-08-08
Below is my HD partitions with dualbooting Ubuntu & host XP via Wubi.

How can I change this setup, without distroying XP, & install ubuntu 11.04 on its own partition.

  Device Boot      Start         End      Blocks   Id       System

/dev/sda1 Logcl(*) 11gb/7.5    1        1437    11534336    12  Compaq diagnostics

/dev/sda2 (d)       4gb/8.1    1437     1959     4194304     c  W95 FAT32 (LBA)

/dev/sda3 (c)Acer  77.8/41.1  *          1959       12121    81627957    7  HPFS/NTFS

/dev/sda4 Extend   56.2/       12121    19458   58932225     5  Extended

/dev/sda5 (*)LinxExt3          12121    19198   56846336    83  Linux

/dev/sda6 (*)LinxSwap          19198    19458    2084864    82  Linux swap / Solaris

---

### Post by garvinrick4 on 2011-08-08
Just a guessing game unless we see a boot script as per below:

#Download this Script to DESKTOP:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
#Open a Terminal and use these four commands one at a time.
cd Desktop
unzip boot_info_script060.zip
chmod +x boot_info_script.sh
sudo ./boot_info_script.sh
#There will now be a file called RESULTS  on Desktop copy and paste to this Thread:
Use code tags and will be easier to read: (Highlight all text after pasting and click on # sign in upper right of message box)

1. You are changing directory's to Desktop
2. You are unzipping 
3. You are making script executable
4. You are executing the Script
5. Done Results on Desktop

##Most likely just have to uninstall Wubi and install Ubuntu in sda5 and swap in sda6 but always nice to look at boot script first.
## This is a thread to move from Wubi to partition if you can understand. If not, the uninstall and reinstall is the way to go.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by nichos on 2011-08-08
Below is my HD partitions with dualbooting Ubuntu & host XP via Wubi.

    How can I change this setup, without distroying XP, & install ubuntu 11.04 on its own partition.

    Device Boot Start End Blocks Id System

    /dev/sda1 Logcl(*) 11gb/7.5 1 1437 11534336 12 Compaq diagnostics

    /dev/sda2 (d) 4gb/8.1 1437 1959 4194304 c W95 FAT32 (LBA)

    /dev/sda3 (c)Acer 77.8/41.1 * 1959 12121 81627957 7 HPFS/NTFS

    /dev/sda4 Extend 56.2/ 12121 19458 58932225 5 Extended

    /dev/sda5 (*)LinxExt3 12121 19198 56846336 83 Linux

    /dev/sda6 (*)LinxSwap 19198 19458 2084864 82 Linux swap / Solaris

---

### Post by mikewhatever on 2011-08-08
It looks like you already have Ubuntu installed on /dev/sda5. Why do you want another installation?

---

### Post by garvinrick4 on 2011-08-08
See you started another thread sorry I confused you, will have to make it look simpler.

---

### Post by nichos on 2011-08-09
sorry Garvin, i do not know how I managed to put my queiry twice.

Thanx Mike, 
I read that the Wubi install entangles ubuntu with windows & if the need arises to Repair XP I loose the lot.

Did you read what garvin wrote above,and yet another post said :

"......You should be able to delete the Wubi folder in XP.
Then, defrag your XP installation.
Use a LiveCD such as GParted or Parted Magic to shrink your Windows partition.After that, install Ubuntu in the free space thaty you just created......." 

Contradictions make one confused.

---

