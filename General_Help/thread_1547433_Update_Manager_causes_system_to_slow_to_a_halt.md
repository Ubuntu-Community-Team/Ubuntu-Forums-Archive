---
title: "Update Manager causes system to slow to a halt"
date: 2010-08-06
forum: General Help
---

### Post by josejuan05 on 2010-08-06
I'm running Lucid on a Compaq nc6000 laptop with a 1.6 GHz Pentium 4/m and 512 MB DDR. Most of the time my performance is acceptable (a bit slow, but if I needed more performance I could turn a bunch of options down).

Anways, for some reason when Update Manager auto-runs it causes the whole computer to slow to a halt - inputs like clicking or typing hang until the screen shows up stating "Software updates are available to this computer."

I have run Update Manager by itself and it doesn't seem to cause the system hang that the autorun does. Performing the updates from the terminal doesn't seem to cause hang either. If I kill the update-manager process ('pkill update-manager') the system becomes responsive again.

I've resorted to disabling the automatic update check at startup (from the "Software Sources" panel). This isn't causing any real problems, as I am pretty anal-retentive about running the updates manually anyways. Still, I was wondering if anyone had any ideas what might cause this slowing behaviour.

Oh, and this behaviour is the same no matter how fast my internet connection is - at the University I can get 3 MB/s downloads yet still experience prolonged periods of system lag when Update Manager autoruns.

---

### Post by Cavsfan on 2010-08-06
Try this instead These 3 commands will get the updates.
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Just make sure that when something is removed without anything to replace it.
Then you want to just wait a while.

I never use Update Manager - I always use these 3 commands.

---

### Post by josejuan05 on 2010-08-06
Oh, yes, this is what I typically do. I just wondered if anyone might know of a reason why Update Manager would cause this behavior.

---

### Post by cmcanulty on 2010-08-06
Or add this to your bash.rc file in home really speeds it up. Then just type ud in terminal enter password and done. Sometimes asks for a yes to download a file.
```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
```

---

### Post by Cavsfan on 2010-08-07
> **cmcanulty said:**
> Or add this to your bash.rc file in home really speeds it up. Then just type ud in terminal enter password and done. Sometimes asks for a yes to download a file.
```
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
```

That sounds like a great idea! Except I am not presently very knowledgeable about bash and scripts. I found this reference manual though 

_[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)_

Would you mind explaining what I would have to do to accomplish the above step?
I didn't see a "bash.rc" file in my home directory. Probably have to make it right?
Thanks in advance.

Sorry OP! Didn't realize I was posting off topic stuff on your thread.

---

### Post by cmcanulty on 2010-08-08
the bash.rc is there , just click in your home folder to view hidden files then just add that line to the file.

---

### Post by Cavsfan on 2010-08-08
> **cmcanulty said:**
> the bash.rc is there , just click in your home folder to view hidden files then just add that line to the file.
Thanks! :D

---

### Post by phredbull on 2010-11-05
I have the same problem; Compaq laptop, P4 processor, Update Manager auto-checks for updates, and my computer becomes unusably laggy. All the above replies are workarounds, but is there a reason for this behaviour, and a solution?

---

### Post by Cavsfan on 2010-11-05
> **phredbull said:**
> I have the same problem; Compaq laptop, P4 processor, Update Manager auto-checks for updates, and my computer becomes unusably laggy. All the above replies are workarounds, but is there a reason for this behaviour, and a solution?
A friend calls it "Update Mangler". The above 3 commands and the scripts to run them are not workarounds.
They are the way some of **choose** to get our updates. I only use Update Mangler to see info about the updates 
and then close it and use the CLI commands to actually get the updates.
It a matter of preference.

You could check if there is a bug filed on it if you want and file one if there is none.

---

### Post by phredbull on 2010-11-05
> **Cavsfan said:**
> I only use Update Mangler to see info about the updates 
and then close it and use the CLI commands to actually get the updates.
You open a GUI tool, then open a terminal to execute the commands? Seems like jumping through hoops to accomplish something that is *supposed* to happen (at least partly) automatically.

---

### Post by Cavsfan on 2010-11-06
> **phredbull said:**
> You open a GUI tool, then open a terminal to execute the commands? Seems like jumping through hoops to accomplish something that is *supposed* to happen (at least partly) automatically.

I like to make simple things difficult.

---

