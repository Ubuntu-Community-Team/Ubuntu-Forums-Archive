---
title: "Desktop doesn't load"
date: 2006-04-22
forum: General Help
---

### Post by MacFloyd on 2006-04-22
Alright, I just installed Ubuntu less than an hour ago and this is my first experiance with linux so bare with me.

Problem:
After I enter my login name and password it gives me some text about copywrite and linux being free ect.  Then I get this
user-name@computer-name:~$

I have no idea what I should enter and I have looked at several guide and as far as I can tell the desktop should automaticly load after a sucsessful login.

Specs
Computer:IBM Aptiva, was running 95, was bought around 1995-96
Processor: Pentium 120 MHz
RAM: 48 MB
Video Card: 1024 KB
Ubuntu Version 5.10

---

### Post by SeeWhy on 2006-04-22
I'm about as new to Ubuntu as you are and have got the same result after changing my video card. The system boots up OK with the old card, but spits the dummy with a new video card. Did you make any hardware changes after the first install?

---

### Post by MacFloyd on 2006-04-22
I haven't done any hardware changes, all I have done is fiddled with the Bios and messing around with bash.  So far nothing seems to work, well the Bash commands work but I don't know what I am doing.

---

### Post by Kevinator on 2006-04-22
Normally you should see a login screen that has some (sort of) pretty graphics. When you log in, the desktop should appear. It sounds like in your case you logged into a text-mode terminal. You may not have gotten the graphical environment because your video hardware failed to initialize properly. You may not have the right drivers installed.

I would suggest typing "startx" at the command prompt. I doubt it will work, but it may give you some useful diagnostic information.

In order to troubleshoot this problem you should probably be aware of how to switch between different virtual terminals. Pressing Ctrl+Alt+[A function key from F1 to F7] switches to the specified terminal. Terminal 7 is usually the graphical one. So if you end up at a text terminal and don't know what to do, you may be able to get back to the graphical terminal by pressing Ctrl+Alt+F7. If you wind up with a graphical session that isn't responding, you can get to a text terminal by using a different function key. (In that case you can also try to kill your graphical session by pressing Ctrl-Alt-Backspace.)

---

### Post by MacFloyd on 2006-04-22
Thank you for the help but none of that worked.  Perhaps I need to do a little upgrading on my old comp that i plan to mess around with linux on.  Once again thanks for the help.

---

### Post by Kevinator on 2006-04-22
Did startx give any error messages? Like I said, I didn't expect it to work. I just expected it might give a clue about what the problem is. Similarly, you could try "sudo /etc/init.d/gdm start". If you post the output of those commands here, we'll have a better idea of what direction to try next.

---

### Post by MacFloyd on 2006-04-22
yea it just said command not found i think,  I have to reinstall, I reinstalled to see if i could fix anything and did something wrong, go figure.  

Edit: Never mind i just have to fix my  BIOS, I will try your ideas in a little bit

---

### Post by MacFloyd on 2006-04-22
alright from
Sudo:
usage: sudo -k|-L|-V|-h|-k|-l|-v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
[-e file [...] | -i | -s | <command>}

Sudo start
Funny thing i did that once and it asked for a password that command not found and now it doesn't recognize it at all.

the rest did nothing

---

### Post by Kevinator on 2006-04-22
I don't understand what you are doing now. It doesn't look like you are typing the command I suggested. The command is:

sudo /etc/init.d/gdm start

This should ask for your password if you haven't provided it recently (it remembers your password for 15 minutes or something, so you don't need to keep entering it if you are doing several commands).

The fact that startx was not found suggests that maybe you haven't installed the ubuntu-desktop package. Please post the output of this command as well:

dpkg -l ubuntu-desktop

---

### Post by MacFloyd on 2006-04-23
I believe you are right, no packages found matching ubuntu-desktop.
it isn't finding the first command

---

### Post by Kevinator on 2006-04-23
Then you may just need to install ubuntu-desktop:

sudo apt-get install ubuntu-desktop

---

### Post by MacFloyd on 2006-04-23
I belive it is working.  It is currently installing and hopefully it will work.

---

### Post by MacFloyd on 2006-04-23
You know what I think the problem is.  My computer cant run the GUI.  I will just learn to use the text interface.  Then when I get a new computer I can put linux on the one I am using right now.

---

