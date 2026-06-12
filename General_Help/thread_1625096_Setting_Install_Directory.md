---
title: "Setting Install Directory"
date: 2010-11-18
forum: General Help
---

### Post by ZJE123 on 2010-11-18
When I install a Linux programs, such as wine, how would I set the install directory for that program.  It would be like setting it to install on the D drive instead of the C drive, in a way.  So far, I have used the Ubuntu software center.  I have not found out how so far;  whenever I install something, it installs somewhere I can't even find the files.  Any ideas how to do this?

PS: I am using Ubuntu 10.10

---

### Post by Verbeck on 2010-11-18
afaik, in linux there is no 'program files'

stuff gets separated to different directories depending on its use

all executables go in  /bin, /usr/bin or /usr/local/bin
 all documents in /usr/share/doc
 all icons in /usr/share/icons

and most importantly for the user, the configuration files for programs are in the user's home directory (/home/username). each program usually have a folder with its name preceded by a (.) and is hidden by default. to see them, press ctrl+H

however, wine creates a virtual C: drive in /home/username/.wine/drive_c . its where the windows applications you install would be

hope this helps

---

### Post by ZJE123 on 2010-11-18
> **Verbeck said:**
> afaik, in linux there is no 'program files'

stuff gets separated to different directories depending on its use

all executables go in  /bin, /usr/bin or /usr/local/bin
 all documents in /usr/share/doc
 all icons in /usr/share/icons

and most importantly for the user, the configuration files for programs are in the user's home directory (/home/username). each program usually have a folder with its name preceded by a (.) and is hidden by default. to see them, press ctrl+H

however, wine creates a virtual C: drive in /home/username/.wine/drive_c . its where the windows applications you install would be

hope this helps

So, is there any way to set the "virtual C: folder?"

---

### Post by WorMzy on 2010-11-18
Sure, simply move the contents of drive_c to your desired partition, remove the now empty drive_c folder, and create a symbolic link to the root folder of the fake C: partition in it's place.

e.g.
Move drive_c contents to /media/fakec ("mv /home/username/.wine/drive_c/* /media/fakec")
Remove drive_c folder ("rmdir /home/username/.wine/drive_c")
Create symlink ("ln -s /media/fakec /home/username/.wine/drive_c")


I haven't tested these commands, but the principle is sound. Note that if you intend to do this, use a ext# partition, and not a FAT/NTFS partition. Due to limitations with the drivers, using FAT/NTFS partitions will often cause applications to run slowly, particularly if they're large programs, like games.

---

### Post by Verbeck on 2010-11-18
> **ZJE123 said:**
> So, is there any way to set the "virtual C: folder?"
moving the folder itself might cause registry issues for the programs there

this user managed a way to change where the c:drive is safely. simply put, he moved the folder and created a link to another location
[http://ubuntuforums.org/showpost.php?p=7800441&postcount=5](http://ubuntuforums.org/showpost.php?p=7800441&postcount=5)
EDIT: its the same as what is posted above by WorMzy

to add a new drive to select while installing programs using wine, try  adding the folder path to 'Applications>wine>configure  wine''Drives' tab

---

### Post by ZJE123 on 2010-11-18
> **Verbeck said:**
> moving the folder itself might cause registry issues for the programs there

this user managed a way to change where the c:drive is safely. simply put, he moved the folder and created a link to another location
[http://ubuntuforums.org/showpost.php?p=7800441&postcount=5](http://ubuntuforums.org/showpost.php?p=7800441&postcount=5)
EDIT: its the same as what is posted above by WorMzy

to add a new drive to select while installing programs using wine, try  adding the folder path to 'Applications>wine>configure  wine''Drives' tab

Well, currently I have no programs installed there.  I am not very good with Linux so if you have already answered the following question, let me know: How do I create, or change a symlink?

---

### Post by ZJE123 on 2010-11-18
> **WorMzy said:**
> Sure, simply move the contents of drive_c to your desired partition, remove the now empty drive_c folder, and create a symbolic link to the root folder of the fake C: partition in it's place.

e.g.
Move drive_c contents to /media/fakec ("mv /home/username/.wine/drive_c/* /media/fakec")
Remove drive_c folder ("rmdir /home/username/.wine/drive_c")
Create symlink ("ln -s /media/fakec /home/username/.wine/drive_c")


I haven't tested these commands, but the principle is sound. Note that if you intend to do this, use a ext# partition, and not a FAT/NTFS partition. Due to limitations with the drivers, using FAT/NTFS partitions will often cause applications to run slowly, particularly if they're large programs, like games.

I am not very good with Linux so if you have already answered the following question, let me know: How do I create, or change a symlink?

---

### Post by WorMzy on 2010-11-18
The "ln -s" (link -symbolic) command above creates the symlink. Simply remove it and recreate it if you want to change it.

---

### Post by ZJE123 on 2010-11-18
> **WorMzy said:**
> The "ln -s" (link -symbolic) command above creates the symlink. Simply remove it and recreate it if you want to change it.

I have tried this on my external hard drive, which is what I wanted in the first place.  When I try to make a link, it says "The target doesn't support symbolic links."  Does this mean it's pretty much imposible?

---

### Post by WorMzy on 2010-11-18
You need to create the symlink in your home area, not on the external drive.

If that is what you were doing, then there's still another option available to you: "mount --bind". This will bind a folder onto another folder, creating a similar effect to a symlink.

```
sudo mount --bind /media/fakec /home/username/.wine/drive_c
```

You will need to recreate the drive_c folder before you run this command though, otherwise you'll get a "mount point does not exist" error.

If you're having a hard time getting your head around this, then post the command you tried, preferably along with the output of "mount", and hopefully someone will be able to point out what you're doing wrong (if anything), if not, I'll be back in the morning and I'll have a look myself. :)

*Note that mount --bind is only temporary, and you'll need to rebind it every time you boot up Ubuntu. You can make Ubuntu automatically bind the folder by adding a new line to to the /etc/fstab file. It should look like this: ```
/media/fakec/ /home/username/.wine/drive_c none bind 0 0
```

---

### Post by ZJE123 on 2010-11-18
> **WorMzy said:**
> You need to create the symlink in your home area, not on the external drive.

If that is what you were doing, then there's still another option available to you: "mount --bind". This will bind a folder onto another folder, creating a similar effect to a symlink.

```
sudo mount --bind /media/fakec /home/username/.wine/drive_c
```

You will need to recreate the drive_c folder before you run this command though, otherwise you'll get a "mount point does not exist" error.

If you're having a hard time getting your head around this, then post the command you tried, preferably along with the output of "mount", and hopefully someone will be able to point out what you're doing wrong (if anything), if not, I'll be back in the morning and I'll have a look myself. :)

*Note that mount --bind is only temporary, and you'll need to rebind it every time you boot up Ubuntu. You can make Ubuntu automatically bind the folder by adding a new line to to the /etc/fstab file. It should look like this: ```
/media/fakec/ /home/username/.wine/drive_c none bind 0 0
```

This is going to sound very stupid but: how do I input these codes?  When people talked about linking, I tried to do it by right-clicking, without codes.  Do I input them in a terminal, because I've tried with no such luck.  Sorry, I am still new to Linux.

---

### Post by WorMzy on 2010-11-19
The "ln" and "mount --bind" commands need to be written in a terminal, but the fstab line would need to be added to the fstab file. The reason I was giving you terminal commands is that they're shorter and easy to just copy-paste (and modify where necessary).

If the commands haven't worked for you, it's probably because you haven't modified them correctly. I don't know what address your "fakec" partition is mounted at, so you'll need to modify the codes slightly to make them correct for your system.

If you want to create a link through the GUI instead:
[LIST=1]
[*]Open two nautilus windows
[*]On the first window, navigate to your ~/.wine folder (press Ctrl+H to show hidden folders)
[*]On the second window, navigate to the parent folder where your "fakec" partition is mounted (e.g. /media)
[*]Middle-click and drag the fakec folder into your other nautilus window, when you release the middle button, you should be asked what action you wish to perform, choose "Link Here"
[*]Finally, rename the newly created link "drive_c", otherwise wine won't see it.
[/LIST]

---

