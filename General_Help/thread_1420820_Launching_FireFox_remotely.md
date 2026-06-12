---
title: "Launching FireFox remotely"
date: 2010-03-03
forum: General Help
---

### Post by metpage on 2010-03-03
Whenever im logged into my Ubutu Desktop at home remotely from work i cannot seem to launch Firefox by clicking on any of the shortcuts.

Seems the only thing that lets me lauch it is by opening a command windown and typing "sudo firefox"

When im at home, link works just fine


What can i do to fix this?


FYI Im running the following:
Firefox 3.5.8
Ubuntu 9.10

---

### Post by jdk82 on 2010-03-03
What happens if you try

```
firefox
```

from the command line?

---

### Post by Bradj47 on 2010-03-03
> **metpage said:**
> Whenever im logged into my Ubutu Desktop at home remotely from work i cannot seem to launch Firefox by clicking on any of the shortcuts.

Seems the only thing that lets me lauch it is by opening a command windown and typing "sudo firefox"

When im at home, link works just fine


What can i do to fix this?


FYI Im running the following:
Firefox 3.5.8
Ubuntu 9.10

If you are running it remotely, how did you set it up so that you just click a launcher? The way I run programs remotely is: 
```

$ ssh yyy.yyy.y.yyy
<password>
$ csh
% setenv DISPLAY xxx.xxx.x.xxx:0.0
% firefox

```
*xxx.xxx.x.xxx being the ip address of the local computer and yyy.yyy.y.yyy being the ip address of the computer you are connecting to remotely.*
Could you paste the code that you put in the launcher?

---

### Post by jdk82 on 2010-03-03
@ Bradj47
Unless I completely misunderstood the OP's post, it looks like he is trying to log in via vncviewer. If this is not the case, could the OP give more details as to the setup and the software in question?

Josh

---

### Post by bodhi.zazen on 2010-03-03
Firefox is a funny application that way.

Are you using ssh ? VNC over ssh ?

When using ssh -X you need the -no-remote option.

```
firefox -no-remote
```

It would also help if you start firefox in a terminal and post any error messages you may get.

---

### Post by metpage on 2010-03-04
OK i'm using a WinXP machine from work and connecting to my home computer via NX Client.

Using the command line and type "firefox" it just hangs

Only way i can get it to run is if i type "sudo firefox"

when i login and click the link to launch firefox it proceeds to launch then disappears (get the "starting firefox web browser" on the task bar then it goes away).

---

### Post by bodhi.zazen on 2010-03-04
> **metpage said:**
> OK i'm using a WinXP machine from work and connecting to my home computer via NX Client.

Using the command line and type "firefox" it just hangs

Only way i can get it to run is if i type "sudo firefox"

when i login and click the link to launch firefox it proceeds to launch then disappears (get the "starting firefox web browser" on the task bar then it goes away).

Try 

```
firefox -no-remote
```

If that works we can make a custom launcher.

---

### Post by metpage on 2010-03-04
hmm just tried that and it didn't do anything, it still hangs

---

### Post by bodhi.zazen on 2010-03-04
Not sure why it hangs. Does it work when you are in front of the box (without connecting from remote ?).

Perhaps it is a corrupt profile ?

You can try starting firefox either with a new profile or in safe mode.

```
firefox -P
```

---

