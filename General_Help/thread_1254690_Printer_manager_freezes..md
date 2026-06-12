---
title: "Printer manager freezes."
date: 2009-08-31
forum: General Help
---

### Post by zippyties on 2009-08-31
Whenever i try to open the printer configuration tool(system-->administration-->printing), it turns dark grey and stops responding.  I haven't done anything special with this tool it just decided to stop working one day.

I did however upgrade to python 3 right around this time, could this be my problem?

Is there a command to run this tool from the command line so that I can see where the error lies?

thanks,

---

### Post by plucky on 2009-08-31
> **zippyties said:**
> Whenever i try to open the printer configuration tool(system-->administration-->printing), it turns dark grey and stops responding.  I haven't done anything special with this tool it just decided to stop working one day.

I did however upgrade to python 3 right around this time, could this be my problem?

Is there a command to run this tool from the command line so that I can see where the error lies?

thanks,

Try ```
/usr/bin/system-config-printer
```

or just ```
system-config-printer
```


Also post output from a terminal of ```
id
```Make sure you have "lpadmin" privilege.


Good Luck

---

### Post by mikkellund42 on 2009-09-11
> **zippyties said:**
> Whenever i try to open the printer configuration tool(system-->administration-->printing), it turns dark grey and stops responding.

I have exactly the same problem. When I type system-config-printer --debug from a terminal I get
```
~$ system-config-printer --debug
Connected as user me
refresh
Created subscription 64
<monitor.Monitor instance at 0x9e5c42c>: printers and jobs lists provided
update_jobs
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
Authentication pass: 1
Authentication: password callback set
```
When the Printer Configuration window is running, some python process is using a lot of CPU power.

```
~$ id
uid=1000(me) gid=1000(me) groups=4(adm),20(dialout),24(cdrom),44(video),46(plugdev),106(lpadmin),122(sambashare),1000(me)
```

I have no idea what this means, so any help is really appreciated. The printer configuration was working nicely just last week, and I haven't changed anything (at least not deliberately).

---

### Post by zippyties on 2009-09-11
So here is what I did to fix it.

It seemed to me like the computer - printer relationship was fine, I was able to access the cups interface by putting ```
http://localhost:631/
``` into the address bar on firefox.

This lead me to the actual printer manager program, I tried reinstalling but continued to have the same problem.

Next I figured that something was causing the program to wait for something it wasn't getting (I tried running it from the terminal and though the program hung it returned no errors in the terminal). 

So I uninstalled all of my printers and retried the program.  This time it worked and it continues to work.

It seems to be the drivers I attempted to manually install for the office Sharp MX 4501n(the default drivers will not work in a network printing environment).

I'm sorry for my weird trouble shooting method, but I am pretty new to Linux.

please post back if this works for you,

---

### Post by mikkellund42 on 2009-09-11
> **zippyties said:**
> I was able to access the cups interface by putting ```
http://localhost:631/
``` into the address bar on firefox.

So I uninstalled all of my printers and retried the program.  This time it worked and it continues to work.

You are a genius! Apparently one of my network printers was making the system hang.

Thanks a lot :D

---

