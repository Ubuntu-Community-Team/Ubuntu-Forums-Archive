---
title: "How to make programs run at startup?"
date: 2010-09-04
forum: General Help
---

### Post by crazyfuturamanoob on 2010-09-04
I don't have a very usual setup on my laptop:
[list]
[*]Ubuntu Server 10.04
[*]Slim (login manager)
[*]Ratpoison (window manager)
[/list]

I need to run some commands after X starts:
```

syndaemon -d -i .1
volume_control
xmodmap -e "keycode 34 = F13 F13 F13 F13 F13 F13 F13 F13"

```

I have tried to put them in:
[list]
[*]~/.xinitrc
[*]~/.xprofile
[*]~/.xsession
[/list]
But they don't get executed. What's the problem?

---

### Post by DeMus on 2010-09-04
> **crazyfuturamanoob said:**
> I don't have a very usual setup on my laptop:
[list]
[*]Ubuntu Server 10.04
[*]Slim (login manager)
[*]Ratpoison (window manager)
[/list]

I need to run some commands after X starts:
```

syndaemon -d -i .1
volume_control
xmodmap -e "keycode 34 = F13 F13 F13 F13 F13 F13 F13 F13"

```

I have tried to put them in:
[list]
[*]~/.xinitrc
[*]~/.xprofile
[*]~/.xsession
[/list]
But they don't get executed. What's the problem?

Try System - Preferences - Start-up Applications. Or type "gnome-session-properties" to start the same program.

---

### Post by ajgreeny on 2010-09-04
> **DeMus said:**
> Try System - Preferences - Start-up Applications. Or type "gnome-session-properties" to start the same program.
The OP does not use gnome!

There must be some way in ratpoison to use startup programs in some way, surely?

What about putting the commands in /etc/rc.local.  I have no idea what they are for, but it is possible that at least the syndaemon might work, as I assume that does not need an x session, but I'm not sure about the other two.

---

### Post by apmcd47 on 2010-09-04
I've just looked at ratpoison's web site. There seems to be a .ratpoisonrc file for start-up commands and an exec command for executing shell commands. Could these help you?

Check the [ratpoison manual]("http://www.nongnu.org/ratpoison/doc/index.html#Top")

Andrew

---

### Post by mendhak on 2010-09-04
But there should still be a 

/etc/init.d

right?

You can copy the script to /etc/init.d

Make sure it's executable.
Then run

$ update-rc.d SCRIPTNAME

---

### Post by apmcd47 on 2010-09-04
> **mendhak said:**
> But there should still be a 

/etc/init.d

right?



Yes and no. Yes there is init.d. No, it's not necessarily the right place to put these commands. While OP says "at startup" I imagine he means "at login". I don't know what syndaemon is, and that perhaps does belong in init.d, but the others are X-session-specific and should be started at login.

crazyfuturamanoob: Is there anything in $HOME/.xsession-errors to explain what is going on? Can you check the slim startup files to see if they are calling /etc/X11/Xsession?

Andrew

---

