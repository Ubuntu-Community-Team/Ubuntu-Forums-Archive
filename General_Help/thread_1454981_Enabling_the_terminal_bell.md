---
title: "Enabling the terminal bell"
date: 2010-04-15
forum: General Help
---

### Post by Blue-Tiger on 2010-04-15
Hi there!
I've recently installed Xubuntu Lucid Beta2 on my new laptop. But I'm unable to turn the bell back on.

the 'pcspkr'-module is removed from the blacklist and is loaded. However, 'alsamixer' doesn't show me any volume-options for the beep. 

However, 'echo -e "\a"' still doesn't make a sound :(
I've installed the 'beep'-package, and it works, thus I am assuming that the hardware-bell itself does WORK fine. It's just deactivated/muted somewhere, and I can't find the option to turn it back on :(

Please help me :)

---

### Post by Blue-Tiger on 2010-05-15
*bump*

---

### Post by Penguin Guy on 2010-05-15
Have you checked [COLOR="Green"]_E_dit -> Pr_o_file Preferences -> Terminal _b_ell[/COLOR]?

---

### Post by Blue-Tiger on 2010-05-15
> **Penguin Guy said:**
> Have you checked [COLOR="Green"]_E_dit -> Pr_o_file Preferences -> Terminal _b_ell[/COLOR]?

Hi and thanks for your reply.

There is no such option in the XFCE Terminal, however the bell is turned on in the XFCE Terminal:

```

tom@blulap:~$ grep -i bell .config/Terminal/terminalrc 
MiscBell=TRUE

```

Also, the beep is not audible in xterm and stjerm either. However, I can hear it if i manually on TTY1 (using STRG+ALT+1 to get there) if I log in there and enter 'echo -e "\a"'

---

