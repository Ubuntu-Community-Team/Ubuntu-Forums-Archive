---
title: "Run script AFTER login"
date: 2009-08-13
forum: General Help
---

### Post by 696f6e6963 on 2009-08-13
I need to run the same script for every user who logs on. Adding it to the rc*.d is not an option since it needs to run after after users login, and manually editing the each users .profile (or System -> Preferences -> Startup Applications) is unreasonable. Did a quick search, and all the results seemed to be for a single user. How can I run the same script for all users after they login?

---

### Post by VCoolio on 2009-08-13
Put a launcher in /etc/xdg/autostart and the script somewhere else, eg /usr/local/bin

---

### Post by Brandon Williams on 2009-08-15
If it's something that should run after login but before the session manager is launched, then you can put it in /etc/X11/Xsession.d/. The files there are numbered to maintain execution ordering, just like the ones in /etc/rc*.d/.

---

### Post by 696f6e6963 on 2009-08-18
So I placed the following test script

```
#!/bin/sh

xterm &
```in /etc/X11/Xsession.d which executable permissions and a name of "startup" - it doesn't seem to be starting. Any ideas why?

---

### Post by nikhilk on 2009-08-18
Probably a simpler way mentioned [here]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") will suffice?

---

### Post by 696f6e6963 on 2009-08-19
> **nikhilk said:**
> Probably a simpler way mentioned [here]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") will suffice?

I don't believe so - from what I understand, that only works for the user who does that. If John adds the start up script using that method, then Mary logs on, the script won't start for her. VCoolio's method seems to work though.

---

### Post by nikhilk on 2009-08-19
> **696f6e6963 said:**
> I don't believe so - from what I understand, that only works for the user who does that. If John adds the start up script using that method, then Mary logs on, the script won't start for her. VCoolio's method seems to work though.

Oops, mea culpa! I did not read your first post correctly. Yes this method is user specific and won't work for all users.

---

### Post by Penguin Guy on 2009-08-19
Couldn't you put it in [COLOR="Green"]/etc/profile[/COLOR]?

---

### Post by 696f6e6963 on 2009-08-19
I did try that, as well as adding a script to /etc/profile.d/ - I didn't seem to have much luck. I probably did something wrong though.

---

### Post by Slim Odds on 2009-08-19
> **Penguin Guy said:**
> Couldn't you put it in [COLOR=Green]/etc/profile[/COLOR]?

That file only applies to bash.

---

### Post by Brandon Williams on 2009-08-19
> **696f6e6963 said:**
> So I placed the following test script

```
#!/bin/sh

xterm &
```in /etc/X11/Xsession.d which executable permissions and a name of "startup" - it doesn't seem to be starting. Any ideas why?

It's not running because, lexigraphically, it comes after 99x11-common_start, which calls exec, and so your script will never be run. Try renaming the script from startup to 98startup so that it gets handled before the session manager is executed.

Bear in mind that this is not a script, in that it is not executed. It is a component of a script, because it is sourced. There is no need for your file to have a '#!' line at the beginning, not is it necessary to make it executable.

If you want to know where your file will fall in the processing order, run this command:
```
run-parts --list /etc/X11/Xsession.d
```
You'll get a listing of the files in that directory in the order in which they will be processed.

---

### Post by Naggobot on 2010-06-13
I created an upstart job

```
/etc/init/[jobname].conf
```for me the job file contents are

```
# Comment header
description    "short description"

start on (started network-manager)

script
    #first sleep a while to give network time to connect
    sleep 60
    do stuff
    exit 0
end script

```I am not sure about the exit 0 but it does not seem to hurt. Also there might be better way to wait for network connection than sleep. 

Benefit of this is that this is now run as root for all users since the script is owned by root. I use the script to start rsync backup and I was unable to get update-rc.d to work.

---

### Post by _nikolaos on 2011-04-22
Is there a way to understand which way some user logged into the system?

I usually log in locally, starting GNOME, or remotely from my windows 7 netbook, either through ssh/putty ("text mode"), or through NX client ("graphics mode").

I want these ways to be automatically discriminated, so the system starts a different startup script depending on these. I am not familliar with the booting process of ubuntu linux, hence I can't figure out what is most appropriate to do.

I have a specific problem that caused this question: I use two different keyboard layouts, but I cannot toggle between them whenever I log in through NX client that starts GNOME; the icon on the panel freezes. To fix it, I always open a GNOME Terminal and type
```
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,gr
```
which un-freezes the icon and allows me to toggle between the two languages' keyboard layouts.

This problem does not occur whenever I log into GNOME locally, only remotely by NX. I want to shortcut that fix and start a small script with the code immediately AFTER the graphics are loaded, so that I will not have to fix it myself every time.

In the same mood, it would be useful to learn something about the way ubuntu-linux "understands" the interface with which users interact.

I wonder if I must use commands like "w", "who", "ps" or is there a completely different way.

---

### Post by tbone3421 on 2011-07-22
Thank you guys for posting. I put a little script in /X11/Xsession.d/ to run some commands after log in and it worked great on 11.04.

I had trouble getting my MacbookPro with 11.04 on it to recognize an external monitor without starting a new Xsession, then running 
metacity --replace &
compiz --replace & 
every single time I logged in and started a new Xsession.  There is probably a better way to do it, but for the time being I just stuck a script to run at login.

---

