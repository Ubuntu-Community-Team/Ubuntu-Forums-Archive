---
title: "Songbird error message and Webcam question"
date: 2009-07-24
forum: General Help
---

### Post by xFlowx on 2009-07-24
*I have two questions. I might just start a new thread for the other one...if I need to.*

I'm fairly new to Ubuntu still, and I'm still not used to how you download and install things. Installing mainly, is a problem for me.

**First question: Songbird**
I just downloaded and installed Songbird, and keep getting the error message of "Could not launch 'Songbird' Failed to execute child process 'Songbird' (No such file or directory."

First, I downloaded it...and couldn't figure out how to install it...so then I found this: [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird) , and I used the script...
I know I did something wrong, of course, but I don't know how to install/uninstall/reinstall things on this Operating system (Ubuntu 9.04 Jaunty).

**Second question: My Webcam.** 

I have a Logitech QuickCam IM Plus. It's practically brand new, and I only used it for about a week before I switched operating systems...But I can't seem to install it. And when I said I was fairly new to Ubuntu, I meant I just started using it this month. I've been using it for about three and a half weeks...
How do I install the driver with the cd it came with? It had a little program that let me record things and snap pictures with.( I miss snapping pictures of me and my pet cat, lol.) Is there a way to use it on Ubuntu, or not?

But I use the webcam for video chatting with my friends and snapping fun pictures with. However, they all either run Macs or Windows, and I was wondering if there was a supported program I could get for it? Like Oovoo, or even a yahoo client that isn't Gyache...?

If I could figure out how to use Sun Virtual box or Wine, I could probably get things working. But I'm not very good when it comes to non-windows computers.




...If you read ALL of that, you get lots and lots of cookies. Thank you SO much for any and all help!

---

### Post by Greenwidth on 2009-07-24
In:
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

The deb section is by far the easiest way to install, its similar to an windows exe.
Download the appropriate deb for your system (32bit, 64 etc).
Double click to install.

To start it:
Applications > Sound and Video > Songbird

---

### Post by PGScooter on 2009-07-24
mmm I like cookies.

Well, for the webcam, some work "out of the box" meaning you don't need drivers. If you need drivers, then it could be a pain. Yes, there are several programs in ubuntu for recording pictures and movies. Try Cheese, for example.

I use skype and talk with video with my friends for hours without any problem. To install skype, open a terminal (click on applications>accessories>terminal) and type ```
sudo apt-get install skype
```. In the settings somewhere there is a way to test your camera.

---

### Post by xFlowx on 2009-07-24
> **PGScooter said:**
> mmm I like cookies.

Well, for the webcam, some work "out of the box" meaning you don't need drivers. If you need drivers, then it could be a pain. Yes, there are several programs in ubuntu for recording pictures and movies. Try Cheese, for example.

I use skype and talk with video with my friends for hours without any problem. To install skype, open a terminal (click on applications>accessories>terminal) and type ```
sudo apt-get install skype
```. In the settings somewhere there is a way to test your camera.

I never thought Skype would work. Thanks! But, when I tried to do that, it said it couldn't find the package....D: here's what it said: ```
flow@ubuntu:~$ sudo apt-get install skype
[sudo] password for flow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype

```

---

### Post by xFlowx on 2009-07-24
> **Greenwidth said:**
> In:
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

The deb section is by far the easiest way to install, its similar to an windows exe.
Download the appropriate deb for your system (32bit, 64 etc).
Double click to install.

To start it:
Applications > Sound and Video > Songbird


Thank you!! That worked and fixed iiit!

That was pretty easy to install. I'll keep in mind to use that way above anything else!

---

