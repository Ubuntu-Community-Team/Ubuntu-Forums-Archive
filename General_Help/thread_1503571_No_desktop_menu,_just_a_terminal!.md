---
title: "No desktop menu, just a terminal!"
date: 2010-06-07
forum: General Help
---

### Post by MaxTTT on 2010-06-07
I am running karmic on my laptop. I made a few changes to config files last night trying to get the laptop to see the windows desktop on the network.

Anyway, I log on this morning, and the blue ubuntu background comes up, (not the normal orange one), but with a terminal window in the top left hand corner (covering where Ubuntu, places etc are located). I am not that familiar with ubuntu, and don't know the script to put in to terminal to see files or access internet..or fix it!

Any idea what to do to restore my desktop to a normal working condition? 

Cheers

M

---

### Post by karthick87 on 2010-06-07
If your panels were  disappeared,you can bring it back by entering these commands in terminal..

[COLOR=Red]gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/COLOR]

---

### Post by MaxTTT on 2010-06-07
Cheers, when I try that I get 
"unknown option -2"

---

### Post by karthick87 on 2010-06-07
> **getyourkarthick said:**
> If your panels were  disappeared,you can bring it back by entering these commands in terminal..

[COLOR=Red]gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/COLOR]



There should be space between 2 and --shutdown

---

### Post by retry32 on 2010-06-07
Try Ctrl > Alt > F2

---

### Post by MaxTTT on 2010-06-07
getyourkarthick, my bad. I have now entered correctly, but nothing happened, just jumped to the next line in terminal.


retry32, I can log in, but I am still just at a terminal screen.

---

### Post by stderr on 2010-06-07
No, the uname/password should be identical: the logins from Alt+Ctrl+F1-F6 are console based TTYs, and from F7-F12 they are corresponding graphical TTYs (so graphical TTY F7, which you normally use, is linked with textual TTY F1).

Can you run this to show us what graphical driver you're trying to run:

```
cat /etc/X11/xorg.conf | grep Driver
```

Also this to show us what driver you're actually running:

```
glxinfo | grep vendor
```

---

### Post by oomar on 2010-06-07
clarification question: does the login screen come up as a graphical log in? if so then make sure taht your session is set to gnome and not on xterm. if the login is the terminal as well... then follow their advice. lol

---

### Post by MaxTTT on 2010-06-07
cat /etc/X11/xorg.conf | grep Driver


[FONT=monospace]I get: 

cat: /etc/X11/xorg.conf: No such file or directory


[/FONT]glxinfo | grep vendorX error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 135 (GLX
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 16
Current serial number in output stream: 16

---

### Post by MaxTTT on 2010-06-07
> **oomar said:**
> clarification question: does the login screen come up as a graphical log in? if so then make sure taht your session is set to gnome and not on xterm. if the login is the terminal as well... then follow their advice. lol

I get the usual black/purple spotlight log in screen, I input my username and password, then it starts loading, and stalls on the same background screen, with nothing else except the terminal in the top left hand corner.

I am very new to Ubuntu, so please don't assume any knowledge.

How do I check if it is set for gnome or xterm?

UPDATE: in the terminal I can type in nautilus, which brings up the desktop and a nautilus window. It brings up the files that are sitting on the desktop, and it brings up the Nautilus window that has my home folder etc. The terminal window is still sitting in the top left, so I don't know if the Applications Places, etc are there.
The weird thing is, if I reboot and go to Nautilus again, the desktop will be there, but no files, and no home folder. Very random.

Also, the nautilus window is stuck at the bottom of the screen and can't be moved or re-sized.
Any ideas?

---

### Post by oomar on 2010-06-07
when you boot up to the log in screen look down at the bottom for a dropdown box labeled "session". if it says "xterm" click on it and change it to "gnome". if it says gnome already.... then you have more complex problems. lol

---

### Post by MaxTTT on 2010-06-08
I don't seem to have that option. All I have at the bottom is the language and keyboard menu, and the date and time.

---

### Post by linuxman94 on 2010-06-08
There should be a menu at the bottom of the login screen once you input your user name.  It will say Sessions next to it. You should open the menu and select GNOME, then login.

---

### Post by oomar on 2010-06-08
[IMG]http://img227.imageshack.us/img227/9402/54351791.png[/IMG]



Ok see the thing named session? it should look like that... lol In the picture it says gnome, which is right, yours im guessing says xterm

---

### Post by MaxTTT on 2010-06-08
Yep, my screen looks exactly like that...but without the session menu! 
In the words of Julius Sumner Miller; "Why is it so?"

---

### Post by oomar on 2010-06-08
even when you click on your username....? like never during the login process is that option there.....?

In the words of the late Gary Coleman, "Whatchu talkin' bout!?"

too soon?

---

### Post by MaxTTT on 2010-06-08
Yes I have played around, clicked everywhere I could, but it is just not there. I can't remember if it every was. I know my ubuntu laptop at work has that menu.
...could it be because this is a dual boot system with Windows loaded first?

Oomar, No one consider Willis in all this...

---

### Post by oomar on 2010-06-09
*sigh*... I need to change my username if possible. lol call me Logan. 

umm no thats not a problem. If you had a problem with that it'd be with GRUB probably and then you wouldnt be able to boot at all. This is odd. What variant is it? 10.04 Ubuntu?

---

### Post by MaxTTT on 2010-06-09
Yes, 10.04, regularly updates, so that's not a problem. 

Do you know the script that shows the last commands used in the computer, I know it's something with -mmin at the end.
I thought I might be able to see what was changed before it all went pear shaped.

---

### Post by oomar on 2010-06-09
if you just type in "history" in the command line it comes up with all the ones youve ever used, in order.

now mine was long enough that i had to scroll up to see them all but if you use "history | less" then it will be scrollable just like a man page.

---

### Post by MaxTTT on 2010-06-12
Well I messed around some more and completely killed the grub.
So this could be marked as solved, because I reinstalled Ubuntu!
Thanks for all your help guys.

---

### Post by hme26 on 2010-08-29
Hi,

Too late to help but I think I had the same problem as you and I just solved it...

I'm running 10.04 and I had messed around with some of my conf files and all had gone horribly wrong. I managed to get the login window to come up but all I got when I logged on was a terminal window. Also, I didn't have the gnome/xterm option on the logon screen either.

I ended up fixing it by reinstalling gnome (sudo apt-get install gnome-core) and then everything seemed to work!

I'm a relative ubuntu novice so this may be pure coincidence but worth a shot if you get the same problem!

---

