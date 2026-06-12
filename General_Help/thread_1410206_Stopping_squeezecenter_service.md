---
title: "Stopping squeezecenter service"
date: 2010-02-18
forum: General Help
---

### Post by nickhopkins07 on 2010-02-18
Hi guys,

I'm trying to install MythTV, but am running into a few problems, I've been told it might be because I already have Squeezecentre installed, and as that installs its own SQL 'Thing' (you can see I'm not very techie!!) it's getting in the way. So I want to stop the squeezecentere service and retry mythtv to confrim if that is indeed the problem. I'm having trouble though, I've given the new a good search, and from what I can see, the following is what I need to type in the terminal:

> sudo /etc/init.d/squeezecenter stop



But I'm just told the command is not found.

I'm running the latest version of Ubuntu and version 7.4.1 of squeeze server, any help most grateful.

Thanks!

---

### Post by jamesisin on 2010-02-18
Squeezecenter is the old name for the service.  It's now called squeezeboxserver.

Check if you have either installed with these two commands:

```
which squeezecenter
which squeezeboxserver
```

If you get a result for either one, you have that one installed.

You can take a look in your init.d folder to see if either of these deamons exist:

```
ls /etc/init.d | grep squeeze
```

Once you have this information you should be able to adjust your stop command accordingly.

---

### Post by nickhopkins07 on 2010-02-18
Thanks James, that worked a treat. Much appreciated

---

### Post by jamesisin on 2010-02-18
Great.  Let me know what you think of MythTV.  I'm working out kinks in a FLAC serving media machine on my network at present.

---

### Post by nickhopkins07 on 2010-02-18
I will, if I ever get it working, sadly it doesn't seem it was the squeezeserver issue that was causing the problem! I get the impression it has something to do with the MythTv user account, as when I run the following
 
> mysql -umythtv -p mythconverg
 
And enter my Mytv password, I get an access denied message, which would seem to point to why It cant do the final leg of the setup process.

---

### Post by jamesisin on 2010-02-18
I wish I knew more about MySQL.  I would make a new thread for this specific issue.

---

### Post by nickhopkins07 on 2010-02-18
Yeah I think i will.
 
Thanks for your help though.:KS

---

### Post by jamesisin on 2010-02-18
No problem.

You'll probably want to mark this thread as SOLVED under Thread Tools above.

---

