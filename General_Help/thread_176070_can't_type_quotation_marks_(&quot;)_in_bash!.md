---
title: "can't type quotation marks (&quot;) in bash!?"
date: 2006-05-14
forum: General Help
---

### Post by dave_m on 2006-05-14
Hello all,

I guess the title pretty much says it all: I can't type quotation marks ("") in bash. Instead, I get a little black square.

I have no problem typing the "quotation marks" anywhere else, except in bash.

Ubuntu 5.10
Acer TM 4001 WLMi

Thanks in advance,

Dave M.

(I also had to add a .inputrc file to allow me to use special characters &é#@è§, etc.)

---

### Post by dave_m on 2006-05-14
ok,

apparently my prompt (.bashrc) caused the black square instead of the ".

the real problems however are:
1. I can't use special characters (i.e. " ") in my (ubuntu) passwords 
2. I can't sudo in my ssh server (FreeBSD), which has some special characters (") in the password

If someone could point me in the right direction...

thanks again in advance

Dave M

---

### Post by steve.horsley on 2006-05-14
If you think it's something in .bashrc, you could try editing or renaming it, but you will have to logout/in again before a change in .bashrc is seen in the gui terminals.

---

### Post by dave_m on 2006-05-14
@steve.horsley
> If you think it's something in .bashrc
I honestly have no idea
>  you could try editing or renaming it, but you will have to logout/in again before a change in .bashrc is seen in the gui terminals
That's how I found out my prompt (PS1='...') causes the " character to display as a square.
If I change, it, the " character displays correctly, but the problems mentioned above (passwords & sudo) still remain.

I have no idea where to look next... keyboard/locale/...? any ideas?

Regards 

Dave M

---

### Post by dave_m on 2006-05-16
I installed ubuntu 5.10 with the US English language and Belgian (azerty) keyboard on an Acer Travelmate 4001WLMi. 
I chose the Acer Travelmate 800 as keyboard model.

On my remote BSD box, I use special characters (&é"§è etc.) in my passwords.

Windows:
(using Putty), I can use the sudo command on my remote ssh server, with no problems.

Ubuntu 5.10:
When I go to console (CTRL + ALT +F1) I can use the sudo command (special characters in password). When I go back to X (gnome) and try to sudo again, it no longer works.

Is there any file in Ubuntu I can edit (xorg.conf,...) or is there something else I can do to resolve this? (besides not using special characters in my passwords, obviously)

Kind Regards

Dave M.

---

### Post by bluenova on 2006-05-16
Make sure the keyboard setup in xorg.conf is (off the top of my head) nl-be
I've never had any problems with my girlfriends laptop (GB English, Belgian Keyboard).

---

### Post by dave_m on 2006-05-16
@bluenova,

here are my xorg.conf settings (regarding to the keyboard) as they are now:
(sudo doesn't work)
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection
```

Gnome keyboard settings:

Model: Acer Travelmate 800
Layout: Belgium

As for setting the XkbModel to "nl", don't they use qwerty in the netherlands, (belgium = azerty) or is that besides the point or did you mean I had to change it to "nl-be"?

Thanks,

Dave M.

---

### Post by bluenova on 2006-05-16
Yea I mean't nl-be (assuming you're in Flanders) but I'm not at home now, I can check in 3 hours, and let you know how it should be set. 'be' may be correct.

---

### Post by dave_m on 2006-05-16
That would be great!
I'll try the "nl-be" setting in the meantime.

Thanks,

Dave M.

---

### Post by bluenova on 2006-05-16
Sorry for the delay in getting back, it should be 'be' in xorg.conf and in gnome 'Belgium' Must be another issue, sorry.

---

### Post by dave_m on 2006-05-17
That's ok. 
I didn't find any mention of the "nl-be" in the /etc/X11/xkb/rules, so I didn't try the setting.

Stange thing is, for example: 
I create a testuser account (ex. user1) with special characters in the password.
At login, I enter the special characters in the login box to see if they display, and they do.
When I actually want to login with the user
   login: user1
   password: spéci@lcharactèr§"
I get nothing!
(If I do the same in console, no problem)

Anywho, thank you for your help!

Dave M.

---

### Post by flaimo on 2006-05-21
i have the same problem like dave_m. when i want to use special chars in my password it just doesn't work from the login screen.

---

