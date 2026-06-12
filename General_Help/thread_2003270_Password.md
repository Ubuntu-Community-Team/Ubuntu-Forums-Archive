---
title: "Password  ??"
date: 2012-06-13
forum: General Help
---

### Post by dritchie on 2012-06-13
When installing 12.04 it asked for a password...
Now I need to enter the password every time I start the computer,
or when I leave the computer for more then a few minutes.
Is there a way to turn "password" off so it will stay off?

Thanks

Don

---

### Post by drs305 on 2012-06-13
To disable the 'screen lock', click the settings button upper right or in DASH type "Lock" and click the Brightness & Lock icon.

Turn the 'lock' off, and on the same page you can also disable the PW for returning from suspend.

For initial login, type "Login" in Dash and you can disable initial login from the User Accounts page.

---

### Post by raja.genupula on 2012-06-13
In your Unity dash type as "user accounts" ans select it . Now select your on the account list and enable the switch of automatic login .

for lock screen 
[http://superuser.com/questions/71465/how-to-disable-screen-locking-after-sleep-on-ubuntu-9-10](http://superuser.com/questions/71465/how-to-disable-screen-locking-after-sleep-on-ubuntu-9-10)

in the above link look at the 2nd solution . 1st solution not going to work .

---

### Post by sammiev on 2012-06-13
> **drs305 said:**
> To disable the 'screen lock', click the settings button upper right or in DASH type "Lock" and click the Brightness & Lock icon.

Turn the 'lock' off, and on the same page you can also disable the PW for returning from suspend.

For initial login, type "Login" in Dash and you can disable initial login from the User Accounts page.

I always change my setting here to never so I can watch movies and so on. :)

---

### Post by greenpeace on 2012-06-14
> **sammiev said:**
> I always change my setting here to never so I can watch movies and so on. :)

It's offtopic, but video players I use (VLC, Totem Movie Player) all block the screensaver from coming on while they are playing videos... so there should be no need to disable the screensaver for that reason.

---

### Post by sammiev on 2012-06-14
> **greenpeace said:**
> It's offtopic, but video players I use (VLC, Totem Movie Player) all block the screensaver from coming on while they are playing videos... so there should be no need to disable the screensaver for that reason.

I had to as it would lock the screen while the kids were watching a video, if they did not shake the mouse quick enough. Then I would need to unlock the screen with the password.

---

### Post by ecsk on 2012-06-14
I have a slightly different problem. I've set 'automatic login' to ON

When my ubuntu 12.04 is booted up, and automatically logged in. I get the following messages and ask me to enter my password.  Is there anyway to remove these message ????
> Unlock login keyring

Enter password to unlock your login keyring

The login keyring did not unlocked when you logged into your computer

---

### Post by naknak987 on 2012-06-14
caffiene makes disabling and enabling the screen saver easy and convenient.

---

### Post by drs305 on 2012-06-14
> **ecsk said:**
> I have a slightly different problem. I've set 'automatic login' to ON

When my ubuntu 12.04 is booted up, and automatically logged in. I get the following messages and ask me to enter my password.  Is there anyway to remove these message ????

Open up Passwords in DASH. Right click on Passwords:login and select Change Password. Enter your old password and leave the new and confirmation entries blank, the OK.  

Usual disclaimer about security and removing passwords (but I've done the same on my home machine).

---

### Post by asensio on 2012-06-16
Sorry drs305, I have the same problem as ecsk, but I can't understand the solution you posted...

"Open up Passwords in DASH"? I have no program/command called "passwords"

Could you be more specific?

Thanks and cheers
**ASENSIO**

---

### Post by drs305 on 2012-06-16
> **asensio said:**
> Sorry drs305, I have the same problem as ecsk, but I can't understand the solution you posted...

"Open up Passwords in DASH"? I have no program/command called "passwords"

Could you be more specific?

Thanks and cheers
**ASENSIO**

The HOME/DASH is the upper left button on 12.04. If you click it and start typing *passwords* the icon for "Passwords & Keys" should appear. If you can't use DASH in a terminal type:
```
seahorse
```

---

### Post by asensio on 2012-06-16
Thanks drs305,

I typed "passwords" and my dash gave me nothing... ok, you meant seahorse. I got it :)

cheers

---

