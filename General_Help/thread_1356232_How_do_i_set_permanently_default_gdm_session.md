---
title: "How do i set permanently default gdm session?"
date: 2009-12-15
forum: General Help
---

### Post by mehepsk on 2009-12-15
Hi,

I have searched everywhere for an answer, but cannot find any that actually works.. What I have tried is basically to manually edit the ~/.dmrc to use XBMC session, both for my local user and for root, but it keeps getting overwritten when I do service gdm restart and then I end up in gnome again..   (I have also tried with sudo chattr +i .dmrc and it stays untouched, but I still keep ending up in gnome if I restart gdm from gnome) 

So I need to set a permanently default gdm session so it doesn't just take me back in to the last used session..

What I basically want to achieve is;

Computer boots into xbmc-standalone. I press a button on the remote and the gdm login manager comes up and I can press the button again to restart gdm and then return into xbmc, OR type in password and select gnome to use gnome. When I'm done in gnome, I want to press the same button on the remote to restart gdm and jump right into xbmc.

I have achieved this on a different computer I have and it works perfectly, but I just cannot figure out what I did to set the default session in gdm permanently to xbmc...   And no I don't want to set gnome as a one-time session every time. :p



And a little side question; 
Is there a better/more suitable login manager/theme that can give me more control with my remote? Situation now: I have to press my username, then enter my password and then select gnome as the session to use and then log in to use gnome. What I want: Have the two sessions (xbmc without password and gnome with password) as two buttons on the login screen so it is possible to drop the mouse and keyboard for everything except the password? (and of course still auto-login to xbmc so I have to kill xbmc to actually see the login manager)



Thanks in advance!


EDIT: I'm using ubuntu 9.10 Karmic :)

---

### Post by mehepsk on 2009-12-15
I just don't understand this... Suddenly after hours and hours of searching and trying to fix this it just works?

The only thing I can think of that might have fixed is was the chattr +i .dmrc and a reboot...    All other changes I have done during this time has been reverted (Well atleast I think so..).

I don't dare trying to change anything to find out what fixed it! :p

---

