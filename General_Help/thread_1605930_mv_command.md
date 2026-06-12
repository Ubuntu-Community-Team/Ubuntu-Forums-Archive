---
title: "mv command"
date: 2010-10-25
forum: General Help
---

### Post by tommadden on 2010-10-25
I used this terminal command to move the folder "class": 
sudo mv ~/class/ /usr/local/bin 
and found that after the move when I use "ls" the only thing that appears is "class" - everything else has disappeared - I don't see what went wrong - help would be appreciated - any way to get the files back? thanks..

---

### Post by Brandon Williams on 2010-10-27
That use of move should have shifted the ~/class/ directory into the /usr/local/bin/ directory without touching any of the contents. If /usr/local/bin/ is on a different partition than /home/, then mv would have to copy the data over for all files in the class directory, but if that part of the operation failed, you would know (and the original ~/class/ directory would still exist).

Are you absolutely certain that the files are gone? What is the output of 'ls ~/class/* /usr/local/bin/class/*'?

---

### Post by sikander3786 on 2010-10-27
**mv** should cause any problems like data loss.

Are you sure that the contents of /class are not set to hidden? You can toggle by Ctrl + H.

---

### Post by steevven1 on 2010-10-27
It should be noted that "sudo mv class" moves "/root/class" somewhere. By using sudo, you are becoming root, and "~" refers to root's home directory, which is /root.

---

### Post by sikander3786 on 2010-10-27
> **steevven1 said:**
> It should be noted that "sudo mv class" moves "/root/class" somewhere. By using sudo, you are becoming root, and "~" refers to root's home directory, which is /root.
Good point. But that will not move the files to some other location than /usr/local/bin. Instead it will change the permissions and now the user needs to chown them back to gain access.

To the OP: Try to start nautilus with root priviledges, navigate to /usr/local/bin and see if you find your files there.

```
gksudo nautilus
```

---

### Post by sisco311 on 2010-10-27
> **steevven1 said:**
> It should be noted that "sudo mv class" moves "/root/class" somewhere. By using sudo, you are becoming root, and "~" refers to root's home directory, which is /root.

Nope, the tilde (~) is interpreted by the shell (most likely bash) and it's replaced with the value of HOME before the sudo command is executed. See:
```
man bash | less +/"Tilde Expansion"
```

---

### Post by tommadden on 2010-10-29
Brandon et al, thanks for the replies, I was trying to move class into the bin directory - class is a folder with an app on the inside (php files) -- the output shows it being there along with its files but nothing else. I'm doing this via ssh and terminal commands against the ubuntu server and no gui display available and the server is not partition.  I used 'ls -a' and it shows '.'  '..' 'class' - so the files might be there but are now hidden - -  I found another post that states "All your hidden files/folders have a period "." in front of them. If you open your home folder in nautilus and press Ctrl + H, you will see the hidden folders.
To **[COLOR=#ff0000]unhide[/COLOR]**, rename the folder to remove the period, or simply use ctrl h when you want to see them.
Nice,  but I'm doing this through a terminal and cannot find out to see the '.' files

---

### Post by WorMzy on 2010-10-29
Have you put anything else into /usr/local/bin? That folder is empty by default.

---

### Post by limestone on 2010-10-29
.

---

### Post by tommadden on 2010-10-29
I didn't put anything else in bin - but I checked it before i moved the class folder and it showed a large list of files, I didn't clip the list but I remember seeing 'bash' and others.. this is a new server install - it looks like my two choices are to wait and see if i run into problems further down the road - or do a reinstall just to be safe..

---

### Post by WorMzy on 2010-10-29
bash is in /bin.

Most applications install their executables to /usr/bin or /usr/sbin. /usr/local/bin is the recommended place for you to put your own system-wide executables, as you're not likely to override anything important.

Open a terminal and run
```
ls /bin
```
```
ls /usr/bin
```
Is either of those what you saw before?

---

### Post by tommadden on 2010-10-29
i did the ls /bin and now see what i saw before - i don't understand (newbi if you can't tell) - when i cd /usr/local/bin and get to the bin directory and then do 'ls' i don't see anything but the folder i moved - at root or in bin when i do 'ls /bin' i see what i saw before and when i do ls /usr/bin i see even more (i assume it's showing what's it both directories - what is the ls /bin doing that the ls when I'm in bin not doing??

---

### Post by tommadden on 2010-10-29
Thanks problem solved - you English folks got it going on!  appreciate the time. Have a good one..

---

### Post by WorMzy on 2010-10-29
Do you understand what you were seeing? running "ls bin" is different to running "ls [COLOR="Red"]**/**[/COLOR]bin". If you write a path starting with a "/" it treats the path as an absolute path, and when you type a path without a "/" it treats it as a relative path.

So running "ls bin" while you're in the /usr/local folder will add the "bin" to the end of the current path, making "/usr/local/bin", but "ls [COLOR="Red"]**/**[/COLOR]bin" will look in the /bin folder.

Maybe it'd be more obvious if I used windows notation:

"ls [COLOR="Red"]**/**[/COLOR]bin" from anywhere would show the equivalent of C:\bin, whereas running "ls bin" inside the /usr/local folder would show the equivalent of C:\usr\local\bin.

---

