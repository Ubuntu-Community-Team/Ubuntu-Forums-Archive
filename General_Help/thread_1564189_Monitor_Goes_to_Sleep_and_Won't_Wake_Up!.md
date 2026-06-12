---
title: "Monitor Goes to Sleep and Won't Wake Up!"
date: 2010-08-30
forum: General Help
---

### Post by czar420 on 2010-08-30
Hi. I just recently got my old box back and now I'm running 10.4. I've had some minor issues that I have got through but now there is one which seems to really be frustrating me. At any random time my monitor may go black as if it is in sleep mode. The problem is when it does this, no mouse movement or keystroke will wake the thing up. So I am forced to press the power button. When I press the power button the Ubuntu logo pops up on the screen as if it magically woke up but it is too late because now the computer is shutting down... When I go to System>Preferences>Screensaver I get to the options for the screensaver and I have about 2 seconds before that triggers the screen going black. 

If anyone can please help me. I have a lot that I need to do but I can't even start until I know that my screen won't shut off at any random moment!

---

### Post by czar420 on 2010-08-30
BUMP!

What, fifty views and nobody can help me?

I'd really like for this to stop happening to me because it is interfering with my abilities to do anything that takes more than five minutes. It actually did this problem while I was attempting to type this... So please anybody have any ideas?? Should I just downgrade versions? I'd hate to do that because I'm liking 10.4 other than this stupid monitor issue...

---

### Post by u_lockjustice on 2010-08-31
I am having the same problem.

I installed 10.04 yesterday and went to change the screensaver options when suddenly my screen went black and I was unable to wake it up using the keyboard or mouse and was forced to restart.

---

### Post by czar420 on 2010-09-01
> **u_lockjustice said:**
> I am having the same problem.

I installed 10.04 yesterday and went to change the screensaver options when suddenly my screen went black and I was unable to wake it up using the keyboard or mouse and was forced to restart.
Were you able to solve this problem?

---

### Post by czar420 on 2010-09-01
I have tried sudo gconf-editor and went to **apps/gnome-power-manager/lock** and unchecked boxes. I close and go to **System>Preferences>Screen-Saver**... and just like that the screen goes black without any time for me to even see what the screen saver options are set as. No mouse movement or key stroke will recover. I am then forced to reboot and hope that it won't kick on at any random moment.. which I know it will.

Help Please!

---

### Post by sikander3786 on 2010-09-01
Try adding these lines to the end of your /etc/X11/xorg.conf

```

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

```

And post back if problems persist.

---

### Post by czar420 on 2010-09-01
I typed "sudo gedit /etc/X11/xorg.conf" and I get nothing but a blank white window? 

wrong command?

---

### Post by sikander3786 on 2010-09-01
Make sure you typed capital "X" in X11 instead of "x".

If it is still empty try running this command as see if a few configurations pop up in the file.

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by czar420 on 2010-09-01
[FONT=monospace]I tried the sudo nano way via terminal and I get the file to open. I see at the bottom ^ with letters next to them for the various options. But I don't know what to do from here. you say to add this text, how? I can type it right away is that all I need to do? I've been using linux for only a limited time but I don't know exactly what I'm doing. I'm doing my best to learn though so a walk through would be cool.
[/FONT]

---

### Post by czar420 on 2010-09-01
Yes I made sure that I was typing the correct case in X11. just a blank window. I even tried it with x11 just to see and the same thing. 

I tried the last command dpkg reconfigure and it didnt do anything in my terminal except go to the next line. I tried it a couple of times with the same result.

---

### Post by sikander3786 on 2010-09-01
Never had a problem like this. Did a little research and found this command. Try this one also and again take a look at your xorg.conf.

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by sikander3786 on 2010-09-01
My xorg.conf is also empty. Just checked. Sorry, I think Lucid no longer requires xorg.conf file.

[COLOR="Red"]EDIT:[/COLOR] What is your graphics card make and model? And also which version of drivers is installed?

---

### Post by czar420 on 2010-09-01
Ok well I have to go to work and probably won't be back on a computer until the morning. Please anybody has suggestions don't be ashamed to post some replies! Thanks guys!

---

### Post by satish_j on 2010-09-01
After how much time does your monitor goes to sleep??you can check it from system->preferences->Power management..
If it is some value,change it to 'Never'(even for HD)
Iam facing the same problem..just found on some blog that the above setting should solve the problem..I have just applied the setting and now am monitoring the issue...Fingers crossed.

---

### Post by SurferEddie on 2010-09-04
I have this problem as well.  Pentium box circa 2000.  Runs like a champ with this exception.  I've had it installed for 3 months but today was the first time I've had this problem.  I really don't know what I'm doing so I can't really tell you what SW I've added.  This is all very new to me and I'm not a programmer or developer.  Just a hack noobie.

---

### Post by jeight on 2010-09-04
This is not a fix, but in my situation my laptop does something similar when I close the lid and then open the lid. If you get a black blank screensaver screen first try entering your password and see if that works. If not sometimes switching to another x screen and then back will work. Try ctrl-alt f2 and then switch back with ctrl-alt f7. Like I said these are not fixes but could prevent a hard reboot.

---

### Post by Eric106 on 2011-05-18
> **jeight said:**
> This is not a fix, but in my situation my laptop does something similar when I close the lid and then open the lid. If you get a black blank screensaver screen first try entering your password and see if that works. If not sometimes switching to another x screen and then back will work. Try ctrl-alt f2 and then switch back with ctrl-alt f7. Like I said these are not fixes but could prevent a hard reboot.


Thanks for post. I had never though to try switching virtual terminals like that but it does bring it back.  This saves killing the X session remotely every time.

I'm trying to diagnose a similar problem where the monitor will go into standby after some hours of inactivity.  I can intentionally put the system in suspend mode and it comes out just fine but if I leave it sit powered up, say overnight, the monitor goes in to standby and won't come back out.  I have every power management setting I can find turned off right now but it is still doing it and I'm have no idea what is causing the problem.

-Eric

---

