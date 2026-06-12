---
title: "VirtualBox OSE USB drives"
date: 2010-01-10
forum: General Help
---

### Post by linden940 on 2010-01-10
Ok I am having alot of trouble with this. this is where i stand.

Main system Ubuntu 9.10 VB system is windows xp black

can not get USB drives to work i have tryed the following post.

[B> **LarryJ2 said:**
> 1.  IF USB device doesn't appear to the guest OS and is unavailable inside the guest  OS.

2.  and/or   IF In the Guest window, under Devices->USB Devices, your USB devices appear but are grayed out...

3.  Try this:
[LIST=1]
[*]
[*] In the host (Karmic 9.10 for example), System->Administration->Users and Groups  
[*]Click on the Keys Icon (to right of Help) and give your password.
[*]Select (highlight) your normal user line (the one with /home/xxx)
[*]Click Manage Groups.  
[*]In the Groups settings List Box, navigate down to vboxusers
[*]With vboxusers high lighted,  click properties
[*]Click the check box next to your normal user to indicate you want the normal user to be a member of the vboxusers group.
[*]reboot the host.
[/LIST]

Hopefully, your USB devices should be visible inside your guest OS.  For example, in XP,  my  USB flash drive  device appears in My Computer as KINGSTON (E:) inside XP.

Please note that you have to tell VirtualBox allow your USB device under Details -> USB/Device Filters, first.   Just click on the button Details Tab button USB,   check Enable USB controller then click the USB+ icon at the right and place a check by the USB device you want your guest to have access to.

Also note this applies to the Non-Open Source Version of virtual box (the one installed from the repository)  The version you can get directly from SUN allows USB devices to be ported through to the guest.  OSE version does not.

Another note: If you have your USB thumb drive mounted in the host (mine is Karmic) an Icon will appear on the desktop.   If you have successfully completed the steps above,  when you start the guest, the Karmic host desktop USB icon disaappears to later return when you shut down the guest! (That is so neat!  Bravo Ubuntu)

Yes, I can read your mind...  If I could run Quicken directly under Karmic,  I wouldn't need XP!!.  I'm totally Linux except for Quicken and Turbo Tax.

[/B]


I have tried to do this.

3.  Try this:
[LIST=1]
[*]
[*] In the host (Karmic 9.10 for example), System->Administration->Users and Groups  
[*]Click on the Keys Icon (to right of Help) and give your password.
[*]Select (highlight) your normal user line (the one with /home/xxx)
[*]Click Manage Groups.  
[*]In the Groups settings List Box, navigate down to vboxusers
[*]With vboxusers high lighted,  click properties
[*]Click the check box next to your normal user to indicate you want the normal user to be a member of the vboxusers group.
[*]reboot the host.
[/LIST]

but i am hitting a brick wall...there is no "vboxusers" in the list under the /home/xxx and there is not one under the root either so i tried the 2ed thing

Please note that you have to tell VirtualBox allow your USB device under Details -> USB/Device Filters, first.   Just click on the button Details Tab button USB,   check Enable USB controller then click the USB+ icon at the right and place a check by the USB device you want your guest to have access to.

But another brick wall...this dos not show up either so...more google and losing more hair as time keeps on ticking by i find this

Select "Install Guest Additions" from the Devices menu.
or if that doesn't work install the .EXE from the CD/DVD drive within the Guest OS.

and well what do you know? this dont work either

and so....someone help me keep my hair on my head an give me a hand?

---

### Post by AlexanderDGreat on 2010-01-10
Hey man, try to download the .deb package for Linux hosts / Ubuntu in virtualbox.org. The Vbox OSE doesn't support USB that's why it's not showing. I've also had the same problem before.

---

### Post by linden940 on 2010-01-10
Yea...just found out that bit of data...they should have that updated so that you would get the right ver and not have 2 do all of this crap..now i am trying 2 get old ver off 100% so i can get the right one....will post if works

---

### Post by howefield on 2010-01-10
One consolation is that you shouldn't lose any virtual machines that you have created.

Once you have the "correct" version of Virtualbox installed, it should just be a matter of putting the settings in place for them.

---

### Post by linden940 on 2010-01-10
ok now i got it installed...but cant find the shortcut 2 run it?

---

### Post by howefield on 2010-01-10
Might take a logout/login to see the menu icon.

You can start from terminal with (note the capitalisation)

```
VirtualBox
```

---

### Post by linden940 on 2010-01-10
Ok i got it...now lets get the usb to work

Thanks

---

### Post by linden940 on 2010-01-10
ok...i see USB drivers now...*about time* now...they are grayed out..so..one more bird 2 hit...

---

### Post by linden940 on 2010-01-10
can anyone help me on the usb being grayed out? i am still trying to get it fix but running into brick wall

---

### Post by howefield on 2010-01-10
Going back to your first post, did you manage to add your user to the vboxusers group ?

It's hard to tell if you got that bit done or not.

---

### Post by linden940 on 2010-01-10
yes..that i did that as well as added root *read else where root needs to be there as well* but all so tryed with out root

---

### Post by howefield on 2010-01-10
The only bit left then should be to create the filters for the devices. In settings for your virtual machine, under the USB tab, have you been able to create the filters ?

---

### Post by linden940 on 2010-01-10
yes

Enable USB Controller (checked)
Enable USB 2,0 (EHCI) Contoller (not checked)

in USB Device Filter i have 3 devices listed

---

### Post by linden940 on 2010-01-10
can u think of anything?

---

### Post by howefield on 2010-01-10
Only a reboot, unless you have already done that since adding your self to the vboxusers group ?

---

### Post by linden940 on 2010-01-10
sadly...yes i have...many times

---

### Post by linden940 on 2010-01-10
Ok....got it...tryed something someone else said on dif fourm and it worked.....this is what i had to do to make it work

sys - administration - users - and groups 

unlock and high light my id click onto manage groups found " lp " clicked on my name and root and loged out and loged back in...they said thats something to do with virtul box being able 2 "mount" or something...i am still learning and not a pro*

---

