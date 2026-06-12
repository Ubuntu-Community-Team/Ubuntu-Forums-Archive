---
title: "Setting environment variable"
date: 2011-08-24
forum: General Help
---

### Post by 8tr4k on 2011-08-24
I had some issues where my web cam wouldn't work in the browser but would work in cheese and ws4gl. After some poking around I found the following fix:

If I run in terminal

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox

I can get the cam working in firefox. The issue is I need to run this everytime I want to start the browser AND (of course) this doesn't allow the use of the cam in chrome. 

I assumed (n00b here) that this was an environment issue so I attempted to edit my /etc/environment and include the above line. After reboot it still didn't work. 


[U]Question is am I putting this in the right place? And what is the syntax to make this load on boot?
[/U]

</etc/environment >

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

<-->

Thanks in advance!

---

### Post by papibe on 2011-08-24
The file /etc/environment is not the place for that. Try to put it in one of the following files:
```

~/.bash_profile
~/.bash_login
~/.profile
```
Hope it helps,
Regards.

---

### Post by raja.genupula on 2011-08-24
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)


look at this

---

