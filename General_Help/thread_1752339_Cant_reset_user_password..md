---
title: "Cant reset user password."
date: 2011-05-07
forum: General Help
---

### Post by Autumn_Glitch on 2011-05-07
I was given an old computer running Ubuntu but the guy that gave me the computer didn't know the user name or password. So I booted into full root shell and did 
[COLOR="Green"]ls /home[/COLOR] 
and the computer responded with 
[COLOR="Green"]mskbx[/COLOR]
I then did 
[COLOR="Green"]passwd mskbx[/COLOR]
and it responded with
[COLOR="Green"]passwd: unknown user mskbx[/COLOR]
Any idea's?
I'm kind of a Ubuntu novice so please talk to me like I'm a child.

---

### Post by wilee-nilee on 2011-05-07
> **Autumn_Glitch said:**
> I was given an old computer running Ubuntu but the guy that gave me the computer didn't know the user name or password. So I booted into full root shell and did 
[COLOR="Green"]ls /home[/COLOR] 
and the computer responded with 
[COLOR="Green"]mskbx[/COLOR]
I then did 
[COLOR="Green"]passwd mskbx[/COLOR]
and it responded with
[COLOR="Green"]passwd: unknown user mskbx[/COLOR]
Any idea's?
I'm kind of a Ubuntu novice so please talk to me like I'm a child.

Install over it, you don't want their personal operating  system and account am I right?

You have to understand the interpretation on us getting you in, the info is all over the web, on how to do it.

---

### Post by aysiu on 2011-05-07
It sounds as if they deleted the user account without deleting the actual home folder.

I agree that you should just reinstall. It takes all of about 30 minutes.

Barring that, you can reset the password by booting into recovery mode:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Autumn_Glitch on 2011-05-07
> **aysiu said:**
> It sounds as if they deleted the user account without deleting the actual home folder.

I agree that you should just reinstall. It takes all of about 30 minutes.

Barring that, you can reset the password by booting into recovery mode:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
I have actually tried to install over it. For some reason when the computer starts to load the live disk it goes to a white screen and stops doing anything. 
Also the method for resetting the password you posted is the method that I tried. are there any other methods for resetting things?
I would even settle for an explanation of the white screen during the attempted instillation. Any help is appreciated.

---

### Post by wilee-nilee on 2011-05-07
> **Autumn_Glitch said:**
> I have actually tried to install over it. For some reason when the computer starts to load the live disk it goes to a white screen and stops doing anything. 
Also the method for resetting the password you posted is the method that I tried. are there any other methods for resetting things?
I would even settle for an explanation of the white screen during the attempted instillation. Any help is appreciated.

May be that a graphic driver is needed, power on the computer, hit the shift key and hold it down to get to a gui of chocies, try ubuntu, install, test memory etc. hit the f6 key mark nomodeset then boot from there.

If this gets you in; install, then on reboot if the same thing happens, follow the shift key procedure to the grub menu choose recovery then at the choice gui choose the failsafe-safeboot, these are all low graphic boot-ins.

So if your installed and you have needed this method to get in; go to menu systems-admin-additional drivers see if anything is there for installation.

The actual install may set you up, so try a reboot to just the install, after installing first.

---

### Post by Autumn_Glitch on 2011-05-08
> **wilee-nilee said:**
> May be that a graphic driver is needed, power on the computer, hit the shift key and hold it down to get to a gui of chocies, try ubuntu, install, test memory etc. hit the f6 key mark nomodeset then boot from there.

If this gets you in; install, then on reboot if the same thing happens, follow the shift key procedure to the grub menu choose recovery then at the choice gui choose the failsafe-safeboot, these are all low graphic boot-ins.

So if your installed and you have needed this method to get in; go to menu systems-admin-additional drivers see if anything is there for installation.

The actual install may set you up, so try a reboot to just the install, after installing first.

This sort of worked.I got to the main live disk screen but the computer overheats and shuts down in the middle of the installation process every time I run it. Now I can't even get an operating system on the computer. **I really should have just stuck to trying to reset the password instead of doing a complete reinstall. **

---

### Post by Buntumatic on 2011-05-08
What do you mean overheats. Clean the dust out. Reseat RAM module(s). Downclock if needed, downclocking the CPU and RAM can give old computers new life.
You should have created a new user, not trying to restore some deleted user.

---

### Post by Autumn_Glitch on 2011-05-09
> **Buntumatic said:**
> What do you mean overheats. Clean the dust out. Reseat RAM module(s). Downclock if needed, downclocking the CPU and RAM can give old computers new life.
You should have created a new user, not trying to restore some deleted user.

Creating a new user is a great idea actually. If I had known it was possible I would have attempted it but its to late now.

Thanks for the advice about downclocking, I will do some research about it and once I make an attempt at doing it I will post the results. It looks like its the type of thing that may take me a while to understand enough to attempt it.

---

