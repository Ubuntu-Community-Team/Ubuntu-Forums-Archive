---
title: "open a folder owned by root in terminal"
date: 2010-11-27
forum: General Help
---

### Post by slgtheindividual on 2010-11-27
I have a folder owned by root, I can open it by changing the permissions but then I have to change them back when I'm done, I was wondering if there was a way to use the terminal to open the folder as root without changing the permission on the folder permanently? I am admin and have the sudo password if necessary.

Thank you

---

### Post by Cheesehead on 2010-11-27
The answer to your direct question is:

$sudo <action> folder
$sudo gedit /etc/network/if-up.d/upstart   #Example


But what exactly are you trying to do?
There may be an easier and less dangerous way.

---

### Post by deserthowler on 2010-11-27
Not sure what you are trying to do but maybe you can download [COLOR="Red"]**nautilus-gksu**[/COLOR] and use the right click menu to open as administrator in nautilus file manager.

Earl

---

### Post by slgtheindividual on 2010-11-28
I'm not trying to access any system files or anything, I just made an empty folder and changed all the permissions and groups so I could play around with it in the terminal.

I have nautilus gksu but I really want a way to open it from the terminal. When I try 

$sudo cd folder 

I get a message saying sudo cd: command not found

I know how to change the permissions of the file in the terminal and change them back afterwards but I want a temporary change so that I can open it once but as soon as i close the terminal or drop my privileges I can no longer access it without being root.

Thank you for your help.

---

### Post by apollothethird on 2010-11-28
> **slgtheindividual said:**
> I'm not trying to access any system files or anything, I just made an empty folder and changed all the permissions and groups so I could play around with it in the terminal.

I have nautilus gksu but I really want a way to open it from the terminal. When I try 

$sudo cd folder 

I get a message saying sudo cd: command not found

I know how to change the permissions of the file in the terminal and change them back afterwards but I want a temporary change so that I can open it once but as soon as i close the terminal or drop my privileges I can no longer access it without being root.

Thank you for your help.

I don’t know what you’re trying to do, but it appears that you are trying to perform some type of paradox.  It appears that you’re trying to put a normal user in an area where the normal user can’t be.  So the system appears to have some type of protection against that.

If you need to be in that area you’ve created, you can be there as root and do everything you have to do, then leave the area by typing “exit”.

The command sequence is:

```
sudo su
cd folder
... # peform the work
exit
```

If there’s something different that you’re trying to do  you might have to explain what you’re actually trying to accomplish other than place a normal user in a place where the normal user doesn’t belong, or other than perform a command sequence that can’t be done.  Again, there’s a chance that the command sequence that you find doesn’t work, doesn’t work for a reason.  And based on the other suggestions you’re been given, no one can identify a reason to use that sequence.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by spiky001 on 2010-11-28
This will change you to root _**But be carefull as you can cause damage to system being root**_ so use it wisely ```
sudo su
```

---

### Post by WorMzy on 2010-11-28
Use
```
sudo -i
```
To switch to a root prompt. You can't use sudo cd, because cd is a shell command. Once you've got a root prompt, you can cd normally.

Press Ctrl+D, or type "exit" to leave the root shell. Don't leave it lying around where anyone can use it.

[QUOTE=Cheesehead]$sudo gedit /etc/network/if-up.d/upstart #Example[/QUOTE]

Note that in this example sudo is being used to launch a graphical application, this is **wrong**. Use gksu or gksudo for graphical apps, only use sudo for command line stuff. e.g.
```
gksu gedit /etc/network/if-up.d/upstart
```

---

### Post by slgtheindividual on 2010-11-28
Thank you everybody, that was helpful, I just wanted to learn a few new terminal commands, the "sudo su" was what I was really after.

Thanks again to everyone who continuous my education in the world of ubuntu and don't worry, I'll be careful =]

---

