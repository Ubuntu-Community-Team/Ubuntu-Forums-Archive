---
title: "Synaptic manager will not open"
date: 2009-11-30
forum: General Help
---

### Post by dmaneleven on 2009-11-30
how to resolve this in synaptic package manager error . It will not open

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
An update was accidentally interupted.

---

### Post by Geoff918 on 2009-11-30
> **dmaneleven said:**
> how to resolve this in synaptic package manager error . It will not open

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
An update was accidentally interupted.

Open up terminal (Applications - Accessories - Terminal)

sudo dpkg --configure -a

Basically something broke on a recent update you ran, or failed to complete successfully. dpkg has to satisfy itself and then life will resume happily. :)

---

### Post by dmaneleven on 2009-11-30
> **Geoff918 said:**
> Open up terminal (Applications - Accessories - Terminal)

sudo dpkg --configure -a

Basically something broke on a recent update you ran, or failed to complete successfully. dpkg has to satisfy itself and then life will resume happily. :)

I now get this" sudo dpkg --configure -a
dpkg: status database area is locked by another process"

---

### Post by QIII on 2009-11-30
You can only have one instance of apt/synaptic running at a time.

Close Synaptic and use the terminal with the command given.

---

### Post by bumanie on 2009-11-30
You probably have something like software centre or synaptic package manager open at the same time when trying to run the code in terminal. You can only have one admin process operating at the one time. Ensure you have everything else closed, then open terminal, put in the command, it should work as expected.

---

### Post by Geoff918 on 2009-11-30
What they said. Any update process--Update Manager. Any running Synaptic process needs to be closed.

That includes any installs at CLI.

If you're totally in doubt, just reboot, and run the command.

---

### Post by qjmoss on 2009-11-30
> **Geoff918 said:**
> What they said. Any update process--Update Manager. Any running Synaptic process needs to be closed.

That includes any installs at CLI.

If you're totally in doubt, just reboot, and run the command.

+1

This should work.

---

### Post by nazgulord on 2009-11-30
Out of curiosity, could it ever happen that Synaptic crashes but the lock file remains, thus causing the error?

---

### Post by dmaneleven on 2009-11-30
tried all the above but still synaptic wont work. where do I go to close other instalers?

---

### Post by dmaneleven on 2009-12-01
I get the red "X" saying that "apt" or "aptitude must be terminated first"
This is really frustrating I've tried:

     Code:
     sudo apt-get install -f 
     Code:
     "sudo dpkg --configure -a " this code just frezes at "moodle...."
     Code:
     sudo apt-get update 
also tried"

sudo killall apt
sudo killall apt-get
sudo killall aptitude
sudo killall synaptic
sudo killall dpkg
sudo rm /var/lib/dpkg/lockbut nothing works.no processes found but it seems to work in the background and is stuck. I was trying to install Vuze and got a message that something about"moodle" or something.....help! everytime I encounter anything containingt moodle my machine refuses to open synaptic package manager. I cant even run update manager

---

### Post by wilee-nilee on 2009-12-01
You have three almost identical threads this is frowned upon and will get you very little help.
[http://ubuntuforums.org/showthread.php?t=1331300](http://ubuntuforums.org/showthread.php?t=1331300)
[http://ubuntuforums.org/showthread.php?t=1342365](http://ubuntuforums.org/showthread.php?t=1342365)

---

### Post by dmaneleven on 2009-12-01
> **wilee-nilee said:**
> You have three almost identical threads this is frowned upon and will get you very little help.
[http://ubuntuforums.org/showthread.php?t=1331300](http://ubuntuforums.org/showthread.php?t=1331300)
[http://ubuntuforums.org/showthread.php?t=1342365](http://ubuntuforums.org/showthread.php?t=1342365)

Forgive me please, but each instance seems unique and previous code fixes have since failed.neither instance was intentional but honest attempts to install apps resulting in crashes of terminal or SPM.

---

### Post by dmaneleven on 2009-12-01
" subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ultimate-g15-toys:
 ultimate-g15-toys depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing ultimate-g15-toys (--configure):
 dependency problems - leaving unconfigured
Setting up moodle (1.9.4.dfsg-0ubuntu4) ..."

This prevents me from accessing SPM updates and Software/app installs.

---

### Post by wilee-nilee on 2009-12-01
> **dmaneleven said:**
> Forgive me please, but each instance seems unique and previous code fixes have since failed.neither instance was intentional but honest attempts to install apps resulting in crashes of terminal or SPM.

I forgive you but the help you have received buy opening a new thread is lost, the original help should have fixed the problem. 

When you have problems make sure you list everything you have tried besides what you have been told to do and in what order. If you mess around to much by being impatient then it can be a much longer process and possibly leave you with no working fixes, basically because we all have our limitations in sticking with a person to help or in the amount of knowledge we have.

---

### Post by mo.reina on 2009-12-01
i'm no expert on this, but whenever i run into dependency problems i just type:

**sudo apt-get install -f**

usually takes care of that

---

### Post by audiomick on 2009-12-01
> **dmaneleven said:**
> " subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ultimate-g15-toys:
 ultimate-g15-toys depends on g15daemon; however:
[COLOR="Red"]**  Package g15daemon is not configured yet.**[/COLOR]
dpkg: error processing ultimate-g15-toys (--configure):
 dependency problems - leaving unconfigured
Setting up moodle (1.9.4.dfsg-0ubuntu4) ..."

This prevents me from accessing SPM updates and Software/app installs.

That would likely be your problem. Find out what that is and try and configure it.

---

### Post by dmaneleven on 2009-12-01
> **wilee-nilee said:**
> I forgive you but the help you have received buy opening a new thread is lost, the original help should have fixed the problem. 

When you have problems make sure you list everything you have tried besides what you have been told to do and in what order. If you mess around to much by being impatient then it can be a much longer process and possibly leave you with no working fixes, basically because we all have our limitations in sticking with a person to help or in the amount of knowledge we have.
Well I'm not "impatient" I'm just becoming aware of the P.I.T.A. Ubuntu can be to a newb:p I also see that some forum members are a little uptight.

---

### Post by wojox on 2009-12-01
Try:

```
sudo dpkg -P moodle
```

---

### Post by dmaneleven on 2009-12-01
> **wojox said:**
> Try:

```
sudo dpkg -P moodle
```


thank you, but no good results- all I got was: " status database area is locked by another process" Everytime I cannot open SPM it's because of some "moodle"error or a g15 not configured. I have no idea about either. you see I'm used to Window's "control/alt/delete"-Task manager, but Ubuntu has no similar function to force apps to close.I like the concept of UBUNTU but man it trying at times.

---

### Post by dmaneleven on 2009-12-01
> **audiomick said:**
> That would likely be your problem. Find out what that is and try and configure it.
how do I configure g15daemon

---

### Post by lidex on 2009-12-01
Enter this command in a terminal:
```
sudo dpkg --configure g15daemon
```

---

### Post by cariboo on 2009-12-01
Please don't create multiple threads about the same problem. I have merged your 3 threads.

---

### Post by ed-koala on 2009-12-01
System - Administration - System Monitor ... Processes tab shows you your running processes and allows you to stop them.

Be warned though, stopping the wrong process can have serious negative effects on your session, and might lock you up, so be sure of what you are stopping.

---

### Post by lidex on 2009-12-01
If you want gui for running processes use key-combo Alt+F2 and enter ```
gnome-system-monitor
```

---

### Post by dmaneleven on 2009-12-02
> **lidex said:**
> Enter this command in a terminal:
```
sudo dpkg --configure g15daemon
```

tried this code but I get this:
"Setting up g15daemon (1.9.5.3-3) ...
Starting g15daemon: invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 g15daemon"
But got synaptic package manager to respond. Thank you.

---

### Post by lidex on 2009-12-02
Tell me what you think about this post:
[http://ubuntuforums.org/showpost.php?p=7389996&postcount=8]("http://ubuntuforums.org/showpost.php?p=7389996&postcount=8")

Here's another:
[http://hostechs.com/2008/10/ubuntudebian-apt-get-subprocess-pre-installation-script-returned-error-exit-status-1/]("http://hostechs.com/2008/10/ubuntudebian-apt-get-subprocess-pre-installation-script-returned-error-exit-status-1/")

---

### Post by pranavakshar on 2010-01-07
> **Geoff918 said:**
> Open up terminal (Applications - Accessories - Terminal)

sudo dpkg --configure -a

Basically something broke on a recent update you ran, or failed to complete successfully. dpkg has to satisfy itself and then life will resume happily. :)

worked awesome for me..thanx!

---

