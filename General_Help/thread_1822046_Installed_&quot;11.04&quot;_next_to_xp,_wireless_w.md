---
title: "Installed &quot;11.04&quot; next to xp, wireless was fine until network manager &quot;disappeared-He"
date: 2011-08-10
forum: General Help
---

### Post by mejbr2003 on 2011-08-10
with fresh install of natty alongside xp pro...using new belkin wireless usb adapter, everything seemed fine. devices recognized and totally connected with great signal strength.
but after the second or third restart, the network manager was gone from the panel and wont light up as an option when i try to add it.

I ant find anyway to connect, Help please. my skills with linux extend just far enough to know not to do anything except get help here. 
thanks

---

### Post by Bubble32 on 2011-08-10
have you tried re-installing your network manager?! I once messed it up and simply doing the following did the trick for me:
```
sudo apt-get install network-manager
```

---

### Post by Wim Sturkenboom on 2011-08-10
Note in advance: I'm using 10.04 and can't say which changes Ubuntu made between 10.04 and 11.04.

First check if it's still running
```

wim@ubuntu-desktop01:~$ ps -ef |grep nm-app |grep -v grep
[B][COLOR="Red"]wim       1596  1519  0 Aug08 ?        00:00:00 nm-applet --sm-disable
[/COLOR][/B]wim@ubuntu-desktop01:~$ 

```
If it is running, you might have the same problem as I have. In my case, it's in the panel, but only one pixel wide.

If not, try to start
```

nm-applet --sm-disable

```

---

### Post by Wim Sturkenboom on 2011-08-10
Wanted to post the question on launchpad, but found [this question](https://answers.launchpad.net/ubuntu/+source/network-manager-applet/+question/116894) there with a possible solution in post #4.

Works partitally for me (till the next reboot :( ) Might work for you though.

---

