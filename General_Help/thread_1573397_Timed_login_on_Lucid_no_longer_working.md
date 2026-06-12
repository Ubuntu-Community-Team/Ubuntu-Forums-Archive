---
title: "Timed login on Lucid no longer working"
date: 2010-09-12
forum: General Help
---

### Post by master higgins on 2010-09-12
Hi. First of all thanks for having such a great forum for all the Ubuntu users that are eager to use this O.S. :D

Now, on to the topic:
I know that since Karmic the **"Timed Login"** Feature **no longer works**, even if you can access it by running gdmsetup. **After killing X or closing the session** the **login screen** just stays **asking for an username**, **[COLOR=Red]despite having chosen an user in gdmsetup to be logged on in a certain amount of seconds.[/COLOR]**

The question is, is there any other way to achieve this? I've configured /etc/gdm/custom.conf this way (Or better said, gsmsetup wrote these values in this file):

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=ivan
TimedLoginEnable=true
TimedLogin=ivan
TimedLoginDelay=10

```The username I'm using is "ivan".

I'm hoping someone enlighten me on how to achieve this in another way. I'm using this configuration for an arcade cabinet with Lucid installed and it's more comfy to just press Ctrl+alt+backspace and wait 10 seconds for the system to autologin than to choose an user and type the password.

Thanks! ;)

---

### Post by dcstar on 2010-09-13
> **master higgins said:**
> 
..........
Now, on to the topic:
I know that since Karmic the **"Timed Login"** Feature **no longer works**
.........

Really?, it works fine on my system.

---

### Post by master higgins on 2010-09-18
Can you post the contents of /etc/gdm/custom.conf (or whatever the configuration file for gdm is)?

I don't know if threre's anything else to configure to get this working :confused:.

**Automatic login works** (after booting Ubuntu automatically logins with the given user in custom.conf). The **timed login** is the thing that **doesn't work after logging out or killing X**. It stays **asking for a user to be chosen**.

Thanks! ;)

---

