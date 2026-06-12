---
title: "Firefox crashes with certain google search"
date: 2009-08-27
forum: General Help
---

### Post by dopple on 2009-08-27
I wsx trying to install .net 3.5 using wine but it crashed due to background intelligent transfer service. That's not my problem however. The problem is when I went to google what the issue might be my browser crashed. whenever I google "background intelligent transfer service" firefox closes and I have to restart. Any ideas?

EDIT: Also happens on yahoo. I'll post back if it happens with any other search.

---

### Post by j7%&lt;RmUg on 2009-08-27
Try getting rid of any remnants of .net 3.5, i highly doubt that its a coincidence, although it is one of the strangest things iv ever heard of happening to a user.

---

### Post by P4man on 2009-08-27
Just when you thought you had seen it all, you read about an error like that lol.

Wild guess: it has something to do with autocomplete?

Try renaming your firefox profile folder, and see if the problem persists.

---

### Post by P4man on 2009-08-27
and another thought: you have enough free space on your root and home ?

---

### Post by dopple on 2009-08-29
Hi. I also found that searching for "translation" will crash firefox as well. I renamed ~/.mozilla/firefox and restarted firefox. Same problem.
This is bizarre.

---

### Post by P4man on 2009-08-29
launch firefox from a terminal, you might get an error that gives you some hint of whats going on.

---

### Post by dopple on 2009-08-30
Ok. Here is the error in the terminal post-crash.
```
graham@graham-laptop:~$ firefox
loaded md5.js
Greasemonkey getFirebugConsole() error:
(new TypeError("chromeWin.Firebug is undefined", "file:///home/graham/.mozilla/firefox/0bylztl2.default/extensions/%7Be4a8a97b-f2ed-450b-b12d-ee082ba24781%7D/components/greasemonkey.js", 392))
Greasemonkey getFirebugConsole() error:
(new TypeError("chromeWin.Firebug is undefined", "file:///home/graham/.mozilla/firefox/0bylztl2.default/extensions/%7Be4a8a97b-f2ed-450b-b12d-ee082ba24781%7D/components/greasemonkey.js", 392))
Greasemonkey getFirebugConsole() error:
(new TypeError("chromeWin.Firebug is undefined", "file:///home/graham/.mozilla/firefox/0bylztl2.default/extensions/%7Be4a8a97b-f2ed-450b-b12d-ee082ba24781%7D/components/greasemonkey.js", 392))
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 27890 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by dopple on 2009-10-06
Bump. 
It's not only searches, it happens when I access my banks website.

Also, it doesn't seem to be isolated to firefox. I tried on the epiphany browser and the same thing happens. Doesn't happen on either of the other 2 accounts on my laptop.

---

