---
title: "Installed and application, but I cant see it anywhere"
date: 2009-12-01
forum: General Help
---

### Post by anikondemand on 2009-12-01
I have installed the program i8kutils_1.27 (a fan controller utility) in ubuntu 8.08, but I cant see it anywhere in Applications.

Should I have to do any extra configurations?
When I tried to install it again, it says package already installed. But cant spot out where it is.

Help.

---

### Post by philinux on 2009-12-01
Right click the top panel, add to panel. See if the applet is in there.

---

### Post by nothingspecial on 2009-12-01
Try opening a terminal and typing ```
i8ktl
```

Infact type ```
man i8ktl
``` for usage instructions.

---

### Post by anikondemand on 2009-12-01
> **philinux said:**
> Right click the top panel, add to panel. See if the applet is in there.

Tried it already, but its not there in the Add to Panel option.

---

### Post by anikondemand on 2009-12-01
> **nothingspecial said:**
> Try opening a terminal and typing ```
i8ktl
```

Infact type ```
man i8ktl
``` for usage instructions.

1. Command not found.
2. No manual entries.

---

### Post by nothingspecial on 2009-12-01
That`s because I can`t type  it should be i8kctl

---

### Post by anikondemand on 2009-12-01
> **nothingspecial said:**
> That`s because I can`t type  it should be i8kctl

Thanks for responding.

This is what I got from the terminal.
> can't open /proc/i8k: No such file or directory

Checked the folder. i8k is not there. This should be my installation directory, isnt it? Then to which folder the program is getting installed?:confused:

---

### Post by nothingspecial on 2009-12-01
What happens if you type ```
sudo modprobe i8k
``` and then retry

---

### Post by anikondemand on 2009-12-01
> **nothingspecial said:**
> What happens if you type ```
sudo modprobe i8k
``` and then retry

Done. Nothing happens. It comes to the next line $.

---

### Post by nothingspecial on 2009-12-01
We may be going down a blind alley here. But we`ll keep trying. As it went to the next line without returning an error that is good. To check the module loaded type ```
lsmod | grep i8k
```

If you see it in the output then it is loaded. The man page does exist on the internet so type in to google man i8kctl and read the instructions there. See if that`s any help.

---

### Post by anikondemand on 2009-12-01
> **nothingspecial said:**
> We may be going down a blind alley here. But we`ll keep trying. As it went to the next line without returning an error that is good. To check the module loaded type ```
lsmod | grep i8k
```

If you see it in the output then it is loaded. The man page does exist on the internet so type in to google man i8kctl and read the instructions there. See if that`s any help.

```
lsmod | grep i8k
```
This gave me the following :
```
i8k                     7448  0 

```
Will try googling man i8kctl.

---

### Post by Kevbert on 2009-12-01
Please take a look at [[COLOR="Red"]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/i8kutils/+bug/194335"). It seems the package has a number of bugs both reported for Ubuntu and Debian (Ubuntu is based on Debian).

---

### Post by anikondemand on 2009-12-01
> **Kevbert said:**
> Please take a look at [[COLOR="Red"]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/i8kutils/+bug/194335"). It seems the package has a number of bugs both reported for Ubuntu and Debian (Ubuntu is based on Debian).

Oops, is it incompatible?:(
But I have downloaded it from a source saying that its a stable one without any bugs.

---

### Post by nothingspecial on 2009-12-01
Giving the bug report a quick glance it just seems to say that you`re going to have to run sudo modprobe i8k before it will work.

A bit annoying but not a major issue.

---

### Post by anikondemand on 2009-12-01
Got the entire commands by googling. And more importantly, the command $i8kctl is working now.

These are the entire command sets (values are not mine).
Tested it, working.

> $ i8kctl 

1.0 A17 B5W123K 52 2 1 8040 6420 1 2 
$ i8kctl temp 

52 
$ i8kctl fan 

2 1

The fan command can accept two optional parameters which specify the new fan state for left and right fans. The state parameter can be: 
0 turn the fan off 

1 set low speed
2 set high speed
- don't change the state of this fan

For example the command: 
$ i8kctl fan - 2

sets the right fan to high speed and leaves the left unchanged. It should be noted that if the i8kmon(1) daemon is used to control the fans, setting the speed with i8kfan is pointless since the daemon will override the speed with its own value. 

Invoking i8kctl as i8kfan is the same as invoking the program with the fan option: 
$ i8kctl fan 1 2 

1 2 
$ i8kfan 1 2 

1 2

One doubt, is it not available in gui?
Only controlling through terminal is possible?

---

### Post by Kevbert on 2009-12-01
Try [[COLOR="Red"]this[/COLOR]]("http://packages.ubuntu.com/karmic/tk8.4") package, I believe it may work, but don't have any means of checking.

---

### Post by anikondemand on 2009-12-01
> **Kevbert said:**
> Try [[COLOR="Red"]this[/COLOR]]("http://packages.ubuntu.com/karmic/tk8.4") package, I believe it may work, but don't have any means of checking.

Same problem. Getting installed, but not showing in Applications.

---

### Post by anikondemand on 2009-12-04
Bump.

---

