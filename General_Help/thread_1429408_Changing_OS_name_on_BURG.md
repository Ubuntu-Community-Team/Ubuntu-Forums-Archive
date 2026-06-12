---
title: "Changing OS name on BURG"
date: 2010-03-14
forum: General Help
---

### Post by S3loth on 2010-03-14
I'm trying to make my BURG boot loader look better, right now it has the Ubuntu and Windows icons, but for name it has things like "untu 2.6" because the name won't fit. I am trying to change them simply to "Ubuntu" and "Windows 7", but I'm having some trouble. Using [this guide]("http://ubuntuforums.org/showthread.php?t=1287602"), I am able to change the entries for GRUB2,but it has no effect on my BURG entries. Even if it was just removing the names all together, and just having the icons, that would be fine.

---

### Post by Alterios on 2010-05-03
If you go into /etc/burg.d (instead of /etc/grub.d) you can follow the same guide if you are in Lucid (10.04). I do not know if this will work in Karmic (9.10).

**A few notes**
(1) Instead of running "sudo update-grub", you need to run "sudo update-burg"

(2) You can run "sudo burg-emu -D" to preview your changes without rebooting. 

(3) Just type "c" to get the grub prompt in the preview window. Type "exit" at the grub prompt to exit the preview.

(4) Make sure you run "sudo update-burg" after each change before you preview it.

---

### Post by olasitha on 2011-09-21
It's true, that, if you are using BURG, the command to make changes to burg configuration is 'sudo update-burg'.

But, If you manually change the menu entry names, and then run the command 'sudo update-burg', your new changes will be lost, you will once again get the same old names for your operating system names.

Well, you can do the following, if you are desperate to change the names which appear on the menu at startup.

While in your linux version,

1) Boot into your Windows version and go to the Windows root directory. Let's assume it's C:.

2) Make sure your computer is showing all hidden files and folders together with all the system files. You can check this in Folder Options.

3) In your C: drive, you will find a hidden file called boot.ini. By default, it has the attributes of Read only, System, and Hidden. Remove the Readonly from it's properties, and open it

4) This is the file which contains the details of which partition has Windows installed and what should be displayed on the menu, if your computer is configured to dual boot with any other operating system.

5) under [operating systems], go to the line, which ends with 
            /fastdetect
    wording.

6) You will see a wording like "Microsoft Windows XP Professional" is there in that line.

7) Change that wording to whatever you like, but don't delete the double quotes for god sake.

8) Save the boot.ini. Restore the Readonly attribute to boot.ini and restart your pc and log in to your windows machine. Don't worry, if the new name you given to your Windows machine won't pop up in the boot menu, because we have not updated the burg menu to take the new settings.

9) sudo update-burg

10) Go into your /etc/default and open the burg.cfg in gedit or whatever you like.
    sudo gedit /etc/default/burg.cfg

11) navigate to the first line which starts as 
                     menuentry

11) As you can see each menuentry line is followed by double quotes. So what does that mean? That's the text which goes into your burg menu at start up.

12) Change them according, and make sure to change the contents which are written within double quotes only. Otherwise you are going to screw up everything, if you are new to burg menu errors.

13) Now save the file.

14) Now don't ever run the command 
      sudo update-burg

15) If you ever do, all the menuentries which shows the normal and recovery mode entries in the burg.cfg file, is going to revert back to system default entry values.

I guess that would sort out your problem.

Now I am not composing this in a Linux machine though..... so if you get an error or, you get an empty text file after opening burg.cfg, that means the file name is wrong.

In that case, try sudo gedit /etc/default/burg instead of burg.cfg

OK?

Correct me if any of my commands are incorrect as opposed to other users.

Thanks.

---

