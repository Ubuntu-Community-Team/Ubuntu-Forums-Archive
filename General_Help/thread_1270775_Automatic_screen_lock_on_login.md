---
title: "Automatic screen lock on login"
date: 2009-09-20
forum: General Help
---

### Post by jay3ld on 2009-09-20
Ubuntu 9.04

I had this working once, after searching for days around the net and testing.  I had to reinstall ubuntu as I screwed things up playing around with it.  Sadly, I didn't keep the file that I had which did this.  I have been searching for at least 4 hours now trying to get it working again, but no luck.

My ubuntu is setup do dual boot.  I setup windows to automatically restart just before midnight and my grub login automatically starts up ubuntu.  I have a automatic login setup to log me in and start an important application.
The problem is I need my screen locked for security.  The only reason I use automatic login is because I can't run this program in the background at the login screen.  It has a gui, but does things on its own once started.

I have read that anything which requires the gnome keyring manager, will prevent the hint of adding the "xdg-screensaver lock" command to my startup applications.  I have also tried the sleep 10 seconds then run the command trick and it doesn't seem to work.
I worked around the issue with me needing to put in my password after automatic login for my wireless connection.  I don't know if this relates to the issue of why the automatic screen lock won't work though.


Is there any solutions that work for 9.04 that can do this for me?   I would really like to add that layer of security, but keep the usability I need for the applications I run.

---

### Post by benpaka on 2009-10-08
I had the same idea for the same reason.

I found this tutorial for 8.10 [http://www.samlesher.com/ubuntu/ubuntu-auto-login-and-lock-screen](http://www.samlesher.com/ubuntu/ubuntu-auto-login-and-lock-screen) but it doesn't work for me in 9.04.
If you have found something could you write it here!!!

---

### Post by baldew.singh@versatel.nl on 2009-10-17
After enabling automatic login (System->Administration->Login Window tab Security) 
add the piece of code below to the .profile of the auto login user. The magic is done by starting gnome-screensaver before locking the screen. In Normal execution mode Ubuntu starts the gnome-screensaver AFTER execution of the .profile script. 
The code first tests whether or not we already have executed the lock command. If not, the var AUTOLOGIN is not set and the then branch will be executed. This will set the env var AUTOLOGIN to true. Subsequent exec of .profile will NOT result in locking the screen. 
The gnome-screensaver is started and the screen is locked immediately. The var AUTOLOGIN is set to true in order to prevent future locks during the entire life of this boot. 

Works perfect in jaunty. Not tested in other releases yet.  

if	[ !"$AUTOLOGIN" ] 
then 
	export AUTOLOGIN=true 
	gnome-screensaver 
	gnome-screensaver-command --lock 
fi

---

### Post by oroulet on 2009-11-09
I used to start xlock from my .xsession file but is a better solution. Thanks for the tips !!
I modified a bit the script to not run when login without X. I might 

#If this is gdm session force screen lock
if	[ "$GDMSESSION" ] ; then 
    if [ !"$AUTOLOGIN" ] ; then 
        export AUTOLOGIN=true 
        gnome-screensaver 
        gnome-screensaver-command --lock 
    fi
fi

---

### Post by lordL on 2009-12-12
Got this working perfectly on Karmic using baldew.singhs script.

Thanks a lot for the tip! :D

---

