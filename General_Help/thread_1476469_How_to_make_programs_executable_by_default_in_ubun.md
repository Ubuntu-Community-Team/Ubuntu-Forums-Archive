---
title: "How to make programs executable by default in ubuntu 10.04?"
date: 2010-05-07
forum: General Help
---

### Post by user333 on 2010-05-07
I am going nuts about the new "not marked as executable" thing. How can I make programs (.exe, .sh, .desktop and all the others) run by default? This causes all sorts of problems for me, and they are a pain to fix. (such as running programs from cd, now it takes a whole minute instead of seconds)

Does anybody know how to fix this?

---

### Post by lmarmisa on 2010-05-07
I think that your problems are due to the loss of attributes of the files when they are stored in a non Linux file system (CD, ntfs, FAT32, etc). 

The +x executable attribute is well stored when the file system is ext2, ext3 or ext4 but it is lost when the same file is stored in a FAT32 file.

Maybe if you could give more details of your problem, it would be easier to help you. Why do you use CDs?. Are you using external USB HDDs (using a FAT or NTFS file system type) for storing programs?.

Some tools like **tar** allow to pack in a file one or more files or a complete directory preserving the UNIX attributes of their files. This is only an idea, but it would interesting to know more details about your problem.

Best regards,

Luis

---

### Post by cuberts on 2010-05-07
> **user333 said:**
> I am going nuts about the new "not marked as executable" thing. How can I make programs (.exe, .sh, .desktop and all the others) run by default? This causes all sorts of problems for me, and they are a pain to fix. (such as running programs from cd, now it takes a whole minute instead of seconds)

Does anybody know how to fix this?have you installed all of the neccesary drivers and have you installed all of your updates?

---

### Post by Ocxic on 2010-05-07
[lmarmisa]("http://ubuntuforums.org/member.php?u=955260") is correct, unless the +x (executable) attribute is already set, you will have to set it manually.

There is no way to allow programs, scripts, etc.. to run by default, as that would be a security risk, and is not allowed. (as far as I know)

Note: .exe files are Windows only and will not run on Ubuntu/Linux without the help of wine.

---

### Post by user333 on 2010-05-07
OK, just so you know, I can run the programs, I just have to always go into the preferences and give myself permission to use it. That is what is bugging me. I can run programs installed through synaptics or the ubuntu software  center really easy without doing this, just not pre-compiled programs I  download. The reason I use CDs is because I have a lot of windows programs that I run with wine(I really have to use them, and there are no substitutes). I don't have any external hard drives.

---

### Post by user333 on 2010-05-07
Ok, thanks for telling me Ocxic. I wish I could get it to _just run_ like in 9.10, without this hassle :( (And yes, I know all about wine ;) )

Maybe I will try fiddling with the permissions preferences...

---

### Post by lmarmisa on 2010-05-07
The compilers (like the C/C++ gcc compiler) add the +x attribute to the executable files. So you do not need to add manually this attribute to the executable files because the compiler is doing this task.

Script files (bash or shell scripts) are created using a text editor (vi, gedit, etc) and the programmer has to add manually the +x attribute once (only once) by means of a command similar to this:

> 
chmod +x script_file
That is all if your file system is ext2, ext3 or ext4.

A different thing occurs if you work with a non-native Linux file system like FAT or NTFS. In that case the +x attributes are lost and you will have to restore them manually.

---

### Post by mc4man on 2010-05-08
Most of what you're seeing is the result of this
[https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required](https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required)

.desktops are a 'global' deal - don't know how to change but not much of a issue anyway - usually it just prevents an icon from being displayed till marked as 'trusted' (exec. bit set.

Wine has several workarounds from using the [wine team ppa ]("https://launchpad.net/~ubuntu-wine/+archive/ppa")to custom launcher to editing the default launch command. ( .exe's on cd's have additional workarounds - 
 cli - wine /path/to/.exe or creating an fstab entry

For the most part java is best done by editing the default launch command.

This is wine's launch comm. now - you can see the cause here..
> 
Exec=[COLOR="Blue"]cautious-launcher[/COLOR] %f wine start /unix

So for custom launcher  just use wine as command
one time setup - (r.click - open with - use custom command, for command just
wine

To edit default
```
gksu gedit /usr/share/applications/wine.desktop
```
use this instead on Exec= line
```
Exec=wine start /unix %f
```

same idea on java - locate the .desktop ( most likely in /usr/share/app-install/desktop/

---

### Post by Struki on 2010-05-10
I'm having some similar problems, with premissions, hope I'm not off topic(much). I've used ext2fsd to mount my ext3 (/home) partition in XP. Now my desktop shortcuts are all marked as untrusted(*.desktop files) and I can't launch my apps from desktop. I've tried
```
sudo chmod ugo+rx *.desktop
``` and rechecking the "allow to execute..." under premissiona, but nothing happened. Any ideas?

---

### Post by kmsalex on 2010-05-31
in the futer i think it would be smarter for instead a of an error message, a message pops up asking if your sour you wan't to run it or not, like in vista and 7 with permission levels, and run as an administrate.

---

### Post by imnotjack on 2010-06-08
I'm suffering from something similar. I play a game called tribes 1. It barely worked in 9.04 and 9.10. I hesitated upgrading and when I did I tried my short cut with no response so I went to the exe itself and it said it wasn't an executable.... I tried telling it to run as an executable in the file's permissions and it said I could not edit any permissions b-cuz I wasn't the owner.... I'm furious with 10.04 cuz ALL my windows apps don't work due to the same reason. I terribly regret upgrading even though my video streaming is better and clearer its not worth the trouble I'm going through. I do use wine to open my windows programs and I still do have wine setup the same way and its very frustrating.....

---

