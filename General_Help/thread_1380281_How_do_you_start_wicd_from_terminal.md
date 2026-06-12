---
title: "How do you start wicd from terminal?"
date: 2010-01-13
forum: General Help
---

### Post by Cotopaxi on 2010-01-13
Hi, I shot the operative system of my son's computer into pieces and the system only boots into terminal mode (Kubuntu 9.04.

Anybody knows how to:

1) Start wicd from terminal?

2) Make wicd scan for an available network from terminal?

3) Make wicd connect to a selected network from terminal?

I want to run the command "sudo apt-get update" but the system can't download any files because it is not connected to the internet!

Thanks very much indeed for your help!

---

### Post by mk1w86 on 2010-01-13
Although it doesn't answer your question what exactly did you do to break the system and how will running apt-get update fix it? :-s

---

### Post by Cotopaxi on 2010-01-13
mk1w86:

I was trying to install the latest nvidia driver and somehow I ended up removing Xorg.:(

---

### Post by nothingspecial on 2010-01-13
```
wicd-curses
```

This will give you a nice little "gui" in the terminal

---

### Post by Cotopaxi on 2010-01-13
> wicd-curses

gives me "command not found".

Am I doing anything wrong?

---

### Post by mk1w86 on 2010-01-13
> [QUOTE]wicd-curses
gives me "command not found".

Am I doing anything wrong? [/QUOTE]

It may seem like a silly question but are you sure wicd is installed?

Also you could use the iwconfig command.  Type:

```
man iwconfig
```

for more information.

---

### Post by philinux on 2010-01-13
You must be running lucid if this has happened. Boot it up and choose recovery mode. Then choose command prompt with networking.

then lets get xorg back.

```
sudo apt-get install xserver-xorg
```

This will remove the nvidia driver but your system will now boot.

See this bug report on this.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/494166](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/494166)

---

### Post by nothingspecial on 2010-01-13
You must be typing it wrong or you don`t have wicd installed.

```
sudo ifconfig wlan0 up
``` 

```
sudo iwconfig wlan0 essid *networkname*
```

```
sudo iwconfig wlan0 key *key*
```

```
sudo dhclient
```

---

### Post by Cotopaxi on 2010-01-13
I will carry the computer of my son to the wireless router and connect this desktop to the ethernet connection.

As soon, as I make any progress, I will keep you informed.

Thanks again for your help!!! :popcorn:

---

### Post by nothingspecial on 2010-01-13
[ATTACH]143505[/ATTACH]


I press enter


[ATTACH]143507[/ATTACH]

Try again

---

### Post by Cotopaxi on 2010-01-14
nothingspecial:

you are not going to believe it:

On my 9.10 system it actually works what you are saying: I boot up into recovery mode and choose "command prompt with networking" and then I can type

> wicd-curses!!

On the 9.04 Desktop system of my son this did NOT work! So I had to make an ethernet connection, boot up into recovery mode and choose: "command prompt with networking", this worked. Thanks by the way philinux! ;)

The positive thing is, I managed to recover the system! :)

Thanks again to all of you for your help! :popcorn:

One last thing: How do I label this topic as "SOLVED" ??

---

### Post by mk1w86 on 2010-01-14
> One last thing: How do I label this topic as "SOLVED" ??

Under thread tools you should be able to mark the thread as SOLVED. :D

---

### Post by Cotopaxi on 2010-01-20
mk1w86:

Thanks, Just marked it! :popcorn:

---

