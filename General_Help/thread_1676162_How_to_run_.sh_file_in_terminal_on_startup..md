---
title: "How to run .sh file in terminal on startup."
date: 2011-01-26
forum: General Help
---

### Post by Stefan_McFeeters on 2011-01-26
I am currently using Ubuntu 10.10 and I desperately need to know how to run an executable file (.sh file) in a terminal when Ubuntu boots up. So far I have tried adding the file to the startup applications and a also tried running the file through rc.local (I didn't really know what I was doing here) but none of these worked. Can anyone help me with this predicament

---

### Post by Krytarik on 2011-01-27
Should work in /etc/rc.local if the script requires root rights.

Otherways you could try it again in "Startup Applications":
- create the entry
- open the text editor
- browse to the directory ~/.config/autostart
- open the respective *.desktop file
- change the value for "Terminal" to "true"; if that entry doesn't exit, add it:
```
Terminal=true
```

If both don't work, please post more info about what the script does and if it requires root rights.

---

### Post by Stefan_McFeeters on 2011-01-30
I don't seem to be able to access the file in the autostary directory. I cd to the location then I use ls to list the files in the autostart directory and the file is there (it's called File System Backup.sh.desktop. I try and open the file using sudo gedit but it only opens a blank text document. I do not know what I am doing wrong.

---

### Post by Krytarik on 2011-01-30
First of all, don't *ever* use "sudo" to launch graphical apps, use "gksudo" instead!
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

And, since you're editing the Startup Applications of the user, you don't need to do it as root at all.

To your original question, since there are spaces in the file name, your command has to be like this:
```
gedit "File System Backup.sh.desktop"
```
You could instead just open the text editor, and open the file from there, like I described.

---

### Post by Stefan_McFeeters on 2011-01-31
I changed the terminal access thing to true after having to add the terminal access thing. I then shutdown my computer and turned it back on. The terminal did not open with my script.

---

### Post by Stefan_McFeeters on 2011-01-31
I just tried rc.local in the etc directory. I just pasted my script in between the blue text and the exit 0, but after a reboot it didn't work. *sigh*

---

### Post by Krytarik on 2011-01-31
That way also doesn't work for me, annoyingly. That would be just too easy, right?! ;)

I found a way that works:

- set "Terminal" to "false" (default)
- set the command like this:
```
gnome-terminal -x sh -c "*terminal_command*"
```:popcorn:

---

### Post by Stefan_McFeeters on 2011-01-31
> **Krytarik said:**
> That way also doesn't work for me, annoyingly. That would just too easy, right?! ;)

I found a way that works:

- set "Terminal" to "false" (default)
- set the command like this:
```
gnome-terminal -x sh -c "*terminal_command*"
```:popcorn:
What do you mean by set command like this, where am I setting the xommand

---

### Post by Krytarik on 2011-01-31
> **Stefan_McFeeters said:**
> What do you mean by set command like this, where am I setting the xommand
Either in the "Add Startup Program" dialog, in the field "Command"

or in the .desktop file, behind "Exec=".

---

### Post by Krytarik on 2011-01-31
> **Stefan_McFeeters said:**
> I just tried rc.local in the etc directory. I just pasted my script in between the blue text and the exit 0, but after a reboot it didn't work. *sigh*
If you put it that way, you have to take into account that the command will be run as root, thus you may have to change the paths.

---

### Post by Stefan_McFeeters on 2011-01-31
Thank you so much, the terminal booted and started running the script - sort of - it just so happens to be that my script has two lines, here they are:

Cd '/media/Backup/Backup_Folder/File_System/February'

Sudo tar -cvpzf Tuesday_1st.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev / 

When the terminal opens the first line reads something about being unable to cd to the location I have listed. The script then continues to run my backup, but to my home directory instead. This script works fine when I run it manually, I believe my problem is something to do with having two lines.
Fan you help me here

---

### Post by Krytarik on 2011-01-31
Does it really read like this?:
> **Stefan_McFeeters said:**
> 
**Cd** '/media/Backup/Backup_Folder/File_System/February'

With capital "C"? That wouldn't work, only with lower "c".

---

### Post by Krytarik on 2011-01-31
Nevermind about the capital thing, since you also posted "Sudo" with cap "S", and mentioned that the "cd" command actually gives output, I assume you have the commands with lower first letter in the script.

Please post the output of the "cd" command when run through the launcher.

---

### Post by HandeH on 2011-02-03
I have succeeded to run scripts and start applications by [gnome-schedule]("apt://gnome-schedule") or by putting into gnome-session-properties a quoted command (or commands separated by ;, i.e. semicolon) starting with bash -c, like this way: 
```
bash -c "rm -rf ~/.macromedia/Flash_Player/#SharedObjects/*"
``` as suggested [here]("http://ubuntuforums.org/showpost.php?p=10120454&postcount=4"). 

There is also another fresh [thread]("http://ubuntuforums.org/showthread.php?p=10423781") on this issue. And some bug reports: [460746]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/460746"), [518740]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/518740"). Consider to mark those affecting you also.

---

