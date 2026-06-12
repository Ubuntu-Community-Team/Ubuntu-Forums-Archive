---
title: "change the login prompt"
date: 2011-10-07
forum: General Help
---

### Post by casaschi on 2011-10-07
Hello,

Is there a way to change/customize the login prompt (the textual login, not the graphical one)?

I know about the /etc/issue and /etc/motd files, those appear before and after the login prompt; what I'm asking is the actual login prompt.

Thanks.

---

### Post by haqking on 2011-10-07
> **casaschi said:**
> Hello,

Is there a way to change/customize the login prompt (the textual login, not the graphical one)?

I know about the /etc/issue and /etc/motd files, those appear before and after the login prompt; what I'm asking is the actual login prompt.

Thanks.

it is the $PS1 variable

see here [http://lindesk.com/2009/03/customizing-the-terminal-the-prompt/](http://lindesk.com/2009/03/customizing-the-terminal-the-prompt/)

saves me typing ;-)

---

### Post by casaschi on 2011-10-07
> **haqking said:**
> it is the $PS1 variable

see here [http://lindesk.com/2009/03/customizing-the-terminal-the-prompt/](http://lindesk.com/2009/03/customizing-the-terminal-the-prompt/)

saves me typing ;-)

no, it's not :(

that is the shell prompt, where you enter commands to your shell terminals.

I want to customize the login prompt, where the systems asks for your username and password for login to a textual terminal.

---

### Post by haqking on 2011-10-07
> **casaschi said:**
> no, it's not :(

that is the shell prompt, where you enter commands to your shell terminals.

I want to customize the login prompt, where the systems asks for your username and password for login to a textual terminal.

oh ok yeah then it is /etc/issue

look at man getty

---

### Post by QLee on 2011-10-07
[QUOTE=casaschi]
I want to customize the login prompt, where the systems asks for your username and password for login to a textual terminal.[/QUOTE]
One place that could be done is /etc/bash.rc. Unless your system has been changed previously and/or is non-standard I would look there first. If you don't have any luck with that come back with the information and we will look for the other possibilities.

---

### Post by haqking on 2011-10-07
> **QLee said:**
> One place that could be done is /etc/bash.rc. Unless your system has been changed previously and/or is non-standard I would look there first. If you don't have any luck with that come back with the information and we will look for the other possibilities.

that is for the shell like my first reply, he doesnt want it for the shell from what i see he wants it from tty

---

### Post by KeyserSoze93 on 2011-10-07
Try running "man login"

"login" is the command which actually handles the login screen as seen on the non-X ttys.

I'm not sure what you can actually change, but it seems a bit configurable through files like /etc/login.defs

---

### Post by casaschi on 2011-10-07
> **haqking said:**
> oh ok yeah then it is /etc/issue

look at man getty

No, wrong again.
/etc/issue is shown BEFORE the login prompt.

If /etc/issue is empty, my login prompt is
```
hostname login:
```
I want to get rid of the login prompt showing the hostname.

---

### Post by casaschi on 2011-10-07
> **KeyserSoze93 said:**
> Try running "man login"

"login" is the command which actually handles the login screen as seen on the non-X ttys.

I'm not sure what you can actually change, but it seems a bit configurable through files like /etc/login.defs

I looked there and in /etc/pam.d/login but the login prompt does not seem configurable there.

---

### Post by haqking on 2011-10-07
> **casaschi said:**
> No, wrong again.
/etc/issue is shown BEFORE the login prompt.

If /etc/issue is empty, my login prompt is
```
hostname login:
```
I want to get rid of the login prompt showing the hostname.

I am pretty sure it is related to getty

man getty refers to it

as does ngetty [http://manpages.ubuntu.com/manpages/maverick/man8/ngetty.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/ngetty.8.html) look for the login prompt string

---

