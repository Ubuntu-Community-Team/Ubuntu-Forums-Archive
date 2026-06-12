---
title: "Please Help! - Several Errors after restart"
date: 2010-10-24
forum: General Help
---

### Post by wiseguy12851 on 2010-10-24
This is a new installation of Ubuntu, everything was working great after installing the programs and configuring settings until a system restart brought these errors down:


[LIST]
[*]It cannot connect to the internet, I've tried everything even restarting the network with the terminal
[*]The windows do not have borders, I know this is a common problem but I've read through many different posts and nothing helps, this all happened at the exact same time and was working perfectly before
[*]When you logoff, shutdown, or end your session in any way it says there is an unknown program that won't quit, you have to end it because it will never end on it's own.
[/LIST]

I've restarted many times in the past but all this suddenly happens randomly, I have Ubuntu 10.10 32-bit and CompizFusion if that makes a difference.

---

### Post by inso_741 on 2010-10-24
Did you install anything...any updates, apps or drivers as such before that restart?

---

### Post by wiseguy12851 on 2010-10-24
Being a new installation I did install many things that I forgot to install before, however, one's that may be of interest are:


[LIST]
[*]CompizFusion Extra Plugins were added
[*]Edited the network file by hand to change it to static with the help of several websites & changed it in the Network Connections program
[/LIST]

That's about all of importance, I do have multiple accounts if that makes a difference.

About the network: I wanted a static ip so I edited the file and it did no good, so then I changed it through the network connections program and it worked, I'm guessing editing it 2 different ways might have caused the network error (rough guess) but I'm loss at to the other errors.

Maybe CompizFusion is corrupt???

---

### Post by argedion on 2010-10-24
take off CompizFusion I've had trouble with it in the past now I just don't bother your graphics card may not be supported by CompizFusion.

---

### Post by wiseguy12851 on 2010-10-24
This is going to sound odd, I fixed all the problems at once by accident - I simply replaced the modified network files with the original and restarted the computer hoping to at least have my network back up and running.

More than that everything is back up and running even the window borders and CompizFusion is working great. Somehow all these errors are tied into

/etc/network/interfaces &
/etc/resolv.conf

and simply replacing them with the originals fixed everything.
I even have my static IP working again from Network Connections Program.

A bit odd but everything is working again, the only problem I have now appears to be really minor and it's that "Unknown Program" that won't terminate when ending session but it appears to have no effect on anything.

---

### Post by inso_741 on 2010-10-25
If you ever get windows w/o borders try:
```
compiz --replace
```
or 
```
metacity --replace
```

---

### Post by wiseguy12851 on 2010-10-25
I did get no windows again, I'm not at home to try the solution yet but right when everything is going fine I launch a new program "vba-m", nothing happens, then the task bar locks up. After I restart with the terminal no window borders again.

---

