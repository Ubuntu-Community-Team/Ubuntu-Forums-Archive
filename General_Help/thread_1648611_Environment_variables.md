---
title: "Environment variables"
date: 2010-12-19
forum: General Help
---

### Post by bakinsoda on 2010-12-19
Hi,

I'd like to set and export an environment variable either for the user or globally (system-wide) that affects the way a program behaves (i currently have to type something like "VAR=MYVAR MyApp" in a terminal.  I'd like the environment variable to be set in all bash sessions, in all applications launched using the Gnome Menu, and launched using Alt-F2.  I think the last two are the hardest to satisfy.

I've tried modifying
~/.bashrc
~/.profile
~/.pam_environment
~/.gnomerc
/etc/environment
/etc/profile
/etc/X11/Xsession

as many threads have suggested.  Is the environment variable setting mechanism in Ubuntu still broken per [this]("http://newyork.ubuntuforums.org/showthread.php?t=1889") thread?

Thanks.

---

### Post by gmargo on 2010-12-19
I did some testing under 10.10 Maverick and found four different locations where you could place environment variables that will carry over in the conditions you stated.  To test, I placed unique environment variables in all the possible candidates and logged which ones came up under each condition.
```

/etc/environment
/etc/profile
/etc/profile.d/env_setting_script.sh
$HOME/.profile

```

---

### Post by bakinsoda on 2010-12-19
Is it because I'm setting LD_PRELOAD then?  Could you test this?

Can you try setting PATH to "" in some of those, and see what happens when you launch using Alt-F2?

---

### Post by gmargo on 2010-12-19
> **bakinsoda said:**
> Is it because I'm setting LD_PRELOAD then?  Could you test this?

Can you try setting PATH to "" in some of those, and see what happens when you launch using Alt-F2?
I don't know.  No.  No.

If you're having a problem with one particular application, you could just launch it from a shell script that makes sure the environment is correct.

---

### Post by efflandt on 2010-12-19
There must be something wrong with the way you are setting or exporting the variable.  Note that if you set something in .bashrc, it might not show in the terminal you edited it from.  For example I added the following to .bashrc:

```
export EDITOR=nano
```  If I do following in the terminal I edited .bashrc from, it comes up empty:
```
efflandt@natty-ssd:~$ **echo $EDITOR**

efflandt@natty-ssd:~$
```But if I open another terminal, it is set there:
```
efflandt@natty-ssd:~$ **echo $EDITOR**
nano
efflandt@natty-ssd:~$
```Give a complete example of what you added to .bashrc or elsewhere to set/export a variable.

---

### Post by bakinsoda on 2010-12-19
Hi everyone,

Thank you for your responses.  The variable I'm trying to set is "LD_PRELOAD" (my working command is "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" and the likes).  I tested setting a variable (TEMPORARY) in "/etc/profile" and it does indeed work.  I think LD_PRELOAD get's set somewhere in the variable loading scripts (hence overwriting my definition in "/etc/profile").

So I guess it is specific to the LD_PRELOAD variable...

Let me know of any suggestions.

---

