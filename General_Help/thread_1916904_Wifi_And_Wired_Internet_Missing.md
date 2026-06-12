---
title: "Wifi And Wired Internet Missing"
date: 2012-01-29
forum: General Help
---

### Post by Wakunahum on 2012-01-29
I installed Xubuntu 11.10 onto a friend's older HP laptop and set up the b43 broadcom drivers last Thursday.  Everything worked fine.

I get a call later after a reboot and the wired connection and wifi are no longer there.

I come to check it out a few days later and the wireless AND wired connection (the eth0) were not even available to use.

I decided to wipe the install and start over thinking I had to have done something wrong.  I install Ubuntu 10.04 as it's the version of Ubuntu I'm most familiar with.

The install goes fine and the additional b43 drivers work without problems.  We have wired and wireless internet as options both which work.

Upon restarting the machine, these are gone.

I put in a live CD of Ubuntu 10.04 and have a wired connection again but none work when using the installed version.

What is happening?  Is this a known issue?  What changes can I make?

---

### Post by carl4926 on 2012-01-29
First. You should know that 11.10 has better support for b43

Did you try to probe the device, for example

```
sudo modprobe -rv b43
```
```
sudo modprobe -v b43
```

Ideally, if you could have the machine ready and use a different machine if necessary to message here.

FYI: It's very unusual for wired connections to not work

---

### Post by varunendra on 2012-01-29
> **Wakunahum said:**
> Everything worked fine.

I get a call later after a reboot and the wired connection and wifi are no longer there.
..
..
The install goes fine and the additional b43 drivers work without problems.  We have wired and wireless internet as options both which work.

Upon restarting the machine, these are gone.
This is indeed very strange! I don't know if it is a known issue, but I would really like to dig it if you are willing to cooperate.

When you restart and the connections are gone, please run and post outputs of:
```
uname -mr
ifconfig -a
iwconfig
sudo lshw -C network
lsmod
cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf
cat /etc/modprobe.d/blacklist.conf
ls /etc/modprobe.d/blacklist*
dmesg | grep -iE 'net | wlan | eth | b43 | BCM'
```Sorry for asking so many outputs, but they should give us some clue about the cause of the problem, or at least an idea of where to start from.

**_EDIT_:**
In 10.04, it is nm-system-settings.conf in /etc/NetworkManager directory, while in 11.04 onwards, it is NetworkManager.conf file. Post the contents of whichever you have.

---

