---
title: "cannot login to ubuntu 12.04 - after restart it started requesting a login"
date: 2012-06-15
forum: General Help
---

### Post by wgregori on 2012-06-15
I can no longer login to my ubuntu machine.  Here's what happened:

my colleague had to do a hard restart on my system

now it boots and presents me with a login prompt (never did before.. it just logged me in automatically)

when I type in my password the system seems like it starts the login process then bounces back to the login screen.  It does the same thing when I try to login as a guest.

I booted into recovery mode and dropped into a terminal window where i reset my login password.  Still not luck.  

Any ideas?

Thanks,
Wayne

---

### Post by iqtedar on 2012-06-15
I suspect you might be using lightdm as your login  manager. At the login screen, get to another console (tty) such as by pressing alt+ctrl+f1 and enter 'sudo service lightdm stop'. Then do 'sudo service gdm start'.  This should bring up the gdm login manager from which you should be able to login without any problems. Let me know what happens.

---

### Post by imachavel on 2012-06-15
don't forget your password. If you reset it and can't use your log in and password, definitely a weird issue is going on. I'd take iqtedar's
advice.

Beyond that I don't know

---

### Post by wgregori on 2012-06-15
I did follow the instructions to stop lightdm and start gdm... when I issue the command "service gdm start" the system tries to go into graphical mode... but the little "half and orange" just spins in on the screen... pressing ctrl-alt F1 goes back to terminal mode... F7 back to the spinning orange.

closer to a rebuild... :(

---

### Post by wgregori on 2012-06-15
I thought that I'd mention that I successfully created a new account and I have the same problem... the system will not allow me to login to the new account.

---

### Post by iqtedar on 2012-06-15
Some things to try:

Can you login into safe graphics mode?
Can you get into rescue mode and enter startx?

Have you tried uninstalling and the reinstalling the login manager? ('sudo apt-get remove lightdm' then 'sudo apt-get install lightdm') (I don't think this will make a difference though because you said gdm lets you login but you still don't get to the desktop.)

Or, have you tried reconfiguring lightdm/gdm? (sudo dpkg-reconfigure lightdm)

If the above doesn't work, remove the file .Xauthority in your home directory (sudo rm ~/.Xauthority) and then try reconfiguring or uninstalling/reinstalling the login manager. Otherwise, I suspect the problem is something else because as you said you can't login using gdm either.

You can also try removing .ICEauthority which is also in your home directory.

---

### Post by zuhudfm on 2012-06-26
I also face that. It happens when i install Burg and try to place a background i want to Burg. Because of need administration access, i type : sudo nautilus to copy a background to folder purpose. 

After restart and i brought to login page, i can't login althought my password is correct. It always brings me back to login page. I had read some sentences between start to login till back to login page. Those are:

[COLOR=#6666CC]stopping save kernel mesages [ok]
starting the winbind daemn winbind saned disabled; edit /etc/default/saned [ok]
starting anac(h)ronistic cron

starting timidity** ALSA midi emulation [ok][/COLOR]

I "googling" for problem solving but not helped untill now. Some solving are:
1. sudo apt-get remove ~ ./Xauthority
2. sudo rm /home/username/Xauthority*
3. sudo apt-get --reinstall nautilus
4. sudo apt-get --reinstall ubuntu-desktop
5. sudo chown -R $USER:$USER $HOME

but those all haven't help me yet.

---

