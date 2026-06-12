---
title: "unable to login / authorisation failure"
date: 2009-10-01
forum: General Help
---

### Post by pommers on 2009-10-01
Hi. Ubuntu newbie here so please excuse any stupid questions!
 
I installed Ubuntu 9.04 for the 1st time a few days ago. Everything worked very smoothly until I tried to automatically unlock the default gnome keyring password. I did this by following the instructions at:-
 
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)
 
 
After following these instructions, I rebooted my PC with "automatically login" enabled. It loaded fine as normal straight into Ubuntu. However, I was still asked for the default keyring password by the network manager applet. I then read that the workaround described in the above link doesn't work if "automatic login" is enabled. So, I disabled automatic login and rebooted. 
 
Now I hit the BIG problem. When I reboot, I am presented with the Ubuntu login screen & am prompted for a username. **Before I even touch the keyboard** this prompt is replaced with a message stating "Authorisation Failure". so, I have no way of accessing my machine :(.
 
I tried running Ubuntu from the live CD & browsed to the */etc/pam.d/gdm* file which I had edited & removed the line which I had added ([FONT=Courier New][COLOR=#000066]@include common-pamkeyring)[FONT=Verdana][COLOR=black]However, the system would not allow me to save the file since I did not have the needed permissions to overwrite.[/COLOR][/FONT][/COLOR][/FONT]
 
Any help would be warmly appreciated since right now the only option I can think of is a re-install...
 
Thanks in advance.

---

### Post by bruno9779 on 2009-10-01
you can save the file, if you open it from CLI with

```
sudo gedit /location/of/file
```

careful with what you do though.

---

### Post by pommers on 2009-10-01
Thanks for your reply. 
 
I did try to do this by loading Ubuntu in "repair mode" (or whatever it's called) from the boot loader and then starting a command line from the various options provided. I typed 
 
sudo gedit /etc/pam.d/gdm
 
But I got an unhelpful response, something like "unable to load display" if I remember correctly.

---

### Post by wojox on 2009-10-01
If you run it from that mode you need:

```
nano /etc/pam.d/gdm
```

---

### Post by mcduck on 2009-10-01
> **pommers said:**
> Hi. Ubuntu newbie here so please excuse any stupid questions!
 
I installed Ubuntu 9.04 for the 1st time a few days ago. Everything worked very smoothly until I tried to automatically unlock the default gnome keyring password. I did this by following the instructions at:-
 
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)
 
 
After following these instructions, I rebooted my PC with "automatically login" enabled. It loaded fine as normal straight into Ubuntu. However, I was still asked for the default keyring password by the network manager applet. I then read that the workaround described in the above link doesn't work if "automatic login" is enabled. So, I disabled automatic login and rebooted. 
 
Now I hit the BIG problem. When I reboot, I am presented with the Ubuntu login screen & am prompted for a username. **Before I even touch the keyboard** this prompt is replaced with a message stating "Authorisation Failure". so, I have no way of accessing my machine :(.
 
I tried running Ubuntu from the live CD & browsed to the */etc/pam.d/gdm* file which I had edited & removed the line which I had added ([FONT=Courier New][COLOR=#000066]@include common-pamkeyring)[FONT=Verdana][COLOR=black]However, the system would not allow me to save the file since I did not have the needed permissions to overwrite.[/COLOR][/FONT][/COLOR][/FONT]
 
Any help would be warmly appreciated since right now the only option I can think of is a re-install...
 
Thanks in advance.

I'd say the real problem was following that quide in the first place, since it's not needed with any recent Ubutnu version, they all have that mechanism included by default.. All you have to do is to mae sure your keyring password is the same as your login password (besides, that guide still doesn't allow you to unlock the keyring automaticaly without using a notrmal logn. the onlyw ay to do that is to remove the keyring password, which can be done in Applications/Accessories/Passwords and Encryption keys).

What comes to removing your changes from the configuration file, the complaint about not having permissions sounds like you simply didn't use "sudo" to do the editing with root permissions.. Of corse when done in revovery mode that's not required since recovery mode logs you in as root anyway.

edit: Also, you can' use Gedit when editing files in command-line. Gedit is a graphical application and requires running a graphical desktop. Use nano instead, like Wojox suggested above.

After you get your changes undone, here's how to change/unset the keyring password:

1.Open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Passwords-tab

3. Right-click the "Passwords:login"-keyring & select "Change Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by pommers on 2009-10-01
Thanks. I'll try to undo my edits using nano, as suggested by Wojox

NB, my keyring & login passwords _are_ the same, but the nm-applet still asked me for my keyring password every time I started the machine. Maybe this was because I had "auto login" enabled?

---

### Post by mcduck on 2009-10-01
> **pommers said:**
> Thanks. I'll try to undo my edits using nano, as suggested by Wojox

NB, my keyring & login passwords _are_ the same, but the nm-applet still asked me for my keyring password every time I started the machine. Maybe this was because I had "auto login" enabled?

Yes, like I said the keyring will be automatically unlocked only when you use your password at the login screen. So it won't work if you use automatic or timed login (or have different passwords for login and the keyring).

If you want automatic login without having to enter the keyring password the only option is to remove the keyring password completely, using the method I posted above.

Not having a keyring password is slightly less secure, but not usually a problem unless you have some important encryption and signing keys or other stuff like that in your keyring. But if you had, you probably wouldn't be using automatic login anyway.. ;)

---

### Post by pommers on 2009-10-02
Hi wojox. Thanks so much for your help; by doing this I can now access my machine again!

---

### Post by pommers on 2009-10-02
Thanks mcduck for your guidance. I'm fully up & running again now & eager to learn more about ubuntu!

---

