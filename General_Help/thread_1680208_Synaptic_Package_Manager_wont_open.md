---
title: "Synaptic Package Manager wont open"
date: 2011-02-02
forum: General Help
---

### Post by squid636 on 2011-02-02
I need some assistance on getting Synaptic Package Manager to start correctly.  I can start it from the command line without any errors.  When I try to use the shortcut under the /System/Administration menu it ask for the password but nothing ever opens up nor is there an error.  My source list is fine.  I have ran "sudo apt-get update" Any suggestions?

---

### Post by ajgreeny on 2011-02-02
Have a look at the menu's command for synaptic by going to properties of the link in your menu by right clicking on the menu bar, choosing edit menus, and navigating to system->administration->synaptic->properties.

The default command in my 10.04 is a complicated
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```but you may find that something as simple as ```
gksu synaptic
``` will suffice, or use what you type in terminal, which you know does work.

---

### Post by squid636 on 2011-02-02
I had the default command under my properties.  So I tried changing it to the short one and still no joy.  When I first click the link I see a transparent window open up full screen but you can see anything on it.  Then after entering the password you it disappears.  Thanks for the reply.

---

### Post by irv on 2011-02-02
> The default command in my 10.04 is a complicated
Code:

```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```

> but you may find that something as simple as
Code:

```
gksu synaptic
```

I checked my setting under 10.10 and it is the same.

---

### Post by irv on 2011-02-02
> **squid636 said:**
> I had the default command under my properties.  So I tried changing it to the short one and still no joy.  When I first click the link I see a transparent window open up full screen but you can see anything on it.  Then after entering the password you it disappears.  Thanks for the reply.

To see if it is a compiz issue do this:
In a terminal type
```
metacity --replace
```
Then try the Synaptic Package Manager.
To go back to compiz type in the terminal
```
compiz --replace
```

---

### Post by squid636 on 2011-02-02
Tried that and this is what is in the terminal
"Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x2a0002c ([lubuntu] ); these messages lack timestamps and therefore suck."
It still didnt open though.

---

### Post by squid636 on 2011-02-03
I think that I have found a lead on this problem.  It seems to stem from me trying to get my fingerprint reader working.  I will update again later today.

---

### Post by squid636 on 2011-02-03
The problem was with the fingerprint software that I downloaded.  I uninstalled it and then reinstalled it all again and now it is working.  Synaptic Package Manager was waiting for the input from the fingerprint scanner and when I wasnt able to use it the program would just close.  When I tried to login or do anything as root I had to enter my password twice.  Thanks for the advice while I was troubleshooting this.

---

### Post by irv on 2011-02-03
> **squid636 said:**
> The problem was with the fingerprint software that I downloaded.  I uninstalled it and then reinstalled it all again and now it is working.  Synaptic Package Manager was waiting for the input from the fingerprint scanner and when I wasnt able to use it the program would just close.  When I tried to login or do anything as root I had to enter my password twice.  Thanks for the advice while I was troubleshooting this.

Glad to see you got the problem figured out. Sometimes we just have to back up to go forward.

---

