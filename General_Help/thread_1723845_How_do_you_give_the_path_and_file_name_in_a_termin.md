---
title: "How do you give the path and file name in a terminal window?"
date: 2011-04-07
forum: General Help
---

### Post by manton1263 on 2011-04-07
p { margin-bottom: 0.08in; }  I don't know how to give the path and file name for the 'dd' command in a terminal window.

  
 I'm trying copy a file (smb.bin) on my cd file (in the install directory) to a floppy disk. 
  
 The command format is: 
  
 [COLOR=#ff0000]dd if=[/COLOR]in-file[COLOR=#ff0000] of=[/COLOR]out-file  
 

 in  dos it would be 
 dd if=D:/install/sbm.bin of=A:/sbm.bin  
 

 You can see I'm a nubee if I can't even give a path and file name in linux!! 



Any help would be appreciated! Thank you!

---

### Post by ~Plue on 2011-04-07
to find the path, open the directory with nautilus, press ctrl+L then copy the location from the location bar. or just drag and drop smb.bin from nautilus to the terminal window after 'if='

dd   if='/media/cd drive/smb.bin'  of=/media/floppy/smb.bin
(use quotes if the path has spaces)

-good luck

---

### Post by imhotep59 on 2011-04-07
The structure of a path is a little bit different of what you usually used in Windows.

/ refers to the root of your hard drive (it corresponds to C:\\). 
/home/user is your home (user should be replaced by the name you use to login). 
In the terminal you can use autocompletion with the tab: for example if you start to enter /ho and then hit tab the line will be automatically completed to /home. It also works with the commands.

---

### Post by WorMzy on 2011-04-07
There is no such thing as D:/ or A:/ on Linux, everything stems from "/". I recommend that you read through this to help you understand where everything is, and how you can navigate to it: [http://www.linuxconfig.org/Filesystem_Basics](http://www.linuxconfig.org/Filesystem_Basics)

Floppy disks and CDs are removable media, so look in there for their files.

Depending on whether you're trying to use this sbm.bin as an image or a file, there's two different ways of copying it to the floppy disk. You can use dd to copy the image, or cp to copy the file.

```
cp /media/[COLOR="Red"]cd-name[/COLOR]/install/sbm.bin /media/floppy
```

```
dd if=/media/[COLOR="Red"]cd-name[/COLOR]/install/sbm.bin of=/dev/floppy
```

In either instance, replace [COLOR="Red"]cd-name[/COLOR] with the correct path.

The difference between copying the file, and copying the image, is that if you copy the file, it will be just a file. If you copy the image, the whole floppy disk will be rewritten to contain whatever the file contains.

EDIT: You'll need to use sudo with the dd command, you may or may not need to use it with the cp command.

---

### Post by manton1263 on 2011-04-07
Thanks ~Plue and all!!
 I followed you instructions and created the file. I wrote everything down and am posting it with this reply for  any nubees to try what I did!!:
 &#8230;............................................
 use file browser (nautilus) to determine path. 
 Use CTRL+L (lower case L) and it will put the path in the location bar. 
 use that as the path and file name (if the any spaces than put it in double quotes). 
 I then used the teminal with this command: 
 sudo dd if=(inpathnfilename) of=(outpathnfilename) 
 and it will write to a floppy. 
 my example: 
 sudo dd if=&#8220;/media/Ubuntu 10.04.1 LTS i386/install/sbm.bin&#8221; of=/media/floppy/smb.bin 
  
 I checked and the copy worked 
 The file didn't boot on my laptop!!. maybe I need check the parameter settings for "dd".   will use dd --help

---

### Post by WorMzy on 2011-04-07
No, it didn't boot because you copied the file, not the image.

```
sudo dd if='/media/Ubuntu 10.04.1 LTS i386/install/sbm.bin' of=/dev/floppy
```

should work.

That said, I have no idea what this binary file is supposed to do. I don't even know if it's supposed to be bootable.

---

### Post by jerome1232 on 2011-04-07
I just wanted to note that you can actually drag the file into the terminal, and it's path will be pasted in.

so you can type "sudo dd if=" then drag file into your terminal and you'll get "sudo dd if=/home/me/path\ to\ that/really/cool/file"

---

### Post by WorMzy on 2011-04-07
> **jerome1232 said:**
> I just wanted to note that you can actually drag the file into the terminal, and it's path will be pasted in.

so you can type "sudo dd if=" then drag file into your terminal and you'll get "sudo dd if=/home/me/path\ to\ that/really/cool/file"

See post #2. ;)

---

### Post by jerome1232 on 2011-04-07
I guess that's what I get for quickly glancing at posts to get the jest of them.

:oops:

---

