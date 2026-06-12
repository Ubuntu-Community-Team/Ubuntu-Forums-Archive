---
title: "how to get error report logs?"
date: 2012-08-12
forum: General Help
---

### Post by LLCoolJeff on 2012-08-12
I don't know if I am just tired or what, but I cannot find out how to obtain error report logs...

I had an error that resulted in this screen:

[IMG]http://i49.tinypic.com/aysf8h.png[/IMG]

and I was wondering how I would find out if:

1. This is serious?
2.where to look for the log in case I should have to post it somewhere for help?

Thanks...

---

### Post by llamabr on 2012-08-12
(I love that ubuntu just tells you to solve the problem by rebooting.  When did we go so wrong?).

error logs are kept in /var/logs/.
 
To answer your first question, if everything seems to be working well, probably it's nothing to worry about.  If everything is not well, describe your problem, and we can help.

---

### Post by TheFu on 2012-08-12
That looks like an error with the most popular software debugger for UNIX systems, gdb. If you are writing compiled code, then you should be using that tool. If you are not writing compiled code, I'd worry if that tool was being used at all. It is doubtful that your system even has it installed.

If you intend to use gdb, there are lots of how-to documents. It is a very simple to use debugger, but extremely deep once you learn the more advanced features. Many people use it directly, but more and more, developers will have a GUI tool as a layer to gdb.

So, if you are a software developer - you should worry.
If you are not, don't worry at all.

I am shocked that Ubuntu is suggesting a system reboot might help.  A system reboot is the last thing I try after looking for answer for a few days first. It simply isn't needed 99.999999999999999% of the time.

---

### Post by LLCoolJeff on 2012-08-12
> **llamabr said:**
> (I love that ubuntu just tells you to solve the problem by rebooting.  When did we go so wrong?).

error logs are kept in /var/logs/.
 
To answer your first question, if everything seems to be working well, probably it's nothing to worry about.  If everything is not well, describe your problem, and we can help.

cool thanks..

Not expecting any answer to this, but heres the log in case anyone is bored and wants to tell me what it means:

```
ERROR: apport (pid 3388) Sun Aug 12 06:24:35 2012: called for pid 3385, signal 11
ERROR: apport (pid 3388) Sun Aug 12 06:24:35 2012: executable: /usr/bin/gdb (command line "/usr/bin/gdb -ex attach\ 27151 --ex info\ threads --ex thread\ apply\ all\ bt --batch")
ERROR: apport (pid 3388) Sun Aug 12 06:24:35 2012: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 3388) Sun Aug 12 06:24:35 2012: debug: session gdbus call: 
ERROR: apport (pid 3388) Sun Aug 12 06:24:35 2012: wrote report /var/crash/_usr_bin_gdb.1000.crash
```

System is running fine so it doesn't look to serious but I never know because I don't kow how to put much meaning to anything in there...

---

### Post by LLCoolJeff on 2012-08-12
> **TheFu said:**
> That looks like an error with the most popular software debugger for UNIX systems, gdb. If you are writing compiled code, then you should be using that tool. If you are not writing compiled code, I'd worry if that tool was being used at all. It is doubtful that your system even has it installed.

If you intend to use gdb, there are lots of how-to documents. It is a very simple to use debugger, but extremely deep once you learn the more advanced features. Many people use it directly, but more and more, developers will have a GUI tool as a layer to gdb.

So, if you are a software developer - you should worry.
If you are not, don't worry at all.

I am shocked that Ubuntu is suggesting a system reboot might help.  A system reboot is the last thing I try after looking for answer for a few days first. It simply isn't needed 99.999999999999999% of the time.

Whoa, thanks for the reply, but your first line messed with my head a little bit, you said

> If you are not writing compiled code, I'd worry if that tool was being used at all 

does that mean I should be worried? Like my system is compromised? I know that may sound extreme, but I just didn't know how to take it.

FYI I am not writing any kind of code, compiled or not..lol

---

### Post by nothingspecial on 2012-08-12
gdb is a debugger.

You are being told that there is a bug with your debugger.

you should report a bug against it by clicking continue.

I wouldn't have though that that it is serious.

---

### Post by TheFu on 2012-08-12
> **LLCoolJeff said:**
> does that mean I should be worried? Like my system is compromised? I know that may sound extreme, but I just didn't know how to take it.

FYI I am not writing any kind of code, compiled or not..lol
if you **are **a software developer - you should **worry**.
If you** are not** a software developer, **do not worry** at all.

---

