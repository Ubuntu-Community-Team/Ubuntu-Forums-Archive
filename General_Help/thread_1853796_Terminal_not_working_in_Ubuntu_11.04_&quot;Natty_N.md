---
title: "Terminal not working in Ubuntu 11.04 &quot;Natty Narwhal&quot;"
date: 2011-10-03
forum: General Help
---

### Post by msapra85 on 2011-10-03
Hi ):P,
I just started on with Ubuntu 11.04 and suddenly this thing came up. The terminal is not working, it just opens up for a split-second and before i could think of anything its gone.:o

Any suggestions, what to do and how to?

Thanks in advance :)

---

### Post by jon zendatta on 2011-10-03
You could try via Ubuntu Software Center -> uninstall terminal, then install

---

### Post by 2F4U on 2011-10-03
Did this happen from the beginning?

---

### Post by Krytarik on 2011-10-03
> **jon zendatta said:**
> You could try via Ubuntu Software Center -> uninstall terminal, then install
Well, I wouldn't do that, as this would remove the "ubuntu-desktop" meta-package as well. You could, however, 'reinstall' "gnome-terminal" via Synaptic or command line, but I really don't think that this would change anything. Better try this:

- Copy the content of "/etc/skel" into the top-level of your home directory.

- Run this command via the Alt+F2 dialog:
```
gconftool-2 --recursive-unset /apps/gnome-terminal
```Greetings.

---

### Post by msapra85 on 2011-10-03
no, it started after 2 or 3 days...

---

### Post by msapra85 on 2011-10-03
> **Krytarik said:**
> Well, I wouldn't do that, as this would remove the "ubuntu-desktop" meta-package as well. You could, however, 'reinstall' "gnome-terminal" via Synaptic or command line, but I really don't think that this would change anything. Better try this:

- Copy the content of "/etc/skel" into the top-level of your home directory.

- Run this command via the Alt+F2 dialog:
```
gconftool-2 --recursive-unset /apps/gnome-terminal
```Greetings.
will try it, but now I got one more trouble.
Everything from my desktop is gone, i can't see any panel, no side bar, absolutely nothing.
I changed some settings from "compiz", something related to extended desktop, and now all i got is desktop pnly :P.
Any idea, what to do??

---

### Post by msapra85 on 2011-10-03
> **2F4U said:**
> Did this happen from the beginning?
no, after 2 3 days

---

### Post by Krytarik on 2011-10-03
> **msapra85 said:**
> Everything from my desktop is gone, i can't see any panel, no side bar, absolutely nothing.
I changed some settings from "compiz", something related to extended desktop, and now all i got is desktop only.
Yay, another one! :p

To fix this, please see this troubleshooting guide:
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

It includes this guide to enable the Cube, if that's what you tried to do:
[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by msapra85 on 2011-10-03
> **Krytarik said:**
> Yay, another one! :p
 
To fix this, please see this troubleshooting guide:
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
 
It includes this guide to enable the Cube, if that's what you tried to do:
[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
 
ya, another one :grin:.
Back to work, will update with more troubles :razz:

---

### Post by Krytarik on 2011-10-03
> **msapra85 said:**
> ya, another one :D.
Back to work, will update with more troubles :P
Actually, I was meaning "*You* are 'another one' having this ubiquitous issue.", the new one.
So, no offense or something to you! :D

---

### Post by msapra85 on 2011-10-03
> **Krytarik said:**
> Actually, I was meaning "*You* are 'another one' having this ubiquitous issue.", the new one.
So, no offense or something to you! :D
 
Its fine, I dint took it as offensive.

---

### Post by msapra85 on 2011-10-03
> **Krytarik said:**
> Yay, another one! :p
 
To fix this, please see this troubleshooting guide:
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
 
It includes this guide to enable the Cube, if that's what you tried to do:
[http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
 
The idea of creating Terminal Launcher didn't worked, beacause, it all started with terminal's problem only :P and the second thing that of Ctrl+Alt+F1 is also not working, because i am unable to login.
Upon successful login, it says "Welcome to Ubuntu...." and in just the next line, asks for login again. :(

---

### Post by Krytarik on 2011-10-03
> **msapra85 said:**
> The idea of creating Terminal Launcher didn't worked, because, it all started with terminal's problem only...
Well, you don't necessarily have to use the terminal for all that. Just create a launcher for "ccsm", as also described there, then follow that particular section.

> **msapra85 said:**
> ...the second thing that of Ctrl+Alt+F1 is also not working, because i am unable to login.
Upon successful login, it says "Welcome to Ubuntu...." and in just the next line, asks for login again.
I think that's caused by the same issue that makes your terminal not work.

When you get to the point where you need to relogin, create a launcher for the command:
```
gnome-session-save --logout
```...and launch those.

---

### Post by msapra85 on 2011-10-03
> **Krytarik said:**
> Well, I wouldn't do that, as this would remove the "ubuntu-desktop" meta-package as well. You could, however, 'reinstall' "gnome-terminal" via Synaptic or command line, but I really don't think that this would change anything. Better try this:

- Copy the content of "/etc/skel" into the top-level of your home directory.

- Run this command via the Alt+F2 dialog:
```
gconftool-2 --recursive-unset /apps/gnome-terminal
```Greetings.

No, It didn't worked.

---

### Post by Krytarik on 2011-10-03
> **msapra85 said:**
> No, It didn't worked.
So, you have at least fixed your desktop by now?
Sorry, man, but I don't see you mentioning that. :-k

As for your initial, and apparently only remaining, issue; before we try reinstalling several related packages, check if it's present in a new, fresh user account, too.

---

### Post by msapra85 on 2011-10-04
> **Krytarik said:**
> So, you have at least fixed your desktop by now?
Sorry, man, but I don't see you mentioning that. :-k

As for your initial, and apparently only remaining, issue; before we try reinstalling several related packages, check if it's present in a new, fresh user account, too.

:guitar: Terminal Working now..
Previously, I changed the shell of current user to "/bin/false"
after which terminal started behaving like that, now upon changing it back to "/bin/sh", its working alright. :)

---

### Post by Krytarik on 2011-10-04
> **msapra85 said:**
> Previously, I changed the shell of current user to "/bin/false"
after which terminal started behaving like that, now upon changing it back to "/bin/sh", its working alright.
Ahh, one setting that isn't included in the locations I already took into account, noted! :D

Just curious, what made you think it's a good idea to do so, changing the shell to a non-existing value?
Btw., I have "/bin/bash" set there, and I didn't touch that since installation; nor am I planning to do it now, obviously. :P

---

### Post by msapra85 on 2011-10-04
> **Krytarik said:**
> Ahh, one setting that isn't included in the locations I already took into account, noted! :D

Just curious, what made you think it's a good idea to do so, changing the shell to a non-existing value?  

Coz I was curious, what would it(changing the shell) do :P

> 
Btw., I have "/bin/bash" set there, and I didn't touch that since installation; nor am I planning to do it now, obviously. :P

Try it, I am here to help :P :P

---

### Post by Krytarik on 2011-10-04
> **msapra85 said:**
> Coz I was curious, what would it(changing the shell) do
Well, at least you eventually remembered having changed that. :D
I'm guessing that you got it when you went about trying the new user thing?

> **msapra85 said:**
> Try it, I am here to help :P :P
:popcorn::D I guess I'd keep those setting in mind if I'd try that. ;-)

Btw., have you got your desktop working again, too?

---

### Post by msapra85 on 2011-10-04
> **Krytarik said:**
> Well, at least you eventually remembered having changed that. :D
I'm guessing that you got it when you went about trying the new user thing?


Yeah, new user, new shell, this is what striked my mind and I remembered the FALSE shell..


> 
:popcorn::D I guess I'd keep those setting in mind if I'd try that. ;-)

Btw., have you got your desktop working again, too?

Yup, desktop's also working fine..

---

### Post by Krytarik on 2011-10-04
> **msapra85 said:**
> Yeah, new user, new shell, this is what striked my mind and I remembered the FALSE shell..
Yay, I was guessing right! \\:D/ :P

---

### Post by msapra85 on 2011-10-05
> **Krytarik said:**
> Yay, I was guessing right! \\:D/ :razz:
:popcorn::)

---

