---
title: "did i install ubuntu wrong?"
date: 2006-04-27
forum: General Help
---

### Post by deansuzi on 2006-04-27
hi. i just particitioned a hard disk space and loaded the disc i burned (from the iso file), and i created my user name and password...to make a long story short, i knew linux programs were command prompt, but after i log in i just can't seem to get past the black and white command prompt screens. i am now downloading a live cd to try because i really don't know where to go or what to do beyond this black and white screen. i'd like to start using all of the components. really all i want to use it for is an alternative to windows. i'd like to get online with firefox and set up an account with thunderbird, and burn cd's/dvd's, etc... i just really can't get off square one. when i boot my log in works, but i can't seem to go anywhere afterwards...does it sound like i loaded it wrong? i know all of the files i need are in the iso...help!!!

---

### Post by cgjones on 2006-04-27
What type of install did you do? Are you getting any error messages?

---

### Post by mscman on 2006-04-27
Is your login screen a command prompt or a graphical login (aka GDM)?  It sounds like you may have some xorg problems, which can be easy to fix.

---

### Post by deansuzi on 2006-04-27
ummm...i really couldn't tell you...which one was i supposed to do? i just want to use it as a regular operating system, an alternative to windows. i'm certainly willing to learn all there is about it...maybe i just need to reinstall? should i have chosen to set it up as a file system? i'm sorry. i know windows pretty well, but as i said i'm an absolute beginner here...that's probably what i did wrong. if i just want to set it up the way i afforementioned, what kind of system should i set it up as?

---

### Post by deansuzi on 2006-04-27
it's all command prompt without graphics...

---

### Post by deansuzi on 2006-04-27
if it's just a problem that simple, such as the xorg problem you mention, i'm willing to try it out...

---

### Post by deansuzi on 2006-04-27
[QUOTE=mscman]Is your login screen a command prompt or a graphical login (aka GDM)?  It sounds like you may have some xorg problems, which can be easy to fix.[/QUOTE]
if so, how do i fix this xorg problem? it's command prompt only. i don't have any graphics...

---

### Post by cgjones on 2006-04-27
It sounds like you did a regular install, so it most likely is an issue with xorg.

---

### Post by deansuzi on 2006-04-27
[QUOTE=cgjones]It sounds like you did a regular install, so it most likely is an issue with xorg.[/QUOTE]
any advice?

---

### Post by deansuzi on 2006-04-27
[QUOTE=cgjones]It sounds like you did a regular install, so it most likely is an issue with xorg.[/QUOTE]
is there any components i need to install to solve the problem?

---

### Post by JulienC on 2006-04-27
I had a similar problem while installing, it went through the user creation screen several times, I went out of it manually, and it asked me to reboot my PC (without installing packages). After I rebooted, I only had a full-screen terminal, no X system working. I began the installing process all over, and then everything worked well.

Sorry if I expressed myself poorly, english is not my primary language.

---

### Post by bbarrons on 2006-04-27
what do you get when you type     sudo apt-get update
at the command prompt?
It should ask for your password and then pull up a list of sources.....
is your cpmuter connected to the network-internet?

---

### Post by deansuzi on 2006-04-27
yes, i have cable internet. i did try sudo apt-get update, and it said the command was not recognized...

---

### Post by cgjones on 2006-04-27
Login in and type this at the command prompt:
```
dmesg | more
```
You can scroll through the output page by page with the space bar. Look for any mention of X11, xorg, X Windows, etc. If you find any, post them here.

---

### Post by bbarrons on 2006-04-27
you must be sitting at another pc right now.....
can you im me? 
I am at yahoo im barrbill_1
maybe we can try a few things to get you up without  reinstalling....

---

### Post by az on 2006-04-27
[QUOTE=deansuzi]yes, i have cable internet. i did try sudo apt-get update, and it said the command was not recognized...[/QUOTE]

Your install probably failed.  that could be due to a bad disk.


When you boot the computer, can you see a grub menu prompt?  Press escape to see the grub menu if you don't see it. Pick the recovery option and hit enter.

Try running

apt-get install ubuntu-desktop

from your prompt.  What happens?

---

### Post by deansuzi on 2006-04-27
i'm sorry, i have to keep toggling between my windows and ubuntu to do anything, so i have to constantly keep rebooting my computer...i am going to try what each one of you has said to do, and then see where we go from there...

---

### Post by deansuzi on 2006-04-27
actually i just did sudo apt-get update, and it worked...however, i'm still in the black and white command prompt screen with no graphics...i do get a grub menu prompt when i boot, but i am going to try what you recommend doing...thank you...

---

### Post by bbarrons on 2006-04-27
good...
apt-get install ubuntu-desktop
should then install or reinstall the desktop. 
after a reboot if all goes well then you should be at a graphical login page. not a command prompt. good luck.

---

### Post by deansuzi on 2006-04-27
i will go ahead and try what you say here. i began doing so, but i stopped...i'll give it a try. i got your message in my inbox...thanks.

---

### Post by mscman on 2006-04-27
I still think the problem is some sort of xorg conflict with drivers.  If (re)installing ubuntu-desktop doesn't work, try running:
```
sudo dpkg-reconfigure xserver-xorg
```
and work your way through the prompts.  When it asks you for the driver, just try choosing "VESA", unless you know exactly what driver your graphics card needs.  Feel free to pm me if you need any other info.

---

### Post by Luke771 on 2006-04-27
The short answer:

Bad hard drive.

The long answer:

I'm only guessing, but there is also some kind of thinking involved: if you have a bad hard drive, some critical files could be not readable, which could cause  the problem.

The story-of-my-life answer:

The exact same thing happened to me when I tried to install a "pure" Debian distro (not a Debian based one like Ubuntu).
I booted from the Debian CD, I followed the on screen instructions, I did the partitioning manually, completed the installation and rebooted.

Guess what?
I got stuck at prompt.

I could log in, but I couldn't start the graphical interface, I tried typing "startx" but all I got was "command not found"

Someone on another forum suggested that maybe I installed a Debian version without Xwindows, but I knew I had the latest version from the official Debian website, and that came with X.

So I got tired of that, formatted the Linux partition and installed Ubuntu the exact same way I installed Debian before and everything went fine.

After booting Ubuntu a couple of times, I was getting error messages during the boot sequence, I was able to recover another couple of times and keep running, but eventually it went all FUBAR and I had to renistall.
Once
Twice
and "trice"

Then someone on this forum pointed out that I shouldn't be reinstalling all the time and suggested a command line to check the state of the hard disk (sorry I forgot that line, if I was good at lines I would be an actor and make millions).

Comes out that I had a bad hard drive, with multiple bad sectors.
I got a new drive, installed it, reinstalled Ubuntu and no problems since then (OK, not that kind of problems).

I didn't try to reinstall Debian, but when I saw that someone got with Ubuntu the same problem I had with Debian, I started to write this answer just to say that the same thing happened to me  with a close relative to Ubuntu, and half way into the writing it hit me. 
Maybe that disk problem I had was causing the problem then, so it could be something like that causing the same problem now.
To confirm that theory I should reinstall Debian from the same CD and get the graphical interface to work, and I don't think I'm going to do that (I don't have any extra partition available and I don't feel like installing operating systems right now)

---

