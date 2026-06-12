---
title: "Startup programs not starting"
date: 2009-12-08
forum: General Help
---

### Post by lieberb on 2009-12-08
Hi all,

On ubuntu 9.10 with all upgrades. After a recent daily upgrade, my startup programs stopped working. I now have to run nm-applet, gnome-volume-control-applet and gnome-power-manager after each startup. I've tried unchecking, rebooting, and rechecking these options in system>preferences>startup applications to no avail. 

Thanks for any help!

-Ben

---

### Post by gettinoriginal on 2009-12-08
under start up apps, have you tried the options tab and "remember running applications".

---

### Post by lieberb on 2009-12-08
Thanks gettinoriginal, 

I don't really want it to remember applications I happen to have running at shutdown, only startup the ones I have selected as startup applications. I actually don't think this would help in anycase because it just doesn't seem to be reading from the startup prefs at all.

---

### Post by gettinoriginal on 2009-12-08
I would start the apps you want to run at startup, choose the remember apps option then reboot, Then uncheck the remember option and see if they stick.

---

### Post by yzf600 on 2009-12-09
I have the same issue. I think they worked for a while after the upgrade, but now they don't. 

The suggestion of using the "remember currently running application" button does not work. In fact, when I click that button, it kills the Tomboy panel icon. The binary is still running, but the panel icon disappears. 

I have also tried deleting my .gnome, .gnome2, .gconf, .gconfd & .metacity directories, but the problem persists. Also tried to delete the ~/.config dir. No luck. 

I really hate to wipe my entire home directory and start from scratch to fix this silly issue. Is there some logfile where gnome shows status that I could look at to debug the issue further?

---

### Post by yzf600 on 2009-12-15
Adding more data to what is known...

I have nomachine NX server installed on my box. When I login remotely via NX, my start-up applications start like they are supposed to.

---

### Post by philinux on 2009-12-15
> **lieberb said:**
> Hi all,

On ubuntu 9.10 with all upgrades. After a recent daily upgrade, my startup programs stopped working. I now have to run nm-applet, gnome-volume-control-applet and gnome-power-manager after each startup. I've tried unchecking, rebooting, and rechecking these options in system>preferences>startup applications to no avail. 

Thanks for any help!

-Ben

Try reinstalling ubuntu-desktop from synaptic.

---

### Post by yzf600 on 2009-12-15
> **philinux said:**
> Try reinstalling ubuntu-desktop from synaptic.

That didn't fix the issue for me. Thanks for the suggestion, though.

---

### Post by philinux on 2009-12-15
Try creating a new user with admin rights. See if that user works as it should.

---

### Post by john newbuntu on 2009-12-15
Just to rule out permission issues, please check the permissions of files in the following directories:
/etc/xdg/autostart/
and
~/.config/autostart/
In the first directory, you should see files like *.desktop owned by root with permission 644. Example:
-rw-r--r-- 1 root root 467 2009-11-28 19:46 at-spi-registryd.desktop

In the second, the files should be owned by the user with permission 644.  My guess is that the settings in .config override the one in /etc/.
Now when you create your own startup script, it should end up in ~/.config/autostart.  If you edit that script, you should have the line:
X-GNOME-Autostart-enabled=true

Where I am trying to get at here is a workaround.  If a daemon is not autostarting by itself, you could just save it with a different name or comment in your startup options.  You can then make sure that the X-GNOME-Autostart-enabled=true is set in that desktop configuration file.

---

### Post by yzf600 on 2009-12-15
> **john newbuntu said:**
> Just to rule out permission issues, please check the permissions of files in the following directories:
 
and
~/.config/autostart/
In the first directory, you should see files like *.desktop owned by root with permission 644. Example:
-rw-r--r-- 1 root root 467 2009-11-28 19:46 at-spi-registryd.desktop

In the second, the files should be owned by the user with permission 644.  My guess is that the settings in .config override the one in /etc/.
Now when you create your own startup script, it should end up in ~/.config/autostart.  If you edit that script, you should have the line:
X-GNOME-Autostart-enabled=true

Where I am trying to get at here is a workaround.  If a daemon is not autostarting by itself, you could just save it with a different name or comment in your startup options.  You can then make sure that the X-GNOME-Autostart-enabled=true is set in that desktop configuration file.

My permissions were all set correctly. However, none of the files under /etc/xdg/autostart/ or ~/.config/autostart/ have the line  X-GNOME-Autostart-enabled=true in them. 

I decided to move my home dir to a backup copy and made a fresh new one. After logging into gnome, none of the startup apps ran still. I switched back to my old home dir since that didn't help any. 

BTW - one thing to note is my home dir is on an NFS mount dictated by autofs/ldap.

---

### Post by whyohwhy on 2009-12-15
Same issue with me.  Mine happened right after I did and upgrade using Synaptics.  For me VLC doesn't start.  It was working fine 2 days ago while I was running 9.10 then kapow after a typical update.  I wish I knew which package broke it.  

I don't believe it is permissions setting.

---

### Post by 3rdalbum on 2009-12-15
It sounds like Gnome is starting as a Failsafe session.

At the login screen, type or select your username. At the bottom of the screen you will see a popup menu with "Session:". Select GNOME as the session. Continue to log in and your startup programs should work again.

---

### Post by SuperGrouper on 2009-12-16
I've been having this same problem- the network manager, volume control and power management applets aren't starting up at startup since around the time I upgraded to the latest distro. :(

I was worried that I'd broken something somehow, but if others are having this problem, is it some sort of bug? :?

---

### Post by yzf600 on 2009-12-16
> **3rdalbum said:**
> It sounds like Gnome is starting as a Failsafe session.



You were right, I was logging in via gnome failsafe session. I forgot I had to do that a week ago because compiz was making gnome unusable after login. 


I feel like such an idiot.

---

### Post by SuperGrouper on 2009-12-16
> **yzf600 said:**
> You were right, I was logging in via gnome failsafe session. I forgot I had to do that a week ago because compiz was making gnome unusable after login. 


I feel like such an idiot.

Apparently, the issues I was having with the system tray were caused by that same problem.  I just tried logging out and sure enough, I had been logging in under failsafe.  I don't even remember setting it to that...

Thanks for solving my problem, guys- I've logged in normally now and everything appears to be peachy. :)

---

### Post by 3rdalbum on 2009-12-17
You're welcome, glad I could help.

---

### Post by effbiae on 2009-12-28
hi 3rdalbum,

my kid was fiddling with the login screen this morning.  and - you guessed it - changed default login mode to "gnome safe".  i watched him do this and made a mental note to check it later.  i've got the memory of a goldfish :)

thanks for your insight into the problem!


jack

--
nm-applet --sm-disable 
network icon
network notification
network manager
network manager applet
panel

---

### Post by ismooth on 2010-01-04
the same problem happened to me, but regular gnome session was not the answer. still my programs are not starting up during boot.

furthermore, after that recent upgrade, grub menu started appearing, and now i gotta choose which kernel to boot into (in the meantime I removed older kernels, but still got the menu appearing).

any suggestions?

---

### Post by ismooth on 2010-02-04
anybody got any ideas?   :(

---

### Post by bhagwad on 2010-03-28
Turning off Gnome failsafe worked for me.

But initially I didn't know what failsafe was. So for those in the same boat, when you log out (not shut down), there's an option in the login screen at the bottom which allows you to select failsafe or not.

Thanks again for helping me solve this problem :)

---

### Post by Jaginus on 2011-01-30
Hi guys,

Thank you SO MUCH for the help !!!!

I was getting crazy looking for permissions, executions and all the stuff. I was starting in "failsafe" with automatic login and never realized it.

You are the best !!! ;)

---

### Post by ex-oficio on 2012-02-17
thank you so much for the failsafe suggestion. ive just deleted and re-entered all the things in my statup applications one by one in desperation, and then read this thread. 

lo and behold i had failsafe selected at login.

i may have reinstalled if it weren't for this thread.

cheers

---

### Post by oldos2er on 2012-02-17
Closed, necromancy.

---

