---
title: "Sudoers   /etc/sudoers"
date: 2011-07-15
forum: General Help
---

### Post by Gr72 on 2011-07-15
Hey guys, I have a problem not running and sudo command.
I get 
"gr72@Grady:~$ sudo
>>> /etc/sudoers: syntax error near line 13 <<<
sudo: parse error in /etc/sudoers near line 13
sudo: no valid sudoers sources found, quitting"

everytime I try to run sudo. This happened after I ran "sudo gedit /etc/sudoers"
then I tried to close the gedit and it said save, so I saved and now I can't open the file. Can you please help? Thanks in advace.

---

### Post by haqking on 2011-07-15
> **Gr72 said:**
> Hey guys, I have a problem not running and sudo command.
I get 
"gr72@Grady:~$ sudo
>>> /etc/sudoers: syntax error near line 13 <<<
sudo: parse error in /etc/sudoers near line 13
sudo: no valid sudoers sources found, quitting"

everytime I try to run sudo. This happened after I ran "sudo gedit /etc/sudoers"
then I tried to close the gedit and it said save, so I saved and now I can't open the file. Can you please help? Thanks in advace.

why did you edit the sudoers file and what did you change then ?

---

### Post by idoitprone on 2011-07-15
well...
can you post
```
cat /etc/sudoers
```if you can
We kidda need to see the file in order to help

well you can boot to recovery and try to fix it urself, but this time use visudo, sudoers file is not meant to be edited directly

[http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)

---

### Post by WorMzy on 2011-07-15
Two things:

[LIST=1]
[*]Never use "sudo" with graphical applications. Doing so can cause permission problems in your home folder.
[*]Only ever edit sudoers with the "visudo" command. The visudo command prevents you from leaving sudo unusable.
[/LIST]

Luckily, this situation is recoverable. Follow this guide: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Gr72 on 2011-07-15
[I]gr72@Grady:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied[/I]
  

and when I try to open it manually from the actual directory I get

[I]Could not disply "etc/sudoers"
The file is of an unknown type[/I]

---

### Post by nothingspecial on 2011-07-15
I don't know how you managed that.

You should not try to edit the sudoers file with anything but visudo.

But, since you have. What shall we do. I have absolutely no idea if this will work. It should in theory, but really, I don't know, you might want to wait for someone else.

Copy this into a text file

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d
```

Call it what you like but I'm going to assume you save it in your home directory and call it blah.txt

Log into a root recovery console.

type

```
mv /etc/sudoers /etc/sudoers_borked
mv /home/[COLOR="Red"]username[/COLOR]/blah.txt /etc/sudoers

```

change the red username for your real username

I'm doubly unsure of this next bit but I think you might have to

```
chmod 0440 /etc/sudoers
```

I'll say that again, [SIZE="2"][COLOR="Red"]I'M REALLY UNSURE ABOUT THAT BIT[/COLOR][/SIZE]

Then type ```
exit
``` and try to resume a normal boot.

---

### Post by Gr72 on 2011-07-15
ok.... I'll try it....

---

### Post by Gr72 on 2011-07-15
How do you open a recovery console?

---

### Post by nothingspecial on 2011-07-15
Reboot and hold down the Shift key

---

### Post by Gr72 on 2011-07-15
Umm yea, that didn't work

---

### Post by Elfy on 2011-07-15
> **nothingspecial said:**
> Reboot and hold down the Shift key

and boot with the second ubuntu option - it will show lots of text then a small menu - choose root terminal as shown in the link you were given earlier

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Gr72 on 2011-07-15
is there anyway to delete the sudoers file, make a new one then replace it b/c it can't read the sudoers file

---

### Post by nothingspecial on 2011-07-15
*****EDIT***** Just discovered they've taken screen out of the default packages so forget all this  unless you have a wired connection and can boot into recovery with networking mode and type apt-get install screen

If not, unless someone can tell you how to do it with vi or emacs, you'll have to copy it all out. ****EDIT****






Type screen (in the recovery console (I hope it's still installed by default))

type ```
visudo
```

Press Ctrl-A then C

type ```
less /home/username/blah.txt
```

(change username for your real username and blah.txt for what you saved the sudoers file for)

Press Ctrl-A then [

Go to the end or beggining of the file with your arrow keys. At the very first/last letter press the space bar, then use your arrow keys to highlight the entire file. Then press the space bar again.

Press Ctrl-A then 0 to get back to the sudoers file. Using the backspace key, delete the lot. Then press Ctrl-A then ] to paste what you just copied into it.

Press Ctrl-O to save it then Ctrl-X to exit then tpe ```
exit
```

See if you can boot.

---

### Post by Gr72 on 2011-07-15
It's fixed..... I did recovery console "visudo" and there was stuff added to the file on line 13 so I deleted it saved, rebooted and now have root access 

THANKS GUYS!!!!!!

---

### Post by nothingspecial on 2011-07-15
Good news :p

---

