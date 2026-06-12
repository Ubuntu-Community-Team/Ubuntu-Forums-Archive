---
title: "adding user"
date: 2011-11-12
forum: General Help
---

### Post by Quarkrad on 2011-11-12
running 10.10 - I have added (obvious not correctly) a new user to my brother-in-laws dual boot PC which I'm doing remotely. The existing user is **tony** and the new user is **dom**. It appears the grub screen (actually not grub - I'm using burg) offers Ubuntu or Windows which is what I expected.  When the pc is left to time out to the Ubuntu option the pc boots to the original user **tony**.  I was expecting a screen that would show both user icons with the choice to choose.  Any advice would be appreciated - I have set the new user **dom** up via the gui, System/Admin/Users & Groups.

---

### Post by WasMeHere on 2011-11-12
Hi Quarkrad,

In Users and Groups make it ***ask for password at login*** for all users (also for tony)!

Have fun finding out :-)
Olle

---

### Post by Quarkrad on 2011-11-12
Thanks - a bit closer.  In system/admin/users & groups the original user **tony** had an **Account Type** of **custom**.  I changed this to Admin (both **tony** and **dom** are now **Admin**) and when in **tony** desktop I can log out - be presented with the expected window giving a choice of **tony** or **dom** and log into **dom**. Great.  The only issue is that on reboot the pc goes straight into **tony** - there is no choice.  Can both users be set as Administrator?

---

### Post by WasMeHere on 2011-11-12
My advice is 'In Users and Groups make it ask for password at login for all users (also for tony)!'

Your problem is the opposite of the following thread
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1875876_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1875876")

Maybe you can pick up some idea from there :-)

---

### Post by Quarkrad on 2011-11-12
Ah... what is happening to my beloved Ubuntu?  Surely having more than one user is not too much?  I did what you say but still not joy.  I deleted dom via the gui and tried again using terminal commands.  **sudo useradd -c dom -m -s /bin/bash dom**  and it did install **dom**.  I went to system/adim/users & groups and there he was.  But on reboot I still go straight into **tony**.

---

### Post by WasMeHere on 2011-11-12
> **forestpiskie said:**
> Perhaps have a look in the conf file and edit it manually if necessary.

cat /etc/lightdm/lightdm.conf

I did it manually in xubuntu and added

autologin-user=hobgoblin
autologin-user-timeout=0

to the file. Looks to be the same file. I also got rid of the guest while I was at it ... 

allow-guest=false

Edit - trying it out in vbox - changing it via the GUI appears to add the autologin-user=hobgoblin line but not the timeout.

Did you try to reverse the above from the thread I suggested? Edit the file as superuser!```
sudo nano /etc/lightdm/lightdm.conf
```

---

### Post by Quarkrad on 2011-11-12
Sorry - no I didn't do that part.  I've opened up lightdm.cong and it's an empty file.  Should I add and save the following?

autologin-user=tony
autologin-user=dom
autologin-user-timeout=10


would this give me the option screen for 10 secs?  Something somewhere must be telling Ubuntu that either tony is the default user or to ignore dom.

---

### Post by WasMeHere on 2011-11-12
I had expected that file to contain at least
[FONT="Courier New"]autologin-user=tony[/FONT]
so now I don't know, but try what you suggested :-)

After that you can look for that 'slider' to toggle automatic login in the GUI for Users and Groups.

---

### Post by Quarkrad on 2011-11-12
This is odd to me (newbie!).  when I sudo nano /etc/lightdm/lightdm.conf  I get a blank window/empty file.  I enter the commands e.g. autologin...=tony etc  and then press Ctrl X followed by Y to save the file.  Then I'm told [error writing /etc/lightdm/lightdm.conf: No such file or directory ].  I had a look via gksuo nautilus (could I edit the file there?) and there is no folder called lightdm in /etc/

---

### Post by Quarkrad on 2011-11-12
I've just added a new user in Ubuntu 11.10 (using virtualbox in my PC) and the same thing.  You can log in an out once you are in but rebooting always goes to the first account setup.  Surely this is not right.

---

### Post by WasMeHere on 2011-11-12
> **Quarkrad said:**
> This is odd to me (newbie!).  when I sudo nano /etc/lightdm/lightdm.conf  I get a blank window/empty file.  I enter the commands e.g. autologin...=tony etc  and then press Ctrl X followed by Y to save the file.  Then I'm told [error writing /etc/lightdm/lightdm.conf: No such file or directory ].  I had a look via gksuo nautilus (could I edit the file there?) and there is no folder called lightdm in /etc/
Try ```
sudo mkdir /etc/lightdm
``` to create that directory!

---

### Post by WasMeHere on 2011-11-12
> **Quarkrad said:**
> I've just added a new user in Ubuntu 11.10 (using virtualbox in my PC) and the same thing.  You can log in an out once you are in but rebooting always goes to the first account setup.  Surely this is not right.
Unless it works very soon, I will agree that something is wrong, probably because 11.10 is new and not yet debugged.

Have you been running previous versions of Ubuntu? In that case, maybe you can consider going back to whatever version you were using, or the long time version [KLX]ubuntu 10.04?

---

### Post by Quarkrad on 2011-11-12
Sorry - I've been confusing, apologies.  The remote system (brother-in-laws) is 10.10 - actually the same as mine.  I have 11.10 on a virtual machine because another family member who I have converted to Ubuntu has to be on 11.10.  So -to confirm, I am talking about a 10.10 machine.  I created the directory and the lightdm.conf file is in here configured.  However, I'm still booting straight into tony - my first user.  (I had a look at dom in the home folder and the owner is dom).

---

### Post by WasMeHere on 2011-11-12
Do you have a program that can be called from the terminal
```
users-admin
```

Please post a ***screenshot*** of that, when 'looking at' the user tony!

Then I may see if there is a way to change the login behaviour.

By the way, I suggest that you clean your system by removing the file suggested by me.
```
sudo rm -r /etc/lightdm

```

---

### Post by Quarkrad on 2011-11-12
Olle Wiklund -thank you for all your help, much appreciated.  In the end I sorted it - as simple as System/Admin/Logon Screen.  A few changes and my problem was solved.  Thank you for your time and effort.

---

### Post by WasMeHere on 2011-11-12
Congratulations, you solved your problem yourself :-)

It is not easy to guess that there is a way to toggle automatic login in
'System/Admin/Users & Groups', but it is overridden by the setting in
'System/Admin/Logon Screen'.

Thank you for sharing!

Having fun finding out
Olle

---

