---
title: "Starting Windows First?"
date: 2010-04-09
forum: General Help
---

### Post by tomsubt on 2010-04-09
Hello:  I have windows xp home (oem) on my pc and I just installed ubuntu!

I noticed everytime I start the pc now, it starts with Ubuntu and I have to scroll down to highlight windows each time I want to start with Windows!

My question is, how can I get Windows to start first without scrolling down the ubuntu menu and highlighting Windows. 

I'd rather scroll down and hightlight Ubuntu if I need too each time. Is this possible, Anyone have any idea's on this? Thanks

---

### Post by sparky-steve on 2010-04-09
boot into ubuntu....

You need to open a terminal, search for menu.lst (mine is in /boot/grub/menu.lst)

Scroll down

Under ## ## End Default Options ## you'll see the entries... the first is entry 0, second is entry 1, etc. Find which entry you want (possibly 4 for windows, being the fifth listed)

At the top, change

```
default         0
```

to

```
default         x
```

x being the entry you want.

SS

---

### Post by tomsubt on 2010-04-09
oK, I tried to follow your instructions and I got this far, does this make sense to you?  It would not let me type in a password or anything when asked to? Please let me know if I am doing this right and what to do next, Thanks>>>>>>
tomsubt@tomsubt-desktop:~$ menu list
No command 'menu' found, did you mean:
 Command 'dmenu' from package 'dwm-tools' (universe)
menu: command not found
tomsubt@tomsubt-desktop:~$ dmenu
The program 'dmenu' is currently not installed.  You can install it by typing:
sudo apt-get install dwm-tools
dmenu: command not found
tomsubt@tomsubt-desktop:~$ 
tomsubt@tomsubt-desktop:~$ sudo apt-get install dwm-tools
[sudo] password for tomsubt:

---

### Post by sparky-steve on 2010-04-09
I assume you've not used linux terminal much? I'm afraid I wont be around after this reply, so I'll try to be concise.

In the terminal, type:

```
sudo updatedb
```

then

```
sudo locate menu.lst
```

hopefully, it will find menu.lst
Let's assume its full path is /boot/grub/menu.lst

type:

```
sudo gedit /boot/grub/menu.lst
```

Look through the file, and count which entry windows is, starting from 0 (so if its the sixth entry, you want number five)

At the top of the file, change

```
default 0
```

to

```
default x
```

x being the entry number

Save the file

Reboot

Good luck.....

SS

---

### Post by lisati on 2010-04-09
Before we continue: Are you running version 9.10? If so, was it a fresh install?

9.04 and earlier use grub, which has the menu.lst file. 9.10 and newer use grub2 by default for fresh installs, which does things differently.

---

### Post by bplzip on 2010-04-09
In Synaptic Package Manager, search for and install Startup Manager. This worked for me with both GRUB legacy and GRUB2. It's very user-friendly and doesn't require using Terminal.

---

### Post by codemaniac on 2010-04-09
Yes "Startup manager " is all you need.It can make life easier by changing the deafult Os to boot,wait time,bootsplash image and many more as per your wish..serch fot it in synaptic.

---

### Post by tomsubt on 2010-04-09
Yes, I believe it was a fresh install 9.10

Also I found the Startup Manager and put a check mark in the box and hit Enter, I think it is installing now but I dont know for sure I dont see a progression bar. How long should it take and how to know if it installted? Thanks
PS; I tried those intstrucions above but when ever it ask for my password, it will not let me type anything????

---

### Post by Chronon on 2010-04-09
In Synaptic you have to tell it to Apply the changes.  Just selecting the checkbox doesn't start the installation.

Regarding your PS: When it asks for your password it doesn't show anything on-screen but it is recording your keystrokes.  Just enter the password you use to log in and press Enter.

---

### Post by piyushchandrakar on 2010-04-09
The startup Manager Thing is Very best option for the windows start..
because it just uses GRUB. you do not need to rewrite the MBR (windows default boot manager) so as my choice is just install startup manager.

you can see form where to install the startup manager..

system> administration> synaptic package manager

in quicksearch type startupmanager

you will find it, then just right click and select mark for installation

and click above Apply..

its simple and easy install

after installation

just start the startup manager

[B]system> administration> startupmanager

on boot options

default operating system

 select your version of windows..[/B]

select timeout (as what time you want to wait at bootmenu)

close that window......

now your default boot is goin to your windows version.

---

### Post by tomsubt on 2010-04-09
Chronon:  Thank you for the information, did not know about the password.
Also, I have been experimenting and I got alot accomplished, especially getting 
most of the Software installed, including changing the Startup option to windows first.

Ubuntu is a little complicated, Im learning and  I love it. 

Have not figured out how to use the terminal yet, if you have any tips on using it, please let me know, Ok? Thank You again

---

### Post by tomsubt on 2010-04-09
piyushchandrakar,  Thats exactly what I did, could have used your instructions earlier, but Thank You, I will save them for future reference

Meanwhile, any tips or thoughts on using the terminal, even the very basic would be appreciated.
Also I installed a thing called Terminal Emulator
is that the same thing as Terminal? Thanks

Also, do I have to download Winehq in order to open up an .exe file I need to open now?

---

