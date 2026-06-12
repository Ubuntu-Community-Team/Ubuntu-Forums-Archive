---
title: "Google Chrome won't auto-start!"
date: 2011-03-25
forum: General Help
---

### Post by ANTlabs on 2011-03-25
Hi everyone, I tried to autostart my chromium browser when I log in. It worked great the first time! But when I restarted, nothing happened! I checked the startup apps and it wasn't there. I've repeated this process several times and been all over the web, but i'm stumped!  :confused:

---

### Post by luceerose on 2011-03-25
Post the actual command that you added to startup apps ?

---

### Post by ANTlabs on 2011-03-25
/usr/bin/chromium-browser %U

 I found this in my main menu where I manually start chrome.

---

### Post by scouser73 on 2011-03-26
Try **chromium-browser %U**, it may work.

---

### Post by ANTlabs on 2011-03-26
Tried it, same thing. Works for one boot, then goes away.

---

### Post by RgnKjnVA on 2011-04-14
I was having the exact same problem until just now. The only thing that works for me is to call a perl script to start chromium-browser. Call the file 'chromium-startup' or some such. Then Add an item to the Startup Applications. Seems a bit silly but it's finally working for me on Linux Mint 10.

Verify your perl install path:

laptop:~/Scripts$ **which perl**
/usr/bin/perl


```
#!/usr/bin/perl

system ("chromium-browser &");

exit 0;

```

---

### Post by statikeffeck on 2011-05-14
This is so odd. Same thing happens with Google Chrome browser (it doesn't remove the entry for me, it just doesn't auto start).

I wonder if Google doesn't want you to auto start the browser?

---

### Post by shashanksingh on 2011-05-14
Same problem with me, it also removes the entry after reboot.

A manul entry in .profile worked for me.

---

