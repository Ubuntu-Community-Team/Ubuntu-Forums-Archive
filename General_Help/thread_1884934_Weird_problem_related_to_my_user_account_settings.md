---
title: "Weird problem related to my user account settings?"
date: 2011-11-22
forum: General Help
---

### Post by Clupus on 2011-11-22
Hello everyone, I've got a strange problem on my hands.. strange as in "I don't really know where to begin look for solutions".

All of a sudden I'm having various problems:
[LIST]
[*]Unable to mount a drive by clicking on it within nautilus
[*]Firefox gives me an error message saying "The bookmarks and history system will not be functional because one of Firefox's files is in use by another application. Some security software can cause this problem."
[*]Strange soundproblems that comes and goes
[*]Unity stopped working
[/LIST]
There might be more, but this is what comes to mind right now.

Now, these problems doesn't really seem to have anything in common, right?
[LIST]
[*]The drive I can easily mount from command line with ```
sudo mount
```, but from within nautilus all I get is "Unable to mount drive Not Authorized".

[*]The problem with Firefox I tried fixing by following this: [http://support.mozilla.com/en-US/kb/The%20bookmarks%20and%20history%20system%20will%20not%20be%20functional](http://support.mozilla.com/en-US/kb/The%20bookmarks%20and%20history%20system%20will%20not%20be%20functional)
But that didn't work.

[*]I got Unity to work again by logging in to Unity 2D, and using ccsm to re-enable the "Ubuntu Unity plugin". Don't know why it was disabled, I sure didn't do it.

[*]The soundproblems I can fix by doing a 
```
killall pulseaudio
``` followed by ```
pulseaudio
```
[/LIST]
The only thing I can recall doing these last days is going into "User Accounts" and enabling "Automatic Login". Now, that doesn't work either, I still have to log in manually.
If I open "System settings" from the menu up to the right and open "User Accounts" I cannot do anything. The button for unlocking the settings is grayed out and it says "System policy prevents changes. Contact your system administrator."
The fun part is that if I open "System settings" from the unity menu to the left and click on "User Accounts" the window crashes.

OK, so I'm thinking this has something to do with my user, but I am logged in as I always have been, account type "Administrator".
I don't get it.

Help, please?

---

### Post by yehuda_moon on 2011-12-09
Same problem here.
Everything started when I enabled automatic login.
Sound problems, mounting problems and I can't even shut down my pc. Even if I select shut down it just logs out from my account.
The difference is that firefox works fine with no problems. Unity works fine too.

Help plz??

---

### Post by werever on 2011-12-15
Same problem here!, window "User accounts" have UNLOCK button disabled, and this message is displayed "system policy prevents changes"

my problem starts when I tried to enable automatic login  on 11.10

I followed instructions from here:

[http://www.liberiangeek.net/2011/09/enable-automatic-login-in-ubuntu-11-10-with-lightdm/](http://www.liberiangeek.net/2011/09/enable-automatic-login-in-ubuntu-11-10-with-lightdm/)

please note some comments added at the end: 

> Proceed with caution when doing this. When I followed the above procedure and rebooted, my computer hung at “Checking Battery State”. The fix is to get back into the desktop and remove auto-start

-ctrl-alt-f1 to a command prompt
-login
-”sudo lightdm start”
- gui-login
- follow procedures to disable auto-login

I am confused about this comment, any toughts?

Thanks!

---

### Post by farhanawan on 2011-12-15
Me too getting these types of problems, my keyboard stops working and files are opening and closing themself I just sitting and watching everything after 5 6 min all become ok,
I face this problem every after 30 40 mins :(

---

### Post by niteman on 2011-12-15
I am having a similar problem in that my issue started when I enabled auto login. Thing is, I cannot log in at all. When I get to the login screen where you select user account, it doesn't ask for a password and when I click on my user it goes into a loop at spits me right back to the login screen. I'm at a loss.

---

### Post by Snarfblat3000 on 2011-12-31
First post for me here.  I am a noob.  I've installed Ubuntu 11.10-64, running Unity, (fakeraid0).

I also had strange problems after enabling "auto logon" for my user account.    It took a long time to load the desktop, I couldn't shutdown or reboot from the GUI (it would just go to the login screen), sometimes the swap file partition would not mount.

In System-UserAccounts I couldn't make any changes, and the unlock button said "System Policy prevents changes, contact your System Administrator" (which is me).  The "Automatic Logon" was stuck "ON".

Here is what I did:

bill@ubuntu11:~$ sudo gedit /etc/lightdm/lightdm.conf

I changed this:

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
autologin-user=bill

To this:

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
autologin-user=

Saved and rebooted, logged in, went to System-UserAccounts and it's now unlocked.  I made sure Automatic Logon was turned off, and everything appears to be working OK now.

I hope that helps someone.  These forums have helped me immensely.  Thanks.

---

### Post by jmikii on 2012-01-28
Thanks, that worked for me also :) Thanks

---

### Post by mightyiam on 2012-11-19
I'm having [bug #1050437]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1050437"). Perhaps it is related. I didn't set up autologin, though.

---

### Post by wildmanne39 on 2012-11-19
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

