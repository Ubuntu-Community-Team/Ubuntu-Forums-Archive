---
title: "Ubuntu Installation"
date: 2011-04-25
forum: General Help
---

### Post by nostromo3030 on 2011-04-25
Hello ALL! :)
I am new to Ubuntu :(
My problem: My system is a dual boot (XP Pro 32/W7 Ultimate 64)
I want to install Ubuntu 10.10 or 11.04 in its own partition.
Well, I have tried MANY times with no success because 10.10 or 11.04 cannot write the boot loader. After installation of 10.10 finishes I cannot boot AT ALL.
After installation of 11.04 finishes, I get the message that it was not possible to write on bootloader......
Any ideas? Am I doing something wrong?
Thank you in anticipation,
George

---

### Post by karthick87 on 2011-04-25
Can you post the results of bootscript?

---

### Post by nostromo3030 on 2011-04-25
No... unfortunately I cannot. I am so determined to install Ubuntu that I`ll go ALL the way formating disks and attempting to install ubuntu in a complete `fresh` situation....
I started installing ubuntu 10.10 INSIDE windows 7. It worked BEAUTIFULLY! I even managed to install a windows program with `wine`. So I desided to install Ubuntu on a more `permanent` installation. (Ubuntu having its own partition...) but it was impossible as I described......
and something else: On another compurer I clean install XP Pro and then attempted to install Ubuntu ALONGSIDE the windows......Result? Negative! ( I got this awful message about not writing the boot loader...)  
After all these... I tried to install ubuntu INSIDE W7 (which had worked) again....but this time there was a boot problem.  
George

---

### Post by Rubi1200 on 2011-04-25
You can do yourself a favor and help us help you by posting the specifications for the computer as well as the boot info script karthick87 asked you for.

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by nostromo3030 on 2011-04-26
Thank you for the instructions! I`ll try to follow them although I am not sure I can.....
The message I get at the end of the installation of 11.04 is:
`Executing `grub-install/dev/sda` failed
This is a fatal error

---

