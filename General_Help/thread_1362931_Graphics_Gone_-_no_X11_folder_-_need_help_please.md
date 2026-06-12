---
title: "Graphics Gone - no X11 folder - need help please"
date: 2009-12-23
forum: General Help
---

### Post by heitjer on 2009-12-23
All,
I had buggy video performance and selected to install the propriatary graphic driver, after reboot I had no readable login screen (stripes, stange colors) so I thought I better revert back to the previous xorg.conf. 

I rebooted into the rescue mode and into a root command, than cd'ed to /etc but  int there is no /X11 folder anymore....


HELP PLEASE!

---

### Post by heitjer on 2009-12-23
OK - I used xfix and the /X11 folder is back.

Now I am trying the last good xorg.conf ....

---

### Post by wojox on 2009-12-23
Is there a failsafe file?

---

### Post by heitjer on 2009-12-23
Need help - none of my old xorg.conf files is working. 

Any advice?

---

### Post by wojox on 2009-12-23
You should be able to reset it by:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by heitjer on 2009-12-23
wojox - thanks for your support. 

But this did not help. 

I have a backup somewhere - can I somehow get this xorg.conf file from the backup?

How would I best do this? USB stick?

---

### Post by audiomick on 2009-12-23
If you can get the backup file onto the computer (use a USB stick, or whatever is convenient), open it in an editor.


Then open the existing one

```
gksu gedit /etc/X11/xorg.conf
```

Copy the contents out of the backup, select all in the current one and paste over the top.


If you want to keep what is in the current one for any reason, put a # at the start of every line and paste the backup in at the end. The # identifies the line it is at the start of as a comment, so it will be ignored.

---

### Post by heitjer on 2009-12-23
Thanks - gedit does not work from the command line in the recovery mode. 

I just mounted the backup harddrive but I just realized that I have only the /home directory saved. Is there a xorg.conf by any chance in the /home directory?

---

### Post by heitjer on 2009-12-23
Now I am completely puzzled. I booted from the original 9.04 CD and then copied the xorg.conf from the temp directory of the live environment to the /X11 folder. Then I rebooted into recovery and copied the 'live CD version' over the harddrive one.

STILL SAME PROBLEM. 

Why did the graphic card work in the live enviroenment and not in the regular boot?

---

### Post by heitjer on 2009-12-23
SOLVED

This fixed my problem:
[http://www.ubuntugeek.com/how-to-install-nvidia-graphics-drivers-195-22-in-ubuntu-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/how-to-install-nvidia-graphics-drivers-195-22-in-ubuntu-karmicjauntyintrepidhardy.html")

First you need to edit /etc/apt/sources.list file

```
sudo gedit /etc/apt/sources.list
```

add this line

For Jaunty users (like me, others follow the link above)

```
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu jaunty main
```

Save and exit the file

Install GPG key using the following command

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
```

Update source list

```
sudo apt-get update
```

Install beta drivers

```
sudo apt-get install nvidia-glx-195 nvidia-195-modaliases
```

These drivers were released actually today!

---

