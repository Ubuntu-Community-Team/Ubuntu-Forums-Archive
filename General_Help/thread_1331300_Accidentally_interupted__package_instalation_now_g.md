---
title: "Accidentally interupted  package instalation now getting this error:"
date: 2009-11-19
forum: General Help
---

### Post by dmaneleven on 2009-11-19
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Synaptic manager will not start. When I enter: "sudo dpkg --configure -a" it seems to want to continue package instalation in terminal, but it doesn't do anything. and now synaptic Packaging manager will not open.

---

### Post by nothingspecial on 2009-11-19
Try ```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

---

### Post by dmaneleven on 2009-11-19
> **nothingspecial said:**
> Try ```
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update
```

Tried all 3 codes all I get is
"E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

---

### Post by drs305 on 2009-11-19
Do you still have Synaptic or another install application open? Normally the message means that another installer is running. If you think you have closed out other installers and still get the message, rebooting should terminate all running processes and will probably allow you to run the commands on restart.

---

### Post by hal10000 on 2009-11-19
> Tried all 3 codes all I get is
"E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"
Before you shoot up these commands you have to stop synaptic (or whatever package manager you are using).

---

### Post by dmaneleven on 2009-11-19
> **drs305 said:**
> Do you still have Synaptic or another install application open? Normally the message means that another installer is running.

No as far as I know. I rebooted several times but get:

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."

Is there a "task manager" function, as in windows, where I can see whats going on in the background? and close it?

---

### Post by drs305 on 2009-11-19
> **dmaneleven said:**
> No as far as I know. I rebooted several times but get:

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."

Is there a "task manager" function, as in windows, where I can see whats going on in the background? and close it?

A very nice terminal app is "htop", but you have to install it.  :-(

You can use System, Administration, System Monitor: Processes to see what is running. Right click on a suspected app to reveal the choices for closing, etc.

You can also try running "sudo killall *appname or commandname*" to try to end a running process. It would normally be preferable to shut down an app in the usual manner but since you have rebooted it's probably not going to make much difference. At this point you might have to manually remove the "lock" file in /var/lib/dpkg. It's not a great option but it may be the only way to regain your ability to add/remove programs.

---

### Post by dmaneleven on 2009-11-19
> **drs305 said:**
> A very nice terminal app is "htop", but you have to install it.  :-(

You can use System, Administration, System Monitor: Processes to see what is running. Right click on a suspected app to reveal the choices for closing, etc.

You can also try running "sudo killall *appname or commandname*" to try to end a running process. It would normally be preferable to shut down an app in the usual manner but since you have rebooted it's probably not going to make much difference. At this point you might have to manually remove the "lock" file in /var/lib/dpkg. It's not a great option but it may be the only way to regain your ability to add/remove programs.

Do you know what app I should end in system monitor to regain use of synaptic package manager? It stopped working because some "apt" or "aptitude"  is working in the background BTW: all processes say "sleeping" also the app I was installing is called "moodle"

---

### Post by hal10000 on 2009-11-19
> Is there a "task manager" function, as in windows, where I can see whats going on in the background? and close it?

If you use gnome, then launch **gnome-system-manager**, or in kde it would be **ksysguard**

---

### Post by dmaneleven on 2009-11-19
> **hal10000 said:**
> If you use gnome, then launch **gnome-system-manager**, or in kde it would be **ksysguard**

Yeah thanx but I'd like to know what process I should close to regain use of Synaptic package monitor. Which one is an apt, aptitude. also the app I interupted while installing is called "moodle"

---

### Post by hal10000 on 2009-11-19
Just try
```
sudo killall apt
sudo killall apt-get
sudo killall aptitude
sudo killall synaptic
sudo killall dpkg
sudo rm /var/lib/dpkg/lock
```

---

### Post by dmaneleven on 2009-11-19
> **hal10000 said:**
> Just try
```
sudo killall apt
sudo killall apt-get
sudo killall aptitude
sudo killall synaptic
sudo killall dpkg
sudo rm /var/lib/dpkg/lock
```


thanx!guys! this worked

---

