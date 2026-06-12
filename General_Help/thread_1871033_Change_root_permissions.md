---
title: "Change root permissions"
date: 2011-10-28
forum: General Help
---

### Post by xavi fernandez on 2011-10-28
Hi, I tried change the root permission from a folder that appears with a lock, the way I tried is in the terminal sudo su and put the password.
Please, is another way? I'm sure I'm getting wrong.
thanks in advance

---

### Post by t0p on 2011-10-28
Press key combination **Alt+F2** - a box will open.  Type in **gksudo nautilus /path/to/folder**.  Now you need to right-click on the folder you want to change; choose the **Properties** option, then the **Permissions** tab.  You can change the permissions however you like, as you are currently using the file manager (Nautilus) as root.

Once you've done whatever you want to do, close the window to close that iteration of Nautilus.  Generally it's best to use gksudo/sudo sparingly, as it is relatively easy to mess up something important when you're logged in as root.

---

### Post by WorMzy on 2011-10-28
If the folder has a lock on it, there's probably a good reason for it. Where is the folder, and what are you trying to do?

---

### Post by xavi fernandez on 2011-10-28
Thanks for your fast reply, I did what you said and after ask me for the psw appear an error like Could not find "/path/to/folder" I tried change the word folder for the name of the folder, but still.
This happen in two folders that I created because ask me do this for install my vpn in linux.
I'm sure I'm doing something wrong, but I'm really new in linux. I'm running ubuntu 11.04

Thanks in advance and for your time.

---

### Post by lazylew on 2011-10-28
> **xavi fernandez said:**
> Thanks for your fast reply, I did what you said and after ask me for the psw appear an error like Could not find "/path/to/folder" I tried change the word folder for the name of the folder, but still.
This happen in two folders that I created because ask me do this for install my vpn in linux.
I'm sure I'm doing something wrong, but I'm really new in linux. I'm running ubuntu 11.04

Thanks in advance and for your time.Do not substitute only the word folder, but the entire example.
If for instance the file is in something like
 /home/xavier/Music then use that instead of /path/to/folder

EDIT; and think about [WorMzy]("http://ubuntuforums.org/member.php?u=1062896")'s warning mentioned above! Be careful :-)

---

### Post by xavi fernandez on 2011-10-29
Well, I press alt+f2 and I wrote gksudo nautilus/home/xavi/keys
keys is the name from the folder I tried change the permissions and just appear the folder home without any folder just the icon from the desktop. after it I press alt+f2 and wrote

gksudo nautilus/home/owner/keys

and appear this time the folder home with all the folders including the folder keys with the lock, but not possible change the permissions cos belong to root. When in a terminal I write sudo su that I think is the command for work like a root, after password didn't allow me change the permissions. I need move the folder keys inside another one call vpn that I created already and is with the locker as well, for put some files from the vpn inside the folder keys and others just leave inside the vpn folder, but I can't.
In the panel next to the clock the name that appears is Owner and sorry for the mistake in my first post, I'm running ubuntu 11.10

thanks for your time and your patience.

---

### Post by lazylew on 2011-10-29
> **xavi fernandez said:**
> Well, I press alt+f2 and I wrote gksudo nautilus/home/xavi/keys

```
gksudo nautilus /home/xavi/keys

```is not the same as what you typed:
gksudo nautilus/home/xavi/keys

note the space that's missing!

---

### Post by xavi fernandez on 2011-10-29
lazylew, is working!!! thanks a lot!!! I really forgot the space like you said, and thanks all of you as well!!! I really appreciate it!!!

---

