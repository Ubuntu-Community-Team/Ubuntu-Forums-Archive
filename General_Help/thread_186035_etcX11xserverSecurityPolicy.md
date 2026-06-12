---
title: "/etc/X11/xserver/SecurityPolicy"
date: 2006-06-01
forum: General Help
---

### Post by jonibo on 2006-06-01
I'm seeing an error about xserver/SecurityPolicty in /var/log/Xorg.0.log.  What happened to this file... it does not seem to be installed?
...
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
...

---

### Post by henriqueqc on 2006-07-03
.

---

### Post by henriqueqc on 2006-07-03
Same error here! Here's what I did:
[INDENT]
*find / -name SecurityPolicy*

And found out there is an example of that file in: /usr/share/doc/examples/SecurityPolicy
Then I created the "xserver" directory:

*mkdir /etc/X11/xserver*

Copied the file over:

*cp /usr/share/doc/examples/SecurityPolicy /etc/X11/xserver*

And the error was gone.
[/INDENT]
I don't know the purpose of that file. But maybe someone forgot it. A bug? I'll try to report it.

---

### Post by ububaba on 2007-01-15
> **henriqueqc said:**
> Same error here! Here's what I did:
[INDENT]
*find / -name SecurityPolicy*

And found out there is an example of that file in: /usr/share/doc/examples/SecurityPolicy
Then I created the "xserver" directory:

*mkdir /etc/X11/xserver*

Copied the file over:

*cp /usr/share/doc/examples/SecurityPolicy /etc/X11/xserver*

And the error was gone.
[/INDENT]
I don't know the purpose of that file. But maybe someone forgot it. A bug? I'll try to report it.

Have a rather similar problem. Startup cannot open **/etc/X11/xserver/SecurityPolicy**. 
When I accessed it through repairmode, it was blank. My basic problem is that [COLOR="Red"]login[/COLOR] has gone
into a loop and [COLOR="Red"]file system check[/COLOR] also fails. Wonder if I can find the contents of "**SecurityPolicy**" 
and paste it there would that help me get out of the loop? Thanks for any help.

---

### Post by henriqueqc on 2007-01-18
I have atached my SecurityPolicy file.
Let me know if it worked.
Good Luck!

---

