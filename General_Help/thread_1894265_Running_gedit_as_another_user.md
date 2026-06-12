---
title: "Running gedit as another user"
date: 2011-12-12
forum: General Help
---

### Post by bala150985 on 2011-12-12
Hi

This is what I am attempting

I login to my Ubuntu as UserA, open a terminal and type gedit, the gedit GUI opens up :D
UserA@system:~$ gedit
UserA@system:~$

Now I opened another terminal, su UserB and enter password so that I become UserB, On the same terminal I type gedit. gedit GUI does not open up :( and it throws these two lines as error.

UserA@system:~$ su UserB
password: ************
UserB@system:~$gedit
No protocol specified

(gedit:6935): Gtk-WARNING **: cannot open display: :1.0

I have this same configuration working on another system perfectly fine, I don't know why I cannot replay the same thing on this box.

Now I opened another terminal, sudo su and enter root's password so that I become Root, On the same terminal I type gedit. gedit GUI opens up, so why am I not able to open up the VirutalBox GUI while I am a normal user ?

UserA@system:~$ sudo su
password: ************
UserA@system:~#gedit

gedit GUI opens up.

Host is running Ubuntu 10.04 i386.

---

### Post by WasMeHere on 2011-12-12
Hi bala150985

I think it is because another regular user is not allowed to write to your desktop (creating a new window). But you can run an editor within your terminal (command line interface) for example ***nano*** or ***vim***.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by sisco311 on 2011-12-12
You have to add the user to the list of allowed users to make connections to the X server:
```

xhost +SI:localuser:**UserB**
su -l UserB -c gedit
xhost -SI:localuser:**UserB**

```

---

### Post by WasMeHere on 2011-12-12
Thanks for a nice tip, sisco311 :-)

I made a small script for this purpose

---

### Post by bala150985 on 2011-12-12
UserA@system:~$xhost +SI:localuser:UserB
localhost:UserB being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8

su -l UserB -c gedit
xhost -SI:localuser:UserB
Gain the same error

I guess xhost throws out some errors.

However If I just type in xhost + and then SU in to UserB then every thing works :confused:

---

### Post by bala150985 on 2011-12-12
First of all I would like to thank  sisco311 and Olle

I found some answers on the link shown below.

[http://askubuntu.com/questions/50938/how-can-i-switch-user-in-a-shell-and-use-the-existing-gnome-display-session](http://askubuntu.com/questions/50938/how-can-i-switch-user-in-a-shell-and-use-the-existing-gnome-display-session)

[B]Solution1

[/B]xhost +

Then try to su to UserB
[B]
Solution2
[/B]xauth nextract - $DISPLAY > /tmp/xauth.temporary.file
su -l bob -c 'xauth nmerge - < /tmp/xauth.temporary.file'
rm /tmp/xauth.temporary.file

I am not sure if security would be an issue with both these methods.

---

### Post by WorMzy on 2011-12-12
Can you not just use gksudo -u?

```
gksudo -u [COLOR="Red"]username[/COLOR] [COLOR="DarkGreen"]appname[/COLOR]
```

---

