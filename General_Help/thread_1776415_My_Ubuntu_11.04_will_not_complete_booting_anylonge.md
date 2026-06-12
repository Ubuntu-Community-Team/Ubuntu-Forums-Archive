---
title: "My Ubuntu 11.04 will not complete booting anylonger?"
date: 2011-06-06
forum: General Help
---

### Post by nickforsberg on 2011-06-06
Hi everyone,

As of this morning I am no longer able to use Ubuntu on my computer (Acer laptop).

I have been running Ubuntu 11.04 with very good results up until this morning, when all of a sudden when I turned on the computer power it loaded a different login screen that I am used to (much simplier in design than the regular one).

Anyways, I entered my password and hit login. After some time my background image appears, and the mouse cursor is visible as "Waiting/Loading" on top of it. And that's it! Ubuntu will not get any further than this and the only thing I can do now is to turn off the power with the button on the computer.

On the login screen I am not able to choose another account than my own account. I know I tried to install a login screen called GDM or something, because I wanted to customize it, but the GDM was not successfully installed - could this be the cause of why I see a very simple login screen all of a sudden?

I am able to choose session type though, and I have tried with all different sorts (User defined session, Ubuntu, Ubuntu Classic, Ubuntu Classic (No effects), Safe mode, Recovery Console) but always the same result (only goes to the point where it loads my background and the mouse cursor in Waiting/Loading state).

My setup is like following:

- Ubuntu 11.04
- Running Ubuntu Classic with Compiz and some GUI tweaks



How can I proceed? I hope I do not have to reinstall Ubuntu entirely!??


THank you all in advance for helping me out! And PS! I am kind of novice when it comes to Linux...

---

### Post by nickforsberg on 2011-06-06
Update:

I am now able to start the terminal. I think I hit the keys Ctrl+Alt+F1/F2 or something while my background was visible.

But I have no idea... But anyways I am able to go to the terminal.
And I tried the "sudo apt-get update" and at the end it gives me errors about gdm2setup:

Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/natty/main/source/sources](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/natty/main/source/sources) 404 Not found
Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/natty/main/binary-i386/Packages) 404 Not Found

---

### Post by nickforsberg on 2011-06-06
Allright guys... I have solved it!

I ran this command:
sudo dpkg-reconfigure gdm

and I choosed gdm as my default window manager, and now it runs the correct login screen and after logging in my desktop boots up correctly.

Issue solved (for now!).

---

