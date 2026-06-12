---
title: "Problem with apt-get"
date: 2010-11-23
forum: General Help
---

### Post by rmcellig on 2010-11-23
I am trying to update my computer as well as install software from the Ubuntu Software Center and keep getting an apt-get error. Even after restarting my computer, I get this error. What should I do so this stops happening?

---

### Post by WorMzy on 2010-11-23
Open a terminal and run

```
sudo apt-get update
```

Assuming it errors, paste the output here.

It should give us more of an insight to what's wrong. It could just be something as simple as a left-over lock file, or you could have some serious problems.

---

### Post by rmcellig on 2010-11-23
This is what I get:

randy@randy-ubuntu:~$ sudo apt-get update
[sudo] password for randy: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
randy@randy-ubuntu:~$

---

### Post by matt_symes on 2010-11-23
Hi

> **rmcellig said:**
> This is what I get:

randy@randy-ubuntu:~$ sudo apt-get update
[sudo] password for randy: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
randy@randy-ubuntu:~$

Did you have the package manager or the software centre open when you ran this command?
If you did ensure both are closed and retype the command and repost results. 

Do you still get this error with apt-get after a reboot?

I am just trying to eliminate the basics.

Kind regards

---

### Post by rmcellig on 2010-11-23
The only thing I have open is Firefox.

---

### Post by rmcellig on 2010-11-23
I will try another reboot but it seems to happen anyway. I will post back.

---

### Post by rmcellig on 2010-11-23
After a restart my Update Manager is working for now. Could Cron jobs I have play a part in all of this? How can I post back my cron jobs?

---

### Post by WorMzy on 2010-11-23
OK. That's a common error, and isn't serious. First make sure that you don't have any hidden instances of apt running by opening a terminal and running ```
pgrep -l 'apt'
```
Check the output for any instances of apt-get or similar applications. If any are running, end them with
```
sudo pkill -9 <process number>
```

Then try again.

If nothing comes up, or no apt-* processes come up, then it's probably safe to remove the lock file manually.

simply run
```
sudo rm /var/lib/apt/lists/lock
```

Then try again.

---

### Post by matt_symes on 2010-11-23
Hi

I expect it will happen after a reboot.

Open a terminal and type (case sensitive)

sudo mv /var/lib/apt/lists/lock /var/lib/apt/lists/lock.bk

Enter your password. You will not see anything on the screen as you type it. This is normal.

Then type

sudo apt-get update

Do you still get the same error?

EDIT: Beaten to it. Your quick Wormzy :)

Kind regards

---

### Post by WorMzy on 2010-11-23
Yes, cron jobs can cause this. If you have one running to update your package information (for example, to use with conky), then the lock will be in place while the update check is running. You will have to wait for it to finish before installing something. Generally speaking, you don't really need to keep the package information updated every hour, I'd set the script to run once a day at most. Ubuntu is hardly a bleeding-edge distro in the first place, so the packages you have installed already should be more than stable enough to be getting on with.

---

### Post by rmcellig on 2010-11-23
Seems to be OK.

---

