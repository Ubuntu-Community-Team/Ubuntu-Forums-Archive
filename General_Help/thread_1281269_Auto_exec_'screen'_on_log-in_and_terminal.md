---
title: "Auto exec 'screen' on log-in and terminal"
date: 2009-10-03
forum: General Help
---

### Post by CloudyWind on 2009-10-03
Howdy,

I am looking to have GNU 'screen' auto execute on 2 events:

1) On User log-in ie - power up user/pass requested - desktop loads - terminal automatically opens and executes screen.

2) New terminal instance - user is logged in and requests a new terminal - screen is executed once the new terminal session opens.

I'm rather new to linux and learning the .profile/.bashrc differences.... 

I've added 'exec screen' to my .bashrc which seems to have worked - 'screen' was called on a new terminal session BUT screen then entered some form of loop and kept calling screen - creating multiple 'screen' instances.

The aim is to have native screen commands in all my terminal sessions and have a terminal/screen available on login.

Cheers,

---

### Post by ermeyers on 2009-10-03
> **CloudyWind said:**
> Howdy,

I am looking to have GNU 'screen' auto execute on 2 events:

1) On User log-in ie - power up user/pass requested - desktop loads - terminal automatically opens and executes screen.

2) New terminal instance - user is logged in and requests a new terminal - screen is executed once the new terminal session opens.

I'm rather new to linux and learning the .profile/.bashrc differences.... 

I've added 'exec screen' to my .bashrc which seems to have worked - 'screen' was called on a new terminal session BUT screen then entered some form of loop and kept calling screen - creating multiple 'screen' instances.

The aim is to have native screen commands in all my terminal sessions and have a terminal/screen available on login.

Cheers,
What version OS?  I'm using 9.04.

1. For a gnome desktop session, you  want to ADD a terminal startup in System->Preferences->Startup Applications with command "gnome-terminal -e screen".

2. Assuming that you're still in a GUI desktop session modify the Menu at System->Preferences->Main Menu.  Select Accessories->Terminal and change its properties to command "gnome-terminal -e screen".

---

### Post by CloudyWind on 2009-10-03
> **ermeyers said:**
> What version OS?  I'm using 9.04.

1. For a gnome desktop session, you  want to ADD a terminal startup in System->Preferences->Startup Applications with command "gnome-terminal -e screen".

2. Assuming that you're still in a GUI desktop session modify the Menu at System->Preferences->Main Menu.  Select Accessories->Terminal and change its properties to command "gnome-terminal -e screen".

Same - 9.04.

Cheers for your 2 ideas - spot on.

Wondering what internal files these changes would have edited? For example, if I wanted to do this without using the GUI  - would it be possible?

Otherwise - all good now.

---

### Post by orange-wedge on 2009-10-03
First I would add screen to your start-up scripts.  You could add it to /etc/rc.local and run the command as your GUI user if you do not want to deal gnome session settings 

EDIT:
```
su - user -c "screen -dm -h 9999 -S screenName" &
```Then you can add:

```
screen -r
```to your .bashrc file.

That should attempt to resume any screens that have not been previously attached, every time you start a bash shell (ie if you login via ssh as well).

Ubuntu does have some handy pre-configured screen profiles:
[https://help.ubuntu.com/9.04/serverguide/C/screen-profiles.html](https://help.ubuntu.com/9.04/serverguide/C/screen-profiles.html)

---

### Post by ermeyers on 2009-10-03
Another option.  Program screen has been complicated over the years, evidently, and doesn't run as simply as it used to run.  Anyway there's an enhancement package called screen-profiles that sets the login stuff.  Just "apt-get install screen-profiles" and try running screen-profiles.  It has a little menu of options.

---

