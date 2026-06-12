---
title: "I can't click on execute file as a program"
date: 2011-09-17
forum: General Help
---

### Post by Beinlaus on 2011-09-17
When I try to click on the square that says "Execute file as a program" it just clicks off automaticly for some reason. It looks like I have permission to "read and write" when I look on the top under the permission page. Please tell me how to execute a file as a program.

---

### Post by gandaran on 2011-09-17
> **Beinlaus said:**
> When I try to click on the square that says "Execute file as a program" it just clicks off automaticly for some reason. It looks like I have permission to "read and write" when I look on the top under the permission page. Please tell me how to execute a file as a program.
copy the file to your home user directory, it will work there.

---

### Post by mcduck on 2011-09-17
> **gandaran said:**
> copy the file to your home user directory, it will work there.

..or anywhere on any Linux filesystem. :)

Not being able to change permissions of a file that you own is most often result from the file being locate don a non-Linux filesystem, like FAT or NTFS, which lack support for file and directory permissions Linux and Unix systems use. (optical media filesystems are also read-only by design, so changing ownerships of files located on a CD, for example, is impossible)

---

### Post by Beinlaus on 2011-09-17
> **gandaran said:**
> copy the file to your home user directory, it will work there.
Thank you it worked.
But is it possible to do it on an external hard drive or any of the hard drives inside the PC? (I'm not very good with computers...)

---

### Post by Mark Phelps on 2011-09-17
> **Beinlaus said:**
> Thank you it worked.
But is it possible to do it on an external hard drive or any of the hard drives inside the PC? (I'm not very good with computers...)

Depends on the filesystems in use on the drives.  External drives that come preformatted nearly always have Windows filesystems -- and the answer there is NO -- since those filesystems don't have an "execute bit".

If you created the filesystems in use on your internal drive, and they are Linux filesystems, then the answer is Yes.

---

### Post by Morbius1 on 2011-09-17
This isn't the same problem you had back in October is it?
> **Beinlaus said:**
> Hey,

I'm having problems when i try to install windows games or other  programs using wine, it says something like the program/file isn't  executable. I'm a new Ubuntu user and i use Ubuntu 10.10.
Wine, the application itself, is incapable of determining if a given file has a Linux executable bit set. The problem is something called cautious-launcher and here are some ways around it: [http://ubuntuforums.org/showpost.php?p=10757436&postcount=2](http://ubuntuforums.org/showpost.php?p=10757436&postcount=2)

As for the other question about other drives and such and they are formatted in NTFS or Fat32 then yes they can be set to have files executable by mounting them with a mask that makes Linux think that they have Linux executable bit's set. That being said doing that on an internal nfts partition is simple, doing it on an external usb ntfs partition is another story.

---

### Post by PayPaul on 2011-09-18
> **Beinlaus said:**
> When I try to click on the square that says "Execute file as a program" it just clicks off automaticly for some reason. It looks like I have permission to "read and write" when I look on the top under the permission page. Please tell me how to execute a file as a program.
Go to Properties>Permissions and click on the check box for Execute "Allow executable file as program".

My problem lies with Winamp only finding the C drive not any other drives on my computer to use for the Media Libraries. The program installed fine with a right click to install with Wine. Very nice but the program is useless unless i can create the Media Library and use it to fix the metadata. Banshee and Rhythmbox don't allow that and don't access metafile online databases.

If I can't find a workaround for this I'm going to whine some more in here.

---

### Post by Beinlaus on 2011-09-18
> **Morbius1 said:**
> This isn't the same problem you had back in October is it?

Wine, the application itself, is incapable of determining if a given file has a Linux executable bit set. The problem is something called cautious-launcher and here are some ways around it: [http://ubuntuforums.org/showpost.php?p=10757436&postcount=2](http://ubuntuforums.org/showpost.php?p=10757436&postcount=2)

As for the other question about other drives and such and they are formatted in NTFS or Fat32 then yes they can be set to have files executable by mounting them with a mask that makes Linux think that they have Linux executable bit's set. That being said doing that on an internal nfts partition is simple, doing it on an external usb ntfs partition is another story.
How do I make linux think its an linux executable bit on the internal drives?

---

### Post by Morbius1 on 2011-09-18
[COLOR=Blue][1] This is important so I'll post it in bold:[/COLOR]
**If all of this is related to wine you don't have to make an exe file executable. Follow the instructions at the link I provided and it will solve your problem:** [http://ubuntuforums.org/showpost.php?p=10757436&postcount=2](http://ubuntuforums.org/showpost.php?p=10757436&postcount=2)

[COLOR=Blue][2] This is the wrong question:[/COLOR]
> How do I make linux think its an linux executable bit on the internal drives?     [COLOR=Blue]This is the right question:[/COLOR]
> How do I make linux think its an linux executable bit on the internal [COLOR=Blue]**ntfs**[/COLOR] drives ( by the way, this is Linux so please refer to them as partitions not drives)?     
This is an example of the procedure. Use your own data for your own system:
 
**First, If you have this partition mounted manually unmount it.**

* Run the following command to see how your system sees your partitions:
```
sudo blkid -c /dev/null
```You will get something like this for an ntfs partition:
> /dev/sdc1: LABEL="BACKUP" UUID="66E4DC83E4DC56C1" TYPE="ntfs" * Create a permanent home for your partition:
```
sudo mkdir /media/Data
```* Edit fstab as root:
```
gksu gedit /etc/fstab
```* Add the following line to the end of fstab:
```
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
```* Save fstab, exit gedit, and back in the terminal run the following command to test for errors and mount the new partition:
```
sudo mount -a
```

---

### Post by PayPaul on 2011-09-18
Isn't the question about running a windows program in Wine and the message that comes up telling the user that it (the windows .exe file) has to be an executable file? The hint given on how to do it has to do with permissions. I was able to do that and get the program to run in Wine. It was as I said, Winamp and I should post the question about how to get Wine to recognize other drives on my system. But the installation went without a hitch after I changed the permission to allow the Winamp installation program to be an executable file by checking the appropriate box in the Permissions tab.

I solved that problem by the method I described above. The commands list you give is actually helpful to me in letting me know the paths and parameters for locating my drives/partitions. It's interesting to know that Ubuntu won't work on drives that don't have a format it can recognize. Am I correct in saying that Linux/Ubuntu will only recognize ntfs formatted drives/partitions? If that's so than what is needed further to allow a Windows executable file on an ntfs formatted to open in Ubuntu without Wine?

Could you please explain the function or the action that takes place when one adds this code to the end of the fstab file?

UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
I see the UUID matches that of the partition that the OP has the program in but what do the entries** nls=utf8, uid=1000, umask=000 0 0 **do to allow this action to take place allowing the program to be seen as a linux program?

---

### Post by Morbius1 on 2011-09-18
> It's interesting to know that Ubuntu won't work on drives that don't  have a format it can recognize. Am I correct in saying that Linux/Ubuntu  will only recognize ntfs formatted drives/partitions?Not sure I followed that. Linux can recognize almost every file system. You don't want to install Linux on anything but a Linux filesystem but that doesn't mean it can't access any of them.
> If that's so than what is needed further to allow a Windows executable file on an ntfs formatted to open in Ubuntu without Wine?You can't run an exe file without Wine. It's an application that depends on an environment and libraries in order to tun. Those are not present on Linux without Wine.
> I see the UUID matches that of the partition that the OP has the program in but what do the entries** nls=utf8, uid=1000, umask=000 0 0 **do to allow this action to take place allowing the program to be seen as a linux program?     In reverse order:

It's does not make it look like a Linux program - it just sets all files to appear to Linux to be executable - that's 2 different things. 

umask=000
umask is a mask that removes permissions from the raw ntfs file or folder. Setting it to 000 allows every folder and file to have permissions of read, write, execute. Each number's location represents a different type of user. The first position represents the owner of the file, the second it's group, the third everyone else. A umask=000 removes nothing from the raw NTFS file which has rwx permissions by default.

uid=1000
The uid is the "User id" and it replaces the default owner of root to you.  It's not really necessary with a umask=000 since you have free access anyway but it's good to have in case you want to use Samba or send something to the Trash.

nls has to do with character encoding so names are recognized.

---

### Post by Wim Sturkenboom on 2011-09-18
> **PayPaul said:**
> 
My problem lies with Winamp only finding the C drive not any other drives on my computer to use for the Media Libraries. The program installed fine with a right click to install with Wine. Very nice but the program is useless unless i can create the Media Library and use it to fix the metadata. Banshee and Rhythmbox don't allow that and don't access metafile online databases.

If I can't find a workaround for this I'm going to whine some more in here.If I'm not mistaken, I installed a tag editor from the repositories. So it might not be necessary to use Wine.

Not behind my Ubuntu machine at the moment, so I can't say what it is called.

---

### Post by PayPaul on 2011-09-18
I have found that not all programs will allow me to click on the checkbox in the permissions tab. I click on it and the check mark doesn't stay there. That sucks. I'm a bit concerned about allowing every program to act as it were an executable. Seems a bit drastic to me. I'm wondering about that permissions tab. The choices for permissions to the file are quite simplistic. True that windoze is very complex with regards to permissions but Linux/ubuntu apparently can't come up with adequate permissions dialogs and if I'm not mistaken has all those kind of deeper controls only accessible via a command line.

Yes, I did find moving a file folder with a windows executable program to the home folder did the trick but the program itself, an AllCityGames freebie refused to run after install. I get the initial white screen I normally get and than it gives me colored noise and halts. Yuck!

Yet I did get another program working, an image editor called Dynamic Photo HDR. However I can only access it via the Wine folder down a few sub levels to where the program files (sic) are and then into the folder for the program installed with Wine. How come I can't even make a link on the desktop and make it work. Weird wine!!

---

### Post by Wim Sturkenboom on 2011-09-19
> **PayPaul said:**
> I have found that not all programs will allow me to click on the checkbox in the permissions tab. I click on it and the check mark doesn't stay there. That sucks. 
I think that that was explained in post #3 (amongst others). If it's not on a native Linux filesystem, you will experience the current behaviour (see also my next comment). In my opinion we're is lucky that there is some kind of support for proprietary file systems.

> **PayPaul said:**
> I'm a bit concerned about allowing every program to act as it were an executable. Seems a bit drastic to me.In that case, don't run it from a file system (or in an operating system) that does't allow the control that you want/need; you need to use the right tool for the job (the tool being a piece of software, an OS or a filesystem, that does not matter). If you're talking about external HDs, they are not intended for that use; they are intended to move files from one system to another or for backups.

> **PayPaul said:**
> I'm wondering about that permissions tab. The choices for permissions to the file are quite simplistic. True that windoze is very complex with regards to permissions but Linux/ubuntu apparently can't come up with adequate permissions dialogs and if I'm not mistaken has all those kind of deeper controls only accessible via a command line.
There might be one thing that you can't do using the gui and that is changing the owner/group of a file (I'm not sure, I've never cared to look at it; others can correct me here). Once you have taken that hurdle, you basically have the same control over who can run a program and who can't; so no deep digging into the command line.

> **PayPaul said:**
> Yes, I did find moving a file folder with a windows executable program to the home folder did the trick but the program itself, an AllCityGames freebie refused to run after install. I get the initial white screen I normally get and than it gives me colored noise and halts. Yuck!
Wine tries to be as good as possible but it's not pretending to be perfect (their homepage states that not every Windows program works yet). That's the fact of life. If you can't live with that, you're better off installing Windows (dual boot, virtual machine or as the only OS). It's anyway the opinion of a number of people that one should run programs in their native environment. If you want to improve it, participate in the project (you don't have to be a coder)

> **PayPaul said:**
> Yet I did get another program working, an image editor called Dynamic Photo HDR. However I can only access it via the Wine folder down a few sub levels to where the program files (sic) are and then into the folder for the program installed with Wine. How come I can't even make a link on the desktop and make it work. Weird wine!!
You should be able to have a shortcut on your desktop. Do some research on the web how to create shortcuts and read the [wine man page](http://pwet.fr/man/linux/commandes/wine).

---

### Post by mcduck on 2011-09-19
> **PayPaul said:**
> I have found that not all programs will allow me to click on the checkbox in the permissions tab. I click on it and the check mark doesn't stay there. That sucks. I'm a bit concerned about allowing every program to act as it were an executable. Seems a bit drastic to me. I'm wondering about that permissions tab. The choices for permissions to the file are quite simplistic. True that windoze is very complex with regards to permissions but Linux/ubuntu apparently can't come up with adequate permissions dialogs and if I'm not mistaken has all those kind of deeper controls only accessible via a command line.
Like I already said in my previous post, it's actually the exact opposite of what you are thinking. :)

Linux and Unix systems have more complicated and detailed permission system than what windows has, and as both FAT and NTFS filesystems are designed for Windows, they only support Windows permissions and lack the ability to handle the permissions Linux uses. So the problem definitely isn't Linux not being able to come up with adequate permission dialogs, it's the filesystem you use not being able to store the permissions. :)

> **PayPaul said:**
> 
Yet I did get another program working, an image editor called Dynamic Photo HDR. However I can only access it via the Wine folder down a few sub levels to where the program files (sic) are and then into the folder for the program installed with Wine. How come I can't even make a link on the desktop and make it work. Weird wine!!
I can only suggest that you try a native Linux application instead. For example [Luminance HDR]("http://qtpfsgui.sourceforge.net/") runs natively on Linux.

Anyway, it should also be mentioned that you don't actually need execute permissions to run a program with Wine. The thing here is that from the operating system's point-of-view, you are not executing the .exe file, you are opening it with Wine. just like you don't need an execute permissions to open an image with a image viewer or play an mp3 with a music player. The tricky part is that this doesn't work if you just double-click an .exe file, you'll need to have a launcher for the program, or right-click the .exe file and choose to open with Wine (or run "wine /path/to/program.exe" in a terminal).

Anyway, I can only recommend trying to find a native Linux application before even considering running Windows applications with Wine. It's no way perfect for running Windows apps, and it will never be. You'll have a much better experience and less problems using programs that are actually meant to be used on the operating system you are running.

edit: As you can see from [this table]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#Metadata"), FAT12, FAT16, FAT32 and ExFAT all lack support for POSIX file permissions. NTFS can kind of handle them using Access Control List, but needs an add-on (like Windows Services for Unix or Cygwin) to translate between ACL and POSIX permissions.

---

### Post by PayPaul on 2011-09-19
I do have to agree with you that I'd prefer a native linux application. I've never had good experience with emulators of any kind and I suspected that was the problem with the playcity games programs. I'm doing the research this morning about shortcuts. The right click I tried didn't work but there must be another method of doing otherwise it wouldn't be there.

---

