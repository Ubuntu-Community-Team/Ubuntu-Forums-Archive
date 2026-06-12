---
title: "Log in stuck and unable to enter"
date: 2011-07-04
forum: General Help
---

### Post by ronux on 2011-07-04
Hi!

After my kids were playing with my PC I am unable to log in. 
After I place my password, the screen changes but it goes back to the starting log in splash window.
I tried some of the suggestions from other posts but nothing seems to help. 
I am trying to avoid reinstalling the OS.
Your feedback and suggestions are very welcome.

Many thanks.

R.

---

### Post by e79 on 2011-07-04
Silly suggestion, but have you checked if your _Keyboard locale (language) has changed_ ? You can check at it when you click/select your username at the login screen, bottom left usually.

You can also try to SSH in your box (if its installed) to make sure your password is still the same.

---

### Post by wildmanne39 on 2011-07-04
> **ronux said:**
> Hi!

After my kids were playing with my PC I am unable to log in. 
After I place my password, the screen changes but it goes back to the starting log in splash window.
I tried some of the suggestions from other posts but nothing seems to help. 
I am trying to avoid reinstalling the OS.
Your feedback and suggestions are very welcome.

Many thanks.

R.
Hi, does it seem to be a password issue? how does the screen change like it tries to go to the desktop and then does not? does it change colors?

---

### Post by ronux on 2011-07-04
Nope, it did not take care of the issue. Locale and language are the correct one.
Not sure about the SSH - I do not believe that I installed it.
Thx for the input. Any other suggestion?

---

### Post by ronux on 2011-07-04
> Hi, does it seem to be a password issue? how does the screen change like it tries to go to the desktop and then does not? does it change colors? 

Once typed in the password and hit Enter - it looks like the usual shift in screen but then it returns back to the log in splash view. 

If I place an incorrect password I get the expected error message regarding the "authentication failure".

Thanks.

R.

---

### Post by wildmanne39 on 2011-07-05
> **ronux said:**
> Once typed in the password and hit Enter - it looks like the usual shift in screen but then it returns back to the log in splash view. 

If I place an incorrect password I get the expected error message regarding the "authentication failure".

Thanks.

R.
Hi, have you tried to log in in fail safe mode? also you can try this guide, your problem is a little different then most people are having.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mikejonesey on 2011-07-05
i had a similar problem once, to resolve setup a new user and sort out from there;

Ctrl+Alt+F1
(login as root or your usual account and sudo su to become root)... doing this won't log you out again as it does not rely on all the x stuff.

then;
useradd bob
passwd bob
enter password for bob x2

Ctrl+Atl+F7 (back to gui)
login as bob...

sort out your old user account...

---

### Post by ronux on 2011-07-05
mikejonesey
I followed your suggestion and it is not working.
After creating user bob and pass, at log in, the splash window disappears and nothing else. With the primary user name there is no change in behavior. The log in splash window comes back after hitting Enter. In either case I am stuck.
Any further idea is very welcome. 
Thanks.
R.

---

### Post by wildmanne39 on 2011-07-05
> **ronux said:**
> mikejonesey
I followed your suggestion and it is not working.
After creating user bob and pass, at log in, the splash window disappears and nothing else. With the primary user name there is no change in behavior. The log in splash window comes back after hitting Enter. In either case I am stuck.
Any further idea is very welcome. 
Thanks.
R.Hi, did you try what I mentioned in my last post?

---

### Post by ronux on 2011-07-06
wildmanne39
Yes, I did without luck...

---

### Post by mikejonesey on 2011-07-07
go back to tty1 Ctrl+Atl+F1, login and check contents of /var/log/syslog

there will probably be some messages from somthing failing which you can then use;

sudo apt-get install --reinstall BROKEN_PACKAGE_NAME

---

### Post by ronux on 2011-07-07
mikejonesey
I am attaching all the syslog that I have.
Not sure what to look for.
I read a
'/etc/gdm/custom.conf': No such file or directory
but I am not sure if this is the cause of the problem.
Thanks for your feedback and help.

R.

---

### Post by conradin on 2011-07-07
sounds like gdm is crashing. 
I would shift to a non-graphical login screen at boot
hit ```
ctrl+alt+F3
```
then try to log in. (user name and password.)
you should be met with a prompt$.
then try and kill the gdm, and other crashing session in the F7 gui session.
so: ```
sudo -i
pkill gdm
pkill gnome
pkill X11

```

basicaly kill all the graphical stuff. 
then retry to log into the graphical session
```
startx
```
you should then be logged in as root in a GUI.
 let us know if any of that doesnt work

---

### Post by ronux on 2011-07-07
conradin
I followed your steps and at the startx I get the following:
Fatal sever error:
Server is already active for display 0
If server is no longer running remove /tmp/.X0-lock
and start again.

Question: what is the F7 gui session. Is F7 the display command to get the gui displayed?

thx

---

### Post by mikejonesey on 2011-07-07
linux has 7 defaul tty f1-f6 are just terminals, f7 is the default with an xsession already loadded, there is a sys env var called DISPLAY that needs setting...

checking log now...

ps re: /etc/gdm/custom.conf': No such file or directory

you can reinstall gdm noprob, gdm is the login manager...

```
sudo apt-get install --reinstall gdm
```(from a terminal Ctrl+Alt+F1)

gdm not looking healthy;
> Jul  7 08:31:59 ubux-10zero4 gdm-binary[830]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul  7 08:31:59 ubux-10zero4 kernel: [   10.353096] type=1505 audit(1310052719.254:11):  operation="profile_load" pid=828 name="/usr/share/gdm/guest-session/Xsession"
Jul  7 08:31:59 ubux-10zero4 gdm-binary[830]: WARNING: Unable to find users: no seat-id found
Jul  7 08:31:59 ubux-10zero4 gdm-simple-slave[932]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul  7 08:32:01 ubux-10zero4 gdm-session-worker[1221]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul  7 08:32:01 ubux-10zero4 gdm-simple-greeter[1220]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow


hmm after this line though...
> Jul  7 08:32:00 ubux-10zero4 pulseaudio[1185]: core-util.c: Home directory /etc/timidity not ours.
please show ```
ls -la /etc/timidity
```
should have perm like;
> drwxr-xr-x   2 root root     4096 May  6 16:24 timidity

---

### Post by ronux on 2011-07-07
mikejonesey

```
sudo apt-get install --reinstall gdm
```
I get "couldn't find package reinstall"

```
ls -la /etc/timidity
```
It seems the same that you posted.

I am afraid that the package gdm has been removed (maybe by my kids, is it possible?)
Is there some way to get it back from a Live CD session?

Thx.

---

### Post by wildmanne39 on 2011-07-08
> **ronux said:**
> mikejonesey

```
sudo apt-get install --reinstall gdm
```
I get "couldn't find package reinstall"

```
ls -la /etc/timidity
```
It seems the same that you posted.

I am afraid that the package gdm has been removed (maybe by my kids, is it possible?)
Is there some way to get it back from a Live CD session?

Thx.Hi,boot to recovery choose root prompt with network then run.
```
sudo apt-get install gdm
``` 
then reboot.

---

### Post by ronux on 2011-07-10
wildmanne39

> Hi,boot to recovery choose root prompt with network then run.
I get "gdm is already the newest version"

I tried this too

```
sudo apt-get install --reinstall gdm
```
I get the packages as expected.

At log in I have the same issue.
:confused:

This is mind boggling...

Thanks for any suggestion or feedback.

R.

---

### Post by mikejonesey on 2011-07-11
> I get the packages as expected.
as-in it reinstalled?

hmmm, post your stdout again please...

---

### Post by ronux on 2011-07-12
Yes, they were reinstalled.
I did not get any odd message. 

> hmmm, post your stdout again please... 

stdout?

---

### Post by wildmanne39 on 2011-07-12
Hi,boot to recovery choose root prompt with network then run. 
```
apt-get update && apt-get install ubuntu-desktop && apt-get upgrade
```

---

### Post by ronux on 2011-07-12
It worked! :) Bravo! wildmanne39
One thing I noticed, is that before the complete log in, there is a lagging time, it does not log as fast as it did in the past.
I am thrilled but I am wondering if there is anything else that could be done at this point.
Many thanks, I really appreciated your perseverance in helping out.

---

### Post by wildmanne39 on 2011-07-12
> **ronux said:**
> It worked! :) Bravo! wildmanne39
One thing I noticed, is that before the complete log in, there is a lagging time, it does not log as fast as it did in the past.
I am thrilled but I am wondering if there is anything else that could be done at this point.
Many thanks, I really appreciated your perseverance in helping out.
Hi, I am glad it worked! I am not sure it is possible the next time you boot up that it will be back to normal, if not you can look at your logs with log file viewer and see what is slowing it down, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by ronux on 2011-07-12
OK, I will mark it Solved

I tried to restart and it worked.

I am attaching the syslog.
I am not sure how to interpret it...let me know if there is something that I could do.

Once again, many thx!

---

### Post by mikejonesey on 2011-07-13
not enough in the syslog, if you used tail specify -100 or -n 100...

will explain what lines mean in next 1, great you can login again, finally :)

---

