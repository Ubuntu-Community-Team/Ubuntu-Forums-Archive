---
title: "Help! Update manager problems"
date: 2011-01-02
forum: General Help
---

### Post by AirBiscuit on 2011-01-02
I've only just come around to Linux, so please go easy on me!

After a failed installation attempt of WinFF, i'm having problems with my Synaptic Update Manager. When i start it, it says:

> E: Malformed line 1 in source list /etc/apt/sources.list.d/winff.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.I'm assuming i need to remove the botched installation of WinFF before it'll work again, but i have no idea how.

I'm on Ubuntu 10.10 if it's relevant.

Thanks in advance

---

### Post by TeoBigusGeekus on 2011-01-02
```
gksu gedit /etc/apt/sources.list.d/winff.list
```
Post us the contents of the file.

---

### Post by Verbeck on 2011-01-02
could you post the output of the following from a terminal (applications>accessories)
```
cat /etc/apt/sources.list.d/winff.list
```

---

### Post by AirBiscuit on 2011-01-02
This is the reply:

>  deb [http://winff.org/ubuntu](http://winff.org/ubuntu) maveric 

---

### Post by TeoBigusGeekus on 2011-01-02
Try this
```
sudo apt-get purge winff
```
and report back.

---

### Post by AirBiscuit on 2011-01-02
response:

> Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.

---

### Post by TeoBigusGeekus on 2011-01-02
Ok, lets completely delete the winff.list file
```
sudo rm /etc/apt/sources.list.d/winff.list
```
Watch out with the rm command!

After that, try to update synaptic
```
sudo apt-get update
```

If this succeeds, reinstall winff
```
sudo apt-get -reinstall winff
```

---

### Post by AirBiscuit on 2011-01-02
Ok, the first entry didn't seem to do anything - it just presented me with another entry prompt. The update got part-way through, and then:

```
Fetched 72B in 1s (52B/s)
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
```

Thank you for the help so far, by the way! Very much appreciated.

---

### Post by TeoBigusGeekus on 2011-01-02
Close synaptic package manager if you have it open and try again.

---

### Post by AirBiscuit on 2011-01-02
Synaptic doesn't appear to be running, although it is showing a red error symbol in the top right (systray?). Anyway, it won't let me close it.

i re-tried the entry:

```
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
```

---

### Post by TeoBigusGeekus on 2011-01-02
You can't run apt-get from terminal when synaptic is running.
Maybe it's frozen or something. Reboot.

---

### Post by AirBiscuit on 2011-01-02
ok, rebooted. Synaptic wasn't in the systray. Opened a terminal, input the "sudo apt-get update" entry, and it did exactly the same. and now synaptic is showing in the systray.

Sorry for the ballache.

---

### Post by TeoBigusGeekus on 2011-01-02
Please post the output of 
```
ls /var/lib/dpkg
```

---

### Post by AirBiscuit on 2011-01-02
```
alternatives   cmethopt        info   statoverride      status-old
available      diversions      lock   statoverride-old  triggers
available-old  diversions-old  parts  status.bad        updates

```

---

### Post by TeoBigusGeekus on 2011-01-02
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by AirBiscuit on 2011-01-02
It asked for a password, then gave me another command prompt

---

### Post by TeoBigusGeekus on 2011-01-02
Good. Can you update apt now?

---

### Post by AirBiscuit on 2011-01-02
You, sir, deserve a pint! i'll buy you an Uzo one day!

Do you mind explaining what just happened?

---

### Post by TeoBigusGeekus on 2011-01-02
You just renamed the status-old file (old database backup of apt) to status, thus making it apt's current... status.
Apt found a correct file to parse and went on updating.
You can now purge winff
```
sudo apt-get purge winff
```
and install it again
```
sudo apt-get install winff
```


P.S.: I don't drink ouzo - I prefer [tsipouro]("http://en.wikipedia.org/wiki/Tsipouro") (I'm drinking it right now)...

---

### Post by AirBiscuit on 2011-01-02
It seems to be working now. Thank you very much for your time!

---

