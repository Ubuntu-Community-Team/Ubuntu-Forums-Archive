---
title: "Where is the location of installed applications?"
date: 2009-11-20
forum: General Help
---

### Post by mirchichamu on 2009-11-20
Just want to know where are the installed programs. I wanted to add one application to start up but couldn't find that.

---

### Post by Giblet5 on 2009-11-20
They're installed in lots of places (hundreds).

To add things to your session startup: System -> Preferences -> Startup Applications

To add things to system startup: /etc/rc.local

To list the installed packages: ```
sudo dpkg -l | awk '{ print $2 }' | sed -e '1,5d'
```

Or just ```
sudo dpkg -l
```

You can see what's installed via gui with Synaptic Package Manager by clicking the Status button and selecting "Installed".

---

### Post by NoaHall on 2009-11-20
> **mirchichamu said:**
> Just want to know where are the installed programs. I wanted to add one application to start up but couldn't find that.

/usr/bin


You won't need to look for it though, just enter the command to run it, for example, to run aMSN, it's "amsn".

---

### Post by Johnny B on 2009-11-20
> $ which {app name}
will tell you where a program is installed to

---

### Post by P4man on 2009-11-20
> **Giblet5 said:**
> 
To list the installed packages: ```
sudo dpkg -l | awk '{ print $2 }' | sed -e '1,5d'
```

You can always count on giblet to write a small bash script no one else understands to do anything lol. Giblet you're scaring new guys I think :)

For human beings try this in a terminal:

```
which pogramname
```

or 
```

whereis programname
```

---

### Post by mirchichamu on 2009-11-20
Thanks a lot for all of you. You are so helpful.
Actually I wanted to add deluge to my start up programs. It is not present in the window that opened and I have to add. But I don't know where was that program installed. Refer to screen shot.
Once again thanks.

---

### Post by NoaHall on 2009-11-20
Under the command bit, just put "deluge" (without the speechmarks)

---

### Post by bodhi.zazen on 2009-11-20
The orginization of the Linux file system is a bit different.

Here is an overview :

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

So most apps are in /usr/bin, but there are other locations and so it depends on the application and sometimes the version of Linux you use as there is no single standard, but the link I gave you will get you started.

See also :

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by mirchichamu on 2009-11-20
Thanks bodhizazen, Noahall,P4man,Johnny B for your help.
I did what NoaHall suggested. My problem solved.

One million thanks.

---

