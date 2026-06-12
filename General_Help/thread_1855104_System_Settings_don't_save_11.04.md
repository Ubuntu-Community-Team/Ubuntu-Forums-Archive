---
title: "System Settings don't save 11.04"
date: 2011-10-05
forum: General Help
---

### Post by brightJoker on 2011-10-05
So far have only two issues in 11.04:
1. Boot splash is broken.  Worked fine after install, however, after updates, displays loading text rather than the Ubuntu boot splash.  Minor, so not too worried about it, would appreciate a point towards a fix though.  Yes I know the boot is slightly faster without the splash, but I like the splash :)

2. The bigger problem is my system settings/preferences don't seem to save/ are inconstant. Oddly, they sometimes are recognized, but other times are not.  For example:  I choose to use two-finger scrolling vs. edge, however it seems to revert to edge everytime.  I also have Touchpad Indicator installed, as I usually use a USB mouse, those settings I have to reset everytime I log in also.  My compiz settings save, and so does everything else.  Any help would be awesome!  Thanks for this great community/OS!

EDIT:  So just logged and my compiz settings weren't saved from before, but the Touchpad Indicator settings were...
I also forgot to mention a third issue: My swap doesn't seem to be recognized/used.  I encrypted my HD during install, so under fstab, it says swap is */cryptswap1, however in conky, it shows no activity from swap.

---

### Post by 3Miro on 2011-10-05
My guess is that both are due to the same bug. There seems to be an issue when using encrypted home folders on 11.04, for me the home folder will not always unlock properly. If so, then you will not be able to save files and hence you will not be able to save your settings. When you encrypt your home folder, the system also tries to encrypt your swap, and if this doesn't open properly, you will be unable to use swap and the splash screen may be crashing to show the swap error message.

I am not sure what the fix is. I hope 11.10 will fix the problem.

---

### Post by brightJoker on 2011-10-05
I guess my next question then is, is it worth keeping the encryption?  And if not, is there a way to decrypt without reinstalling?

---

### Post by 3Miro on 2011-10-05
> **brightJoker said:**
> I guess my next question then is, is it worth keeping the encryption?  And if not, is there a way to decrypt without reinstalling?

That depends. Encryption is the only thing that can stop a person from accessing your personal information if you lose possession of your laptop. I am a bit split on the question.

You can set up encrypted folders instead of encrypting all of /home, but it requires more work.

I am not sure how to decrypt the home folder. You can backup all of your files, then create a new user (without encryption) and remove the old user (deleting the old /home/old_user).

---

### Post by brightJoker on 2011-10-05
I'm fairly protective of my laptop, so I don't believe anyone would get their hands on it physically, does the encrpytion help from online attacks?  I've never had anyone try to get into my system, so I'm not too concerned about that either...The biggest thing is not having my settings saved.  I can live with no boot splash haha.  The swap worries me too though.

---

### Post by garvinrick4 on 2011-10-05
> 1. Boot splash is broken.  Worked fine after install, however, after  updates, displays loading text rather than the Ubuntu boot splash.   Minor, so not too worried about it, would appreciate a point towards a  fix though.  Yes I know the boot is slightly faster without the splash,  but I like the splash :smile:
Go into Synaptic and install plymouth themes that you want as choices. Make sure they
say themes.
Then open a terminal and:
```
sudo update-alternatives --config default.plymouth 
```
Choose which theme by number.
Then:
```
sudo update-initramfs -u
```
Will now have the plymouth theme you have choosen.

---

### Post by 3Miro on 2011-10-06
> **brightJoker said:**
> I'm fairly protective of my laptop, so I don't believe anyone would get their hands on it physically, does the encrpytion help from online attacks?  I've never had anyone try to get into my system, so I'm not too concerned about that either...The biggest thing is not having my settings saved.  I can live with no boot splash haha.  The swap worries me too though.

Ecryption offers zero protection from an outside attack. Assuming that someone manages to remotely gain root access to your machine while the machine is working, then the HDD is already decrypted and they can access whatever they want. It is also possible to break the encryption if they simply gain access to the machine while it is still running (the encryption key is saved in RAM).

The only time that encryption offers protection is if you have  your laptop turned off and someone steals it. Then they will be unable to access anything on it.

---

### Post by brightJoker on 2011-10-06
@garvinrick4

Awesome! Thank you for that!

@3miro

Thanks for all the wise words :) created a new user with no encryption, everything is working as it should now :)  Hope they fix that in 11.10 though, always better to have more security than necessary.

---

