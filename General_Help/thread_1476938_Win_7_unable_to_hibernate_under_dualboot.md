---
title: "Win 7 unable to hibernate under dualboot"
date: 2010-05-08
forum: General Help
---

### Post by hknajjar on 2010-05-08
I have recently installed OpenSuse with GRUB boot-loader on my Vaio FW series laptop. I had to uninstall it because it caused Windows 7 to be unable to hibernate. I installed other distros (Fedora 11 and others) and the same problem recurred. This lead me to the conclusion that the problem is with the boot-loader (as my research suggested)..It has been months now, and I have not found any proper solutions to this yet. Linking this to Ubuntu, I recently downloaded and burned Ubuntu 10.04 LTS, however, I am still reluctant to install it until I know a solution is available. Has anyone had Linux-Windows 7 dualboot and also faced problems with hibernation/stand-by?

---

### Post by Hack.The.Pow. on 2010-09-26
I recently just installed ubuntu 10.04 and my windows partition has just stopped being able to hibernate.  I had it set up before on my last lap top being able to hibernate though....So I'm not sure what changed.

Anybody got any help?

---

### Post by jasker on 2010-11-29
The problem is because of the way the Windows bootloader (BCD) works with hibernation; it looks for the active partition to write the hibernation data to. If your windows partition is not marked as active, it will fail.

If this is the problem, some symptoms are: after choosing hibernate, goes to a black screen then dumps you to the windows logon screen; or, after doing 'shutdown -h' from a command prompt, responds with 'The specified file could not be found.(2)'

The way to fix it is by modifying your Grub entries. Assuming you are using Grub2, which is the Ubuntu default (I think), you need to edit one of your options in your **/etc/grub.d** folder.

First, find out what partition your Windows installation resides on. This corresponds to the /dev/sda**#** for your Windows install (in my case, /dev/sda**2**)

If you are not using the Grub OS Prober, edit your **/etc/grub.d/40_custom** file, and add the line
**parttool hd0,2 boot+**
(remember the **2** here should match your /dev/sda**#** partition that Windows is on) just after the line containing **set root=...**

If you are using the Grub OS Prober, it is a little more complicated. Open the **/etc/grub.d/30_os-prober** file, and look for the part that looks like this:
```


      case ${LONGNAME} in
        Windows\ Vista*|Windows\ 7*)
        ;;
        *)
          cat << EOF
        drivemap -s (hd0) \${root}
EOF
        ;;
      esac

      cat <<EOF
        chainloader +1

```

You want to add the line:
**parttool hd0,2 boot+**
(again, the **2** here should match your /dev/sda**#** partition that Windows is on, mine is /dev/sda**2**) right after the **drivemap...** line and before the **EOF** line.

Save your file, and then run **sudo update-grub**, then reboot into Windows, and hibernation should work properly.

(Side note: There is probably a better way to change the 30_os-prober file, extracting the /dev/sda# from ${DEVICE}, but I don't know how to specifically do it, if anyone wants to make a suggestion, please do!

Side side note: Perhaps this 30_os-prober change should be submitted as a patch to Grub2??)

---

### Post by -magi- on 2010-12-30
If I want to solve the same issue on grub version 0.97 what are the correct steps then? Which files should I change and where I chanded only the /boot/grub/menu.lst so that win 7 is predefined to booting, but nothing was changed.

---

