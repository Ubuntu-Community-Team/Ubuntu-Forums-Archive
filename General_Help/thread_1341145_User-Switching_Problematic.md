---
title: "User-Switching Problematic"
date: 2009-11-29
forum: General Help
---

### Post by pascat on 2009-11-29
Alright. I just installed Ubuntu 9.10 directly off the disk. 

First thing I did, is notice that Pidgin was replaced with something called ...Empathy? anyway, went into package manager and removed Empathy (which came with that Easy Switcher gnome applet) and then, did the security updates, installed xchat, thunderbird... 
Installed my fglrx graphics driver, and Wireless Networkcard after enabling the non-free repository, Google Gadgets....

When I rebooted, something happened: The Easy Switcher applet could not load anymore, giving me an error popup. 

Then, I made an account for sister (whom just drove over her laptop with her car... Blond behind wheels everyone :/) 
So, I setup the screensaver to lock the screen when its enabled. That worked.

Problem:
Trying to recover from the screensaver (hitting any keys) brings me with a black screen, without the Password or Switchuser prompt I was used to seeing. Though, typing in the password and hitting enter still works. (For info, I use that Matrix screen saver)

Problem 2: 
Going from System->Log Out-> Switch User often has me with the dialog I spoke of earlier (That one that is supposed to appear after screensaver) but I am unable to click on anything. (and sister does not -ever- do Keyboard commands) Again, Password and Enter works. 

Result:
If I want to switch from my account to hers, I have to actually LOG OUT.

Note: I'm using Compiz-Fusion with a few default settings (using Easy CompizConfig package) 


If anyone knows WTF is going on with this, I'd really appreciate.

---

### Post by pascat on 2009-11-29
Tried turning off Compiz, no change. 

And the reason the screensaver lockout is there, is to prevent sister from accessing my User Desktop and have to use Hers, when I'm being pulled off and don't have time to switch out. (aka, have to run off and leave the system as is) and I don't want her to come and close my windows :/ 

She has done that SO many times on windows its abusive :/

---

### Post by ac7ss on 2009-11-30
I am having a similar problem. I can switch using Gnome (the applet works there) but not from KDE. Even when the screen saver comes up to password, it doesn't give the option to change users. 

I use KDE and my wife uses Gnome. 

What system are you using? KDE or Gnome?

---

### Post by pascat on 2009-11-30
I use Gnome. 

I just found out also, hitting -Escape- brings up the dialog and makes it clickable, but I am unable to Switch users. ((I click the icon, and nothing happens... It should bring you back to User Login screen no?))

---

### Post by ac7ss on 2009-12-01
Make sure that you are using the GDM login manager. that seems to be my problem (I am using KDE with the GDM manager.)

---

### Post by pascat on 2009-12-01
How do I do that?

---

### Post by ac7ss on 2009-12-10
sudo apt-reconfigure gdm

This will allow you to choose the Login manager. You may have to close X to to this, I can't remember now.

---

### Post by pascat on 2009-12-10
> **ac7ss said:**
> sudo apt-reconfigure gdm
sudo: apt-reconfigure: command not found

---

### Post by john newbuntu on 2009-12-11
```
sudo dpkg-reconfigure gdm
```

---

### Post by pascat on 2009-12-11
did that. It didn't do much of anything.

---

### Post by john newbuntu on 2009-12-11
I'd suggest reinstalling "gdm". Open system->administration->synaptic package manager.  Hit reload and search for gdm. You should see version 2.28.1-0ubuntu2.1.  Now right click this and choose mark for reinstallation.  Then click on apply.
Also, use update manager and get all updates.  I am hoping all these would help you.

---

### Post by pascat on 2009-12-11
Been there, done that. 

I think the problem is GDM using openGL. So when I try to do Switch-User, (I read somewhere else) that it creates a new copy of the GDM in another terminal screen, but since graphics card don't allow two instances of openGL, it won't work. Thus, making the switch user crash and revert back to my screensaver.

Then, that would mean GDM is somehow setup to be using openGL (for Ubuntu's built-in Compiz) and whenever I enable the fglrx drivers, it won't work. 

I fixed the problem though, by uninstalling the driver, but now I can't benefit of 3D Acceleration. 

Of course, this is all theoretical ideas of what it could be based on what some people told me and so forth. 

If someone knows a way to make GDM stop using openGL without having to turn off the 3d acceleration, I'm all ears.

---

### Post by Gary_inNYC on 2010-09-09
This happens to me as well.  It's gotten to a point where my secondary user account lies dormant, since switching users just crashes my computer.

When it crashes from a user switch (I switch using the gui menus), the screen just acts crazy: the screen flickers, but mouse movements still work although not in a functional manner.  Nothing works in this state except for this superficial mouse pointer still responding.  Essentially switching users in Ubuntu for me is a nuke-my-system button that I currently stay away from.  

What DOES work correctly is logging out the current user, and logging in the other, and it's problem free.  This leads me to agree that the problem has something to do with having multiple users logged in simultaneously adversely affecting the gui.  Could be the compositing thing being restricted to one instance (I have compiz enabled), it sounds logical.  My specs aren't spectacular (thinkpad t40 w/ 7500m radeon video).  

- Gary_inNYC

---

