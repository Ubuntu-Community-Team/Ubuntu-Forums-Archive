---
title: "Need Emergency Logon Help"
date: 2012-09-02
forum: General Help
---

### Post by aviator1 on 2012-09-02
> **pqwoerituytrueiwoq said:**
> can you post the output of these commands
```
cat /proc/cpuinfo | grep "model name" | head -1
``````
lspci | grep VGA
``````
sensors
```you could try the nvidia driver in the xswat ppa if this is not a really old system

Intel (R) Core (TM) 2 quad CPU Q6600 @ 2.4 GHz
VGA compatible controller NVIDIA Corporation G86 [GeForce G8300 GS] Rev a1

If I knew what you meant by, "try the nvidia driver in the xswat ppa if this is not a really old systemt," I would try it.

I don't think the computer is getting hot. The fans are all working, and I took the side off, and have a small desk fan cooling it, also.

Thanks very much for your help.

---

### Post by aviator1 on 2012-09-02
> **2F4U said:**
> Is the machine getting hot? Are you running the default desktop environment (Unity)? What model of nVidia card do you have?

I don't think it's getting hot. All the fans are running, and I have the side off and have a small desk fan blowing in the case, also.

I have no idea what "Unity" means, or how to find out if that is what is there.

I am using whatever the upgrade put there. I have a picture for wallpaper, but no other changes.

Actually, the picture was on my 10.04, and the upgrade just kept it.
The Video card is an Nvidia GeForce 8300 GS

Thanks for your help.

---

### Post by pqwoerituytrueiwoq on 2012-09-02
[Unity](http://www.omgubuntu.co.uk/wp-content/uploads/2011/07/Selection_010.jpeg) Default on Ubuntu 12.04

this person is using a desktop just so everyone knows
this will get the correct GPU driver on your system
```
sudo apt-get purge nvidia-173; if [ -e "/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list" ]; then sudo apt-get update;sudo apt-get install nvidia-current; else sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current; fi
```

---

### Post by aviator1 on 2012-09-02
I was having trouble with 12.0, which I loaded this morning. I used a set of commands that was recommended, but now cannot logon.
 
I get to a black screen which says:
 
dave-desktop login:
Password:
 
I use dave as the login, and then my regular password.
 
I then get a welcome to Ubunty 12.04.01 LTS and the following prompt:
 
dave@dave-desktop:~$
 
What do I need to do to finish the logon, and how do I correct this?
 
Thanks for any help. I'm using my wife's computer to post this.
 
Dave

---

### Post by aviator1 on 2012-09-02
> **pqwoerituytrueiwoq said:**
> [Unity]("http://www.omgubuntu.co.uk/wp-content/uploads/2011/07/Selection_010.jpeg") Default on Ubuntu 12.04
 
this person is using a desktop just so everyone knows
this will get the correct GPU driver on your system
```
sudo apt-get purge nvidia-173; if [ -e "/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list" ]; then sudo apt-get update;sudo apt-get install nvidia-current; else sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current; fi
```
 
I used your script above, and now cannot logon.

I get to a black screen which says:

dave-desktop login:
Password:

I use dave as the login, and then my regular password.

I then get a welcome to Ubunty 12.04.01 LTS and the following prompt:

dave@dave-desktop:~$

What do I need to do to finish the logon, and how do I correct this?

Thanks for any help. I'm using my wife's computer to post this.

Dave

---

### Post by flipper T on 2012-09-02
try ```
sudo startx
```

---

### Post by aviator1 on 2012-09-02
> **flipper T said:**
> try ```
startx
```
 
Thanks for your suggestion. I got a lot of words (a page full).
Finally:
 
xinit: giving up
xinit: unable to connect to x server: no such file or dir
xinit: server error
 
Then back to [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL]

---

### Post by pqwoerituytrueiwoq on 2012-09-02
run ```
startx
``` or ```
sudo service lightdm start
```post the error message it gives

edit:
may just have to run ```
sudo nvidia-xconfig; sudo reboot
```

---

### Post by flipper T on 2012-09-02
try 
```
sudo apt-get install xorg-x11-server-Xorg
```

then reboot

---

### Post by aviator1 on 2012-09-02
> **pqwoerituytrueiwoq said:**
> run ```
startx
``` or ```
sudo service lightdm start
```post the error message it gives
 
edit:
may just have to run ```
sudo nvidia-xconfig; sudo reboot
```
  The startx command gets me to the xinit fail and shuts down. The lightdm start gets me to a dead end
and the nvidia sudo stuff kills it also.
 
Too much to re-type manually.
 
Have to be away for a few hours.
 
Please send any ideas. 
 
Thanks,
 
Dave

---

### Post by opensshd on 2012-09-02
Try this:
```
cd /var/log/
edit Xorg.0.log
```

See any relevant information there regarding X errors?

---

### Post by aviator1 on 2012-09-02
> **opensshd said:**
> Try this:
```
cd /var/log/
edit Xorg.0.log
```
 
See any relevant information there regarding X errors?
 
There were some x errors, but I don't know what would be important. I am late for a meeting. Will be back in about 3 hours.
 
Thanks for your help.
 
Dave

---

### Post by pqwoerituytrueiwoq on 2012-09-02
```
sudo apt-get purge nvidia-*;sudo rm /etc/X11/xorg.conf;sudo reboot
```

---

### Post by sffvba[e0rt on 2012-09-02
*Threads **moved **from another thread*... OP - Please don't hi-jack other threads, it just creates confusion and please don't post the same issue in multiple threads.


404

---

### Post by aviator1 on 2012-09-02
> **opensshd said:**
> Try this:
```
cd /var/log/
edit Xorg.0.log
```
 
See any relevant information there regarding X errors?
 
I get:
 
No such file or directory

---

### Post by aviator1 on 2012-09-02
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get purge nvidia-*;sudo rm /etc/X11/xorg.conf;sudo reboot
```
 
This got me back to my desktop, but when I put my password in, it just returns to the same place and wants my password again.

---

### Post by aviator1 on 2012-09-02
> **not found said:**
> *Threads **moved **from another thread*... OP - Please don't hi-jack other threads, it just creates confusion and please don't post the same issue in multiple threads.
 
 
404
 
Sorry. The other post was mine, also. I had lost all my login info, so I set up a new account.

When I got on this machine, it remembered my login info. That's why the query was under 2 threads.

I'll be more careful, and not let that happen again. I do apologize..

---

### Post by steeldriver on 2012-09-02
> **aviator1 said:**
> This got me back to my desktop, but when I put my password in, it just returns to the same place and wants my password again.

Did you run startx as sudo at any point? If so that creates a root-owned .Xauthority file in your home dir, which can't be overwritten on normal user login. If so go into a virtual terminal (Ctrl-Alt-F1) and login at the text console, then:

```
rm ~/.{ICE,X}authority
```It will prompt you to confirm but should let you do so; when you're done type 

```
exit
```and then Ctrl-Alt-F7 back to the graphical login screen and try again

---

### Post by aviator1 on 2012-09-02
> **steeldriver said:**
> Did you run startx as sudo at any point? If so that creates a root-owned .Xauthority file in your home dir, which can't be overwritten on normal user login. If so go into a virtual terminal (Ctrl-Alt-F1) and login at the text console, then:
 
```
rm ~/.{ICE,X}authority
```It will prompt you to confirm but should let you do so; when you're done type 
 
```
exit
```and then Ctrl-Alt-F7 back to the graphical login screen and try again
 When this issue began, I was instructed to type startx, but it got me to several lines that said xinit fail and shut the computer down.
 
As of now, I can get on as a guest, but when I type my password in I get a black screen in the upper left corner with [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL]
 
Thanks for your help.

---

### Post by steeldriver on 2012-09-02
Right. So when you see

```
dave@dave-desktop:~$
```

you *are* logged in - just to a console session rather than your graphical desktop session. We need to figure out why your desktop session won't start. Initially that was because your whole xserver subsystem / graphics drivers were messed up (which pqwoerituytrueiwoq helped you fix). Now it sounds like you can get to the graphical session-manager (lightdm) logon screen but when you enter your credentials there it can't start your user-session and just bounces you back to the graphical logon screen? That's what I'm trying to help you with.

---

### Post by aviator1 on 2012-09-02
> **steeldriver said:**
> Right. So when you see
 
```
dave@dave-desktop:~$
```
 
you *are* logged in - just to a console session rather than your graphical desktop session. We need to figure out why your desktop session won't start. Initially that was because your whole xserver subsystem / graphics drivers were messed up (which pqwoerituytrueiwoq helped you fix). Now it sounds like you can get to the graphical session-manager (lightdm) logon screen but when you enter your credentials there it can't start your user-session and just bounces you back to the graphical logon screen? That's what I'm trying to help you with.
 I appreciate all that you are doing.

---

### Post by steeldriver on 2012-09-02
no problem, please type the following command at the ' dave@dave-desktop:~$' prompt

```
ls -al ~/.*authority
```

and post the result back here (really we just need to know who is listed as the owner - you or root, no need to post the rest)

---

### Post by aviator1 on 2012-09-02
> **steeldriver said:**
> no problem, please type the following command at the ' dave@dave-desktop:~$' prompt
 
```
ls -al ~/.*authority
```
 
and post the result back here (really we just need to know who is listed as the owner - you or root, no need to post the rest)
 -rw--------- 1 dave dave 114 sep  2 20:44 /home/dave/.Xauthority

---

### Post by steeldriver on 2012-09-02
OK thanks in that case it's not the issue I thought it might be

---

### Post by pqwoerituytrueiwoq on 2012-09-02
we could try a different desktop manager like gdm or mdm

were you able to login before (and see your desktop) on 12.04? if so nvidia-173 ([FONT=Courier New]sudo apt-get install nvidia-173;sudo reboot[/FONT]) may work
if that makes things worse "[FONT=Courier New]sudo apt-get purge nvidia-173;sudo reboot[/FONT]"

try loging in with effects off

---

### Post by aviator1 on 2012-09-02
> **steeldriver said:**
> OK thanks in that case it's not the issue I thought it might be
 But, a new issue has come up. I shut down from the guest login, and now when I power up, I get to the [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] and it's locked. I can get to the login and PW request by ctrl+f2. Then I can get the blinking dash to enter stuff

---

### Post by aviator1 on 2012-09-02
> **pqwoerituytrueiwoq said:**
> we could try a different desktop manager like gdm or mdm
 
were you able to login before (and see your desktop) on 12.04? if so nvidia-173 ([FONT=Courier New]sudo apt-get install nvidia-173;sudo reboot[/FONT]) may work
if that makes things worse "[FONT=Courier New]sudo apt-get purge nvidia-173;sudo reboot[/FONT]"
 
try loging in with effects off
 That now gets me to a black screen with [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] and it's locked.
I can use ctrl+alt+f2 to get me to [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL]_ with the cursor blinking

---

### Post by aviator1 on 2012-09-02
Would it be easier to:
1. Uninstall 12.0 and reinstall
2. Reinstall 12.0
 
I have it on a USB stick
 
I really appreciate everone's help.

---

### Post by pqwoerituytrueiwoq on 2012-09-02
probably just back your data up before re-formating
easily done from a live cd/usb

---

### Post by aviator1 on 2012-09-02
> **pqwoerituytrueiwoq said:**
> probably just back your data up before re-formating
easily done from a live cd/usb
 How would I back up the data if I cannot get to it? Sorry to be so basic, but I'm just a user.

---

### Post by pqwoerituytrueiwoq on 2012-09-02
you can open the file browser and navigate to your home folder
your data is accessible, your GUI is just broken on your install
just click on XXX mb files system on the left of the file browser and click on the folder called home then the one with your name

---

### Post by aviator1 on 2012-09-02
I want to thank everyone for the help I have received tonight. I have to call it a night due to an early morning tomorrow. I'll post what progress I make ASAP.

---

### Post by aviator1 on 2012-09-03
Good morning all.
 
I'm desparate for some help today. 
 
To recap where I am......this is my computer: Intel (R) Core (TM) 2 quad CPU Q6600 @ 2.4 GHz, VGA compatible controller NVIDIA Corporation G86 [GeForce G8300 GS] Rev a1.
 
Problems started yesterday when I upgraded from 10.04 to 12.04 and the computer would freeze every few minutes. We almost had it fixed, but the situation has evolved to where I cannot boot.
 
When I try to boot up, I get to a black screen that shows dave@dave-desktop:~$. At this point, the system is locked. I can use ctrl+alt+f2 to get me to a login and password prompt with a blinking cursor. I can then add a command, but have no idea what to type in.
 
I was going to try to reinstall, but my computer will not boot from a USB stick. Yes, I have the boot sequence to allow that. I tried making a CD from the USB stick, but the process tells me there is a back section on the CD and will not continue.
 
I really appreciate anyone's help to get me running again.

---

### Post by aviator1 on 2012-09-03
UPDATE.....
 
I clicked on the [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] with the mouse, and that gave me a solid white rectangle. 
 
I typed "exit" and it takes me to my desktop where the password prompt is.
 
However, when I type in my password, it takes me back to a small black screen in the upper left corner of the monitor, and the [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL]
 
I am able to type a command, but still have no idea what to type in.

---

### Post by pqwoerituytrueiwoq on 2012-09-03
so you have a terminal and wallpapaer on hte screen?
click on the gear when you login before hitting enter with you password and change the list to unity/xfce/kde/gnome/gnome classic/mate/unity no effects what ever DE makes you happy

---

### Post by aviator1 on 2012-09-03
Another update......
 
I was able to use the "guest" logon, but could not view my drives. 
 
I shut down suing the shutdown button from the guest area, and now when I boot, I get to the same [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] prompt and use the ctrl+alt+f2 to get to the login/password prompts.
 
Also on the screen at the top, is Ubuntu 12.04.1 LTS dave-desktop tty2
 
When I type in my login and password now, I get to the [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] with the blinking cursor.
 
When I type "exit", it takes me back to a black screen and the login prompt.

---

### Post by aviator1 on 2012-09-03
> **pqwoerituytrueiwoq said:**
> so you have a terminal and wallpapaer on hte screen?
click on the gear when you login before hitting enter with you password and change the list to unity/xfce/kde/gnome/gnome classic/mate/unity no effects what ever DE makes you happy
 After shutting down from the guest area, when I boot now, I get to the black screen with a very small [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] in the upper left corner. The machine at this point is locked up.
 
When I type ctrl+alt+f2, I get:
Ubuntu 12.04.1 LTS dave-desktop tty2
dave-desktop login:
 
I type in dave and get
 
Password:
 
I type in my password, and get:
 
[EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] with a blinking cursor
 
If I type exit, I get back to the login prompt.

---

### Post by pqwoerituytrueiwoq on 2012-09-03
from a tty (ctrl+alt+f1) [FONT=Courier New]sudo service lightdm stop;startx[/FONT]

---

### Post by aviator1 on 2012-09-03
> **pqwoerituytrueiwoq said:**
> from a tty (ctrl+alt+f1) [FONT=Courier New]sudo service lightdm stop;startx[/FONT]
 Whn I get to the black screen and the [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] in the corner, I pressed ctrl+alt+f1 and that gave me:
 
Ubuntu 12.04.1 LTS dave-desktop tty1 (last time it was 2)
 
I also have:
 
dave-desktop login: (I type dave)
Password: (I type my password in)
 
I get [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] with the blinking cursor and I type:
 
sudo service lightdm stop;startx
The system requests my password and I enter it and hit enter....
 
I then get a black screen. Only ctrl+alt+del will do anything.

---

### Post by steeldriver on 2012-09-03
It's a little bit hard to guess, but it *sounds* like what is happening is

1. you have autologin enabled for user 'dave' (this is the only way you can get to a 'dave@dave-desktop:~$ ' prompt straight from boot)

2. your desktop session has been changed from the default ubuntu GUI to an 'xterm' session, either because it's finding an .xsession or .xinitrc in your home dir that tells it to do so, or because something is preventing the normal session from starting, and it is falling back to a minimal xterm 

3. you can't select a different session from the login screen after booting because of the autologin

You say that the machine is 'locked up' when you get to the **small** dave@dave-desktop:~$ but elsewhere you said you could click the mouse in it and get a white cursor - have you actually tried typing commands there? Or even typing garbage and then pressing 'Enter' to see if the terminal responds?

If you are comfortable using the xterm *OR* the Ctrl-Alt-F2 virtual terminal, you can do some more diagnosing with these commands

```
echo $DESKTOP_SESSION
```and to see if autologin is enabled

```
cat /etc/lightdm/lightdm.conf 
```and to see if you have a .xsession or .xinitrc:

```
ls ~/.x*
```

---

### Post by aviator1 on 2012-09-03
> **steeldriver said:**
> It's a little bit hard to guess, but it *sounds* like what is happening is
 
1. you have autologin enabled for user 'dave' (this is the only way you can get to a 'dave@dave-desktop:~$ ' prompt straight from boot)
 
2. your desktop session has been changed from the default ubuntu GUI to an 'xterm' session, either because it's finding an .xsession or .xinitrc in your home dir that tells it to do so, or because something is preventing the normal session from starting, and it is falling back to a minimal xterm 
 
3. you can't select a different session from the login screen after booting because of the autologin
 
You say that the machine is 'locked up' when you get to the **small** dave@dave-desktop:~$ but elsewhere you said you could click the mouse in it and get a white cursor - have you actually tried typing commands there? Or even typing garbage and then pressing 'Enter' to see if the terminal responds?
 
If you are comfortable using the xterm *OR* the Ctrl-Alt-F2 virtual terminal, you can do some more diagnosing with these commands
 
```
echo $DESKTOP_SESSION
```and to see if autologin is enabled
 
```
cat /etc/lightdm/lightdm.conf 
```and to see if you have a .xsession or .xinitrc:
 
```
ls ~/.x*
```
 When I get small [EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] in the corner, the is a small white rectangle. I do not have a mouse cursor, but after left clicking a few times, the rectangle turns solid white and I can type.
 
I typed in echo $DESKTOP_SESSION and after hitting enter, the next line showed the word xterm
 
I typed in cat /etc/lightdm/lightdm.conf  and got cat: /etc/lightdm.conf: No such file or directory
 
I typed in ls ~/.x* and got /home/dave/.xscreensaver-getimage.cache /home/dave/.xsession-errors.old
/home/dave/.xsession-errors

---

### Post by aviator1 on 2012-09-03
Further info....
 
I did a hard reset and got back to the small [EMAIL="dave@desktop:~$"]dave@desktop:~$[/EMAIL] and the white rectangle.
 
No button or mouse click will make the rectangle fill. I cannot type anything.
 
When I use ctrl+alt+f2, I get to:
 
Ubuntu 12.04 LTS dave-desktop tty2
dave-desktop login:
Password
 
And after entering the info, I get
 
[EMAIL="dave@dave-desktop:~$"]dave@dave-desktop:~$[/EMAIL] and a blinking cursor
 
These are all in much larger letters
 
Typing in exit here only takes me back to the login prompt.

---

### Post by aviator1 on 2012-09-03
The magic of computers.
 
I did another hard reset and the maching booted all the way to my desktop.
 
When I type in my password, the screen goes black, then brings me back to the desktop.
 
I'm not touching anything until I hear from someone as to what the next step will be.
 
Thanks for everyone's help so far......

---

### Post by steeldriver on 2012-09-03
Do you mean it takes you back to the login screen? if so it is possible that either (i) your home dir is not writable or (ii) the dir is writable but you have screwed up ownership / permissions on the .Xauthority file

Please go back to the virtual terminal (Ctrl-Alt-F2), login, and then type

```
ls -ld ~
ls -al ~/.{ICE,X}authority
```

---

### Post by aviator1 on 2012-09-03
> **steeldriver said:**
> Do you mean it takes you back to the login screen? if so it is possible that either (i) your home dir is not writable or (ii) the dir is writable but you have screwed up ownership / permissions on the .Xauthority file
 
Please go back to the virtual terminal (Ctrl-Alt-F2), login, and then type
 
```
ls -ld ~
ls -al ~/.{ICE,X}authority
```
When I reboot, it goes all the way to my desktop with my original wallpaper.
 
There is a box for my password or to use a guest session. If i select guset seesion, it takes me to a basic ubuntu desktop with the command buttons on the left side.
 
If I type in my password, the screen goes blcak and brings me back to my desktop with the wallpaper.
 
On the box where the passowrd blank is located is a circle in the upper right ahnd corner.
 
Clicking that shows the following selections:
 
Recovery Console
Ubuntu
Ubuntu2d
User defined Session
 
I don't know how to get to the prompt where I need to us ctrl+alt+f2
 
Sorry, I'm just a user, not a techie.

---

### Post by aviator1 on 2012-09-03
From the desktop with wallpaper, I pressed ctrl+alt+f2 and got back to the prompts for the login.
 
The ls -ld ~ shows
 
drwxr-xr-x 54 dave dave 4096 Sep 3 09:47 /home/dave 
(Note that /home/dave is in Blue)
 
The ls -al ~/.{ICE,X}authority shows
-rw------- 1 root root 57 Sep 3 09:29 /home/dave/.Xauthority

---

### Post by steeldriver on 2012-09-03
OK so lets try removing the ~/.Xauthority file - it should be owned by 'dave' and it will get regenerated on successful session login

```
rm ~/.Xauthority
```It will likely ask you to confirm that you want to remove read only regular file or somesuch so you will need to confirm 'y'

Then go back to the GUI login (Ctrl-Alt-F7 should get you there - if not you may need to reboot) and try again

---

### Post by aviator1 on 2012-09-03
> **steeldriver said:**
> OK so lets try removing the ~/.Xauthority file - it should be owned by 'dave' and it will get regenerated on successful session login
 
```
rm ~/.Xauthority
```It will likely ask you to confirm that you want to remove read only regular file or somesuch so you will need to confirm 'y'
 
Then go back to the GUI login (Ctrl-Alt-F7 should get you there - if not you may need to reboot) and try again
 
We're back to square 1......
 
On the hard reset, I am back at the black screen with the small [EMAIL="dave@dave.desktop:~$"]dave@dave.desktop:~$[/EMAIL] and the empty white rectangle. No ket willcause any change.
 
Using ctrl+alt+f2will take me through the sequence of getting to:
 
[EMAIL="dave@dave-deasktop:~$"]dave@dave-deasktop:~$[/EMAIL] in larger letters and a blinking cursor.

---

### Post by steeldriver on 2012-09-03
So what you're seeing sounds normal - for a user whose $DESKTOP_SESSION is set to 'xterm'

Are you getting to a GUI login screen now - or is it booting straight to the session with the small prompt 'dave@dave-desktop' (the 'xterm' session)?

If you ARE getting a GUI login, you can do as pq suggested i.e. press the circle button next to your name and select either 'Unity' or 'Unity-2d' from the menu

If you are NOT getting to the GUI login, then we need to turn off your autologin so that you can

---

### Post by aviator1 on 2012-09-03
> **steeldriver said:**
> So what you're seeing sounds normal - for a user whose $DESKTOP_SESSION is set to 'xterm'
 
Are you getting to a GUI login screen now - or is it booting straight to the session with the small prompt 'dave@dave-desktop' (the 'xterm' session)?
 
If you ARE getting a GUI login, you can do as pq suggested i.e. press the circle button next to your name and select either 'Unity' or 'Unity-2d' from the menu
 
If you are NOT getting to the GUI login, then we need to turn off your autologin so that you can
 
It is booting straight to the small prompt [EMAIL="dave@dave-desktop"]dave@dave-desktop[/EMAIL] However, that is frozen until I use ctrl+alt+f2 to get to the sequence of login/PW/binking cursor.

---

### Post by aviator1 on 2012-09-03
> **aviator1 said:**
> It is booting straight to the small prompt dave@dave-desktop However, that is frozen until I use ctrl+alt+f2 to get to the sequence of login/PW/binking cursor.
 It looks like it's pretty much fixed from the logon issues. I was sitting here, and the rectangle turned white after about 30 minutes. I typed "exit" and got the desktop. I have been able to logoff and on without too many glitches. Sometimes I get some weird screens on the logoff.
 
However, I am back to the very original problem I posted. The computer will just freeze and the only thing that moves is the mouse cursor. However, nothing can be selected when it freezes.
 
Also, I notice I have no video drivers. I did a driver search and the selections are way different than prior to all these issues. Before, there were several nvidia-173 choices.
 
Now, there are only NVIDIA binary Xorg driver, kernel module and VDPAU library types of choices.
 
None of them are activated.
 
Should I activate one of them to see if the freeze problem stops?
 
Thanks very much for all your help.

---

### Post by steeldriver on 2012-09-03
sorry I am completely lost now - we seem to have gone around in several circles, I can't explain why things that were broken have suddenly started working - I don't think I can really help you here

good luck

---

### Post by aviator1 on 2012-09-03
> **steeldriver said:**
> sorry I am completely lost now - we seem to have gone around in several circles, I can't explain why things that were broken have suddenly started working - I don't think I can really help you here
 
good luck
 I agree about the circles. The only guess I *might* have is that when everything got reset, the processor just took a long time crunching numbers before it straightened itsellf out.
 
I seem to be having normal bootups, logins, and logoffs.
 
I am going to make another thread about the freeze problem. From what I have seen, this is something that has been happening with 12.0 a bit.
 
I really appreciate the time and effort you, PQ, and some others put in to help me with these issues.
 
Hope you all have a Blessed Day!

---

### Post by Crossbow on 2012-09-03
Hi - I'm having the same exact problem. I fixed the no-GUI problem with 

> sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current

Then just ctrl-alt-delete to reboot.

From Here: From: [http://ubuntuforums.org/showpost.php?p=12203435&postcount=16 ](http://ubuntuforums.org/showpost.php?p=12203435&postcount=16 )

But I can't log in as myself. It just keeps throwing me back to the login screen. At least it's the GUI login screen. Interestingly I can log in with my guest ID, but how can I use that to fix the login problem?

Follow-up question: Is this a punishment from the computer gods for me complaining about how ugly the Unity GUI is?

---

### Post by aviator1 on 2012-09-08
The video card was overheating. I changed to a new nvidia GT 430 and it's working fine.

Just took the old one out, and put the new one in....it worked.

I really appreciate everyone's help.

Dave

---

