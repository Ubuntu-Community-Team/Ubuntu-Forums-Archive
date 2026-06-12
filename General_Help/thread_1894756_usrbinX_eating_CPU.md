---
title: "/usr/bin/X eating CPU"
date: 2011-12-13
forum: General Help
---

### Post by elvisd on 2011-12-13
Hi all,

Ubuntu 11.10 with unity 3d.

I have an issue with a process, eating 20% to 50% CPU sometimes the system remains almost unresponsive with that process eating 100% cpu power.

the process is /usr/bin/X
exactly the command looks like:
```
/usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
```

why is this process so cpu intensive?

---

### Post by BC59 on 2011-12-13
It's an old bug:

/usr/bin/X leaks memory with firefox

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/111299](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/111299)

---

### Post by elvisd on 2011-12-13
Hi BC59, thank you for your quick response.
But currently I haven't FF open, I open it once or twice a day to check e-mail on my secondary account... This bug is inactive since middle of 2010...

---

### Post by BC59 on 2011-12-13
Look if you can tweak something with Jupiter:

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by elvisd on 2011-12-13
I don't understand how could I solve my issue using jupiter...

---

### Post by elvisd on 2011-12-14
I have tried to avoid using FF and I confirm that the /usr/bin/X isn't eating my cpu anymore.
strange is that in another pc this isn't happening. some thoughts?

---

### Post by supercheetah on 2011-12-14
Do you have a lot of tabs open?  My computer always slows down and processor usage goes up when there is lots of tabs open in Firefox (I have tabitis, I admit), and so I'm forced to close a number of them, and then also clear the cache from Firefox.

Although, honestly, I'm mostly using Chrome now, so it hasn't really been an issue.

---

### Post by elvisd on 2011-12-14
Hi have 2 to 5 tabs open in FF, not many cause i used it to check emails on a secondary account.
i use chromium a lot more too.

what is really strange about this issue is that the process eats cpu even after i close ff.

---

### Post by supercheetah on 2011-12-14
What do you see in *top* or System Monitor (under the Processes tab)?  You should be able to find the culprits there.

---

### Post by elvisd on 2011-12-14
the process is that described in main post..

---

### Post by anaspeople on 2012-01-17
Did you find out why this happens?
I'm having the same issue here with a NVIDIA GeForce 8400M GS. Using propietary current driver in Ubuntu 11.10.

---

### Post by elvisd on 2012-01-18
Hi anaspeople,

I have found on another thread (sorry I haven't the link anymore) that states this issue is caused by Firefox.
I have stopped using firefox and the problem has gone.

Sorry I can't offer you a solution but only a work-around.

---

