---
title: "Desktop lockup"
date: 2012-02-20
forum: General Help
---

### Post by OldManRiver on 2012-02-20
All,

About a year ago, after the install of a security patch for 10.04 LTS, the Desktop started locking up.  You do not notice it at first, then you notice that the clock (mine is set with seconds on to track this), does not update and the Network Manager icon does not show, nor update.

Anyway at first it was corrected with a simple restart of gdm issuing:

/etc/init.d/gdm restart

But lately that does not fix it and even a complete system restart using:

reboot now

Does not clear this.  Really frustrated with this, as leaves me blind on the internet connectivity and time sides which I think are critical in operations.

I looked at thread:

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

which was talking about freezes in 10.04, but did not find my particular scenario.

Would appreciate some help on this to:

1. Know what is causing the hang up,
2. Find a better way to re-set the DT, so it restores correctly when hung,

Thanks!

OMR

---

### Post by OldManRiver on 2012-03-14
All,

Can I get some help here?

OMR

---

### Post by 2F4U on 2012-03-14
It could be of advantage if you would provide information about your hardware.
Such lockups are difficult to diagnose, but what you should do is
1. Look into the log files at the time of the lockup and see if there are any errors
2. Verify, that the lockups are not a result of overheating
3. Run a memtest program (for example from a liveCD)
4. Try to find a patter, e. g. happens when particular programs are running

---

### Post by Zill on 2012-03-14
> **OldManRiver said:**
> ...Would appreciate some help on this to:

1. Know what is causing the hang up,...
I understand from [this post]("http://ubuntuforums.org/showthread.php?p=11765088") that your system *may* not have been fully updated with patches and bug fixes.

I suggest you could first update/upgrade your system to the current 10.04 LTS release which is actually 10.04.4.  You can check your current release with the following command:
```
cat /etc/lsb-release
```
For example, my system shows the following output:
```
roger@dino:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
```
Then I suggest you run the following two commands to update/upgrade to the latest 10.04.4 LTS standard:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by OldManRiver on 2012-04-02
> **Zill said:**
> I understand from [this post]("http://ubuntuforums.org/showthread.php?p=11765088") that your system *may* not have been fully updated with patches and bug fixes.

I suggest you could first update/upgrade your system to the current 10.04 LTS release which is actually 10.04.4.  You can check your current release with the following command:
```
cat /etc/lsb-release
```

Zill,

Yup at latest with:
```
cat /etc/lsb-release
```giving:
```

root@localhost:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
```
Wondering if this is an Ubuntu or X-Win problem?

Current reading is at setting in uploaded screen shot, from time of last reboot.

---

### Post by Zill on 2012-04-02
OldManRiver: Have you updated/upgraded *all* installed packages to the *latest* Ubuntu 10.04.4 LTS standard?
```
sudo apt-get update
sudo apt-get upgrade
```
If any errors occur when running these commands please post relevant output(s).

---

### Post by OldManRiver on 2012-04-03
> **Zill said:**
> OldManRiver: Have you updated/upgraded *all* installed packages to the *latest* Ubuntu 10.04.4 LTS standard?
```
sudo apt-get update
sudo apt-get upgrade
```
If any errors occur when running these commands please post relevant output(s).

Zill,

None!

OMR

---

### Post by HiImTye on 2012-04-03
I saw in another post that their problem was the result of the bottom panel and that removing it then adding it again and the stuff they use on it manually fixed the problem

I have no way of verifying this as I don't use 10.04 in favor of newer hardware support but it shouldnt be too hard to check

---

### Post by Zill on 2012-04-03
> **OldManRiver said:**
> About a year ago, after the install of a security patch for 10.04 LTS, the Desktop started locking up...
1)  Do you know which packages were upgraded as part of this security patch?

2)  Have you installed anything non-standard, such as backported packages or ppa's etc?

3)  Which graphics card are you using?

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #12 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

### Post by Zill on 2012-06-08
> **OldManRiver said:**
> ...Your help in getting them resolved, closed, SOLVED, is appreciated!
Sorry but I find this post ambiguous!

Do you still need help?  If so then please respond to any questions that have been posted in this thread.

If your problem has been resolved then please use the "Thread Tools" at the top to mark the thread as "Solved".

---

