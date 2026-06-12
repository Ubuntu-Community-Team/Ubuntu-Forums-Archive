---
title: "Installing Android App URemote Desktop Server help..."
date: 2011-01-19
forum: General Help
---

### Post by Dangerzone812 on 2011-01-19
Hi everyone, I recently found this app for my Android Phone that allows me to wirelessly control my computer through my phone, but it's asking me to download the server, and it has the terminal code on the page.

The code is as follows: 

1. Install dependency:
$ sudo apt-get install xautomation

2. Grant execution permition:
$ chmod +x launch.sh
$ chmod +x vd.sh

3. Launch the app:
$ ./launch.sh

I did step one with no problems, but when I typed in "chmod +x launch.sh" terminal outputted back:

"chmod: cannot access `launch.sh': No such file or directory"

Help? :\

---

### Post by xob on 2011-01-19
And is the file there, try ls -l

---

### Post by Dangerzone812 on 2011-01-19
I ran that, and the output was:

total 2592
drwxr-xr-x  3 andrew andrew    4096 2011-01-13 16:35 Azureus Downloads
drwxr-xr-x  3 andrew andrew    4096 2011-01-18 22:38 BioWare
drwxr-xr-x  4 andrew andrew    4096 2011-01-19 16:17 Desktop
drwxr-xr-x 11 andrew andrew    4096 2011-01-11 22:52 Documents
drwxr-xr-x  2 andrew andrew    4096 2011-01-19 17:40 Downloads
-rw-r--r--  1 andrew andrew     179 2010-12-07 21:33 examples.desktop
-rw-r--r--  1 andrew andrew   52766 2010-12-15 13:33 hs_err_pid3998.log
drwxr-xr-x  5 andrew andrew    4096 2010-12-25 23:09 lmms
drwxr-xr-x  5 andrew andrew    4096 2010-12-15 01:23 Music
drwxr-xr-x  3 andrew andrew    4096 2010-12-09 19:03 NetBeansProjects
drwxr-xr-x  3 andrew andrew    4096 2011-01-18 18:54 Pictures
drwxr-xr-x  2 andrew andrew    4096 2010-12-07 21:47 Public
drwxr-xr-x  2 andrew andrew    4096 2010-12-07 21:47 Templates
-rw-r--r--  1 andrew andrew   79472 2011-01-03 00:15 tumblr_lef20ys8Wx1qct2yqo1_400.jpg
drwxrwxr-x  2 andrew andrew    4096 2011-01-19 14:56 Ubuntu One
-rw-r--r--  1 andrew andrew 2240700 2011-01-07 01:56 ubuntupocketguide-v1-1.pdf
drwxr-xr-x  3 andrew andrew    4096 2010-12-15 09:08 Videos
drwxr-xr-x  4 andrew andrew    4096 2011-01-18 19:29 virtual-drives
drwxr-xr-x 13 andrew andrew    4096 2011-01-13 02:22 wine-git
-rw-r--r--  1 andrew andrew  202520 2011-01-12 13:12 winetricks.sh
drwxr-xr-x  3 andrew andrew    4096 2010-12-15 10:12 workspace

---

### Post by Dangerzone812 on 2011-01-19
I ran that, and the output was:

total 2592
drwxr-xr-x  3 andrew andrew    4096 2011-01-13 16:35 Azureus Downloads
drwxr-xr-x  3 andrew andrew    4096 2011-01-18 22:38 BioWare
drwxr-xr-x  4 andrew andrew    4096 2011-01-19 16:17 Desktop
drwxr-xr-x 11 andrew andrew    4096 2011-01-11 22:52 Documents
drwxr-xr-x  2 andrew andrew    4096 2011-01-19 17:40 Downloads
-rw-r--r--  1 andrew andrew     179 2010-12-07 21:33 examples.desktop
-rw-r--r--  1 andrew andrew   52766 2010-12-15 13:33 hs_err_pid3998.log
drwxr-xr-x  5 andrew andrew    4096 2010-12-25 23:09 lmms
drwxr-xr-x  5 andrew andrew    4096 2010-12-15 01:23 Music
drwxr-xr-x  3 andrew andrew    4096 2010-12-09 19:03 NetBeansProjects
drwxr-xr-x  3 andrew andrew    4096 2011-01-18 18:54 Pictures
drwxr-xr-x  2 andrew andrew    4096 2010-12-07 21:47 Public
drwxr-xr-x  2 andrew andrew    4096 2010-12-07 21:47 Templates
-rw-r--r--  1 andrew andrew   79472 2011-01-03 00:15 tumblr_lef20ys8Wx1qct2yqo1_400.jpg
drwxrwxr-x  2 andrew andrew    4096 2011-01-19 14:56 Ubuntu One
-rw-r--r--  1 andrew andrew 2240700 2011-01-07 01:56 ubuntupocketguide-v1-1.pdf
drwxr-xr-x  3 andrew andrew    4096 2010-12-15 09:08 Videos
drwxr-xr-x  4 andrew andrew    4096 2011-01-18 19:29 virtual-drives
drwxr-xr-x 13 andrew andrew    4096 2011-01-13 02:22 wine-git
-rw-r--r--  1 andrew andrew  202520 2011-01-12 13:12 winetricks.sh
drwxr-xr-x  3 andrew andrew    4096 2010-12-15 10:12 workspace

---

### Post by Dangerzone812 on 2011-01-19
Hello?!

---

### Post by piquat on 2011-01-20
Hi,
 
launch.sh is not in the directory listing you posted. The command is looking for launch.sh in the current working directory, IOW, the directory you're running the command in. It can't find it and according to your ls output, it's not there. The only other possibility is that it's **.**launch.sh, which seems odd to me but anything is possible. The . in front would hide it.
 
This:
 
```
 
ls -a

```
 
should, additionally, show you the hidden files in that directory. If it doesn't show it, it's not in that directory and you're going to have to find where it went.

---

### Post by RaYdOg on 2011-02-07
The problem is that you need to download the zip that is mentioned on that page just a few lines above those instructions. Then you unzip it, and then you run those commands from that directory. In my case, I downloaded the zip file to '~/Downloads/URemoteDesktop_Server_122310_2.zip'.

Then, in a terminal, I typed 'mkdir ~/RemoteControl' to make a 'RemoteControl' directory in my home. Then, to move into that directory, you would type 'cd ~/RemoteControl'. Then, to unzip the files into that new directory, you'd type 'unzip -j ~/Downloads/URemoteDesktop_Server_122310_2.zip'

From there, all the files are now in the directory that you are currently in, so you can now just follow the normal directions. So that means that you'd run: 'chmod a+x *.sh' to make all the .sh files executable. (IE: they can now have permission to act like programs.) Then, just run ./launch.sh, and you're good to go! Well, once you install the android app, but I'm sure you can figure that one out. ;)

Best of luck.

---

