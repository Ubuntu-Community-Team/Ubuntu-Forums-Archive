---
title: "Firefox 3.6.3 not working - Need help"
date: 2010-05-18
forum: General Help
---

### Post by sunrpc on 2010-05-18
Hello,

I'm trying to upgrade my Firefox 3.0.19 (coming with Ubuntu 9.04) to 3.6.3 using the Mozillateam/firefox-stable repo.

My problem is when I upgrade my firefox package, it is not possible to run Firefox anymore. When I click on the firefox icon, I have the 'Starting firefox toolbar' that comes up. But then, nothing happens. Firefox process is running fine, but nothing comes up on the desktop.

Does someone knows about that issue ?

My OS is Ubuntu 9.04.

Thanks

---

### Post by sunrpc on 2010-05-18
In fact, I also have the same issue with the standard firefox-3.5 package (Shiretoko).

Does someone have an idea about that issue ?

---

### Post by s.fox on 2010-05-18
Hello.

Can you run this command in terminal:


```
firefox
```Does it  bring up any errors?  

Also can you confirm that firefox is not minimised or displayed on a different desktop (Just thinking in terms of the desktop switcher)

-Silver Fox

---

### Post by sunrpc on 2010-05-18
Hello,

Thank you for your support.

I don't think it is minimized (I can't see anything close to that state) and it is not in another desktop. I reduced the number of desktop to 1, to be sure this won't be the cause.

When I type the 'firefox' command in a terminal, nothing happens (no error on the terminal). Except that I have a firefox-3.5 running.
It is 3.5 because I tried the 3.5 version which is in the standard repo. It is exactly the same as 3.6.3.
However, in that situation, I have both 3.0.19 and 3.5.9.
3.0.19 is working just fine.
3.5.9 won't display on the desktop !

One point I can add:
It seems that with 3.5.9 or 3.6.3, my ~/.mozilla directory is not updated or accessed anymore.
I have no explanation about that ! But this may be the cause of my problem

---

### Post by pradeepthundiyil on 2010-05-18
type 'about:config' on the url bar oof firefox. . 

search for network.htttp.pipelining - true.

---

### Post by pradeepthundiyil on 2010-05-18
type 'about:config' on the url bar oof firefox. . 

search for network.htttp.pipelining - make it true........

---

### Post by sunrpc on 2010-05-18
The thing is that I don't have access to the URL bar or firefox 3.5 or above since nothing is displayed on the desktop.

---

### Post by lovinglinux on 2010-05-18
Check ~/.mozilla permissions. See the first item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

If the permissions are OK, then make sure you kill all firefox processes before starting:

```
killall firefox-bin
```

If that doesn't help, then try to start the profile manager and create a new profile:

```
firefox -P
```

If that doesn't work, start it with this:

```
firefox -safe-mode
```

If that works, then I would look if you have Moonlight installed, then remove libmoon.

More info [here](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html).

---

### Post by tad1073 on 2010-05-18
> **pradeepthundiyil said:**
> type 'about:config' on the url bar oof firefox. . 

search for network.htttp.pipelining - true.

> **pradeepthundiyil said:**
> type 'about:config' on the url bar oof firefox. . 

search for network.htttp.pipelining - make it true........


has nothing to do with the problem the OP is facing.

---

### Post by sunrpc on 2010-05-19
Thanks lovinglinux for your advice. I just tried the following to start Firefox with a sudo command and it worked.

I made sure that ~/.mozilla folder permissions/ownership were set correctly but even after that when I started again Firefox (without sudo), nothing happened. :(

One additional point.
When I use 'sudo' to start firefox from a terminal, I have a bunch of those coming up:
'Xlib:  extension "Generic Event Extension" missing on display ":1042.0".'
If I don't use 'sudo', none of those lines come up.

It is now obvious that I have one problem somewhere in permissions settings. However, I'm not Linux experienced enough to know where to look.

Some additional help would be greatly appreciated. :)

---

### Post by lovinglinux on 2010-05-19
> **sunrpc said:**
> Thanks lovinglinux for your advice. I just tried the following to start Firefox with a sudo command and it worked.

I made sure that ~/.mozilla folder permissions/ownership were set correctly but even after that when I started again Firefox (without sudo), nothing happened. :(

One additional point.
When I use 'sudo' to start firefox from a terminal, I have a bunch of those coming up:
'Xlib:  extension "Generic Event Extension" missing on display ":1042.0".'
If I don't use 'sudo', none of those lines come up.

It is now obvious that I have one problem somewhere in permissions settings. However, I'm not Linux experienced enough to know where to look.

Some additional help would be greatly appreciated. :)

Never start Firefox with sudo. See the fist item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html) for a solution.

---

### Post by sunrpc on 2010-05-19
I did what is explained in the link you gave me.
However, it does not solve my issue as explained before.
Both sudo and gksudo will allow to start firefox.

However, as soon as I start firefox with my standard user account, it does not work anymore: firefox windows will not display.

I suppose there is somewhere some security setting that prevent firefox from being displayed.

Do you have any idea ?

---

### Post by lovinglinux on 2010-05-19
> **sunrpc said:**
> I did what is explained in the link you gave me.
However, it does not solve my issue as explained before.
Both sudo and gksudo will allow to start firefox.

However, as soon as I start firefox with my standard user account, it does not work anymore: firefox windows will not display.

I suppose there is somewhere some security setting that prevent firefox from being displayed.

Do you have any idea ?

Have you tried to create a new profile?

---

### Post by maddg3241 on 2010-05-19
good advice remember to mark your forum as solved when done

---

### Post by sunrpc on 2010-05-19
I tried already a new profile...
I'm going to try a new user !

---

### Post by sunrpc on 2010-05-19
Well, I have the exact same issue with a brand new user.

There is some setting somewhere in the system that prevent Firefox to run when not executed with gksudo/sudo command.

---

### Post by lovinglinux on 2010-05-19
> **sunrpc said:**
> Well, I have the exact same issue with a brand new user.

There is some setting somewhere in the system that prevent Firefox to run when not executed with gksudo/sudo command.

Again, don't use sudo to start Firefox. If you have used it after applying the suggested fix, then ~/.mozilla will be owned by root and will cause such problems like preventing Firefox (regular user) from starting or saving anything.

---

### Post by sunrpc on 2010-05-19
I did not use sudo/gksudo with my newly created user.
Using either -safe-mode or -P option did not give any result.

Regarding the use of sudo, I wanted to point out the fact that it works with root privileges, which means that I don't have any missing component.
The fact that it does not work with standard permission (non root), means that somewhere I have some kind of weird configuration or permission that prevents the execution of firefox.

I clearly understand the use of sudo is not appropriate. Using gksudo, everything is ok.
I did try the use of sudo to make sure I did not miss some component. Anyway, after the use of sudo, I changed back all settings/ownership on the ~/.mozilla folder.

So as I said before, my problem lies outside the user profile. I just have no idea of where !

---

### Post by lovinglinux on 2010-05-19
> **sunrpc said:**
> So as I said before, my problem lies outside the user profile. I just have no idea of where !

Try to reinstall xulrunner.

---

### Post by sunrpc on 2010-05-19
I already reinstall xulrunner many times.
I did it with version 1.9 and 1.9.1
It did not fix my problem.

Is there a way to test xulrunner installation ?

---

### Post by lovinglinux on 2010-05-19
> **sunrpc said:**
> I already reinstall xulrunner many times.
I did it with version 1.9 and 1.9.1
It did not fix my problem.

Is there a way to test xulrunner installation ?

I'm sorry, it seems the latest versions of Firefox are not dependent on xulrunner anymore. They have a built-in version of it, so re-installing xulrunner wouldn't help anyway.

---

### Post by sunrpc on 2010-05-20
I have decided to fully reinstall my Ubuntu.
Thank you to all of you who provided support.

---

