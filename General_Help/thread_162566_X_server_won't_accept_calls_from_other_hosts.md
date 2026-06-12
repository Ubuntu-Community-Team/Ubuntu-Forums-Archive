---
title: "X server won't accept calls from other hosts"
date: 2006-04-19
forum: General Help
---

### Post by David Olivier on 2006-04-19
Ever since I installed Ubuntu (5.10) I have been unable to get it to display for clients on other hosts. ](*,) 

If I try from another computer:

```
DISPLAY=my-ubuntu-host:0.0 some-x-application
```

it gives an answer such as:

```
Error: Can't open display: my-ubuntu-host:0.0
```

It doesn't seem to be a problem of authorisation; I have done:

```
/usr/bin/xhost +
```

to no avail. :evil:

The problem is not with the clients either; they display fine on other X11 servers (Solarix, MacOSX...).

Actually, the X server won't even display for itself! I get the same sort of error if on the Ubuntu server I type:

```
DISPLAY=localhost:0.0 gedit
```

However, if I omit the host altogether:

```
DISPLAY=:0.0 gedit
```

then it works.

So it gives me the impression that the X server is working over some sort of non TCP pipe, and is not listening at all on a TCP socket.

How do I get it to listen to the network? I have searched on the Ubuntu site and on the Web generally, but have found nothing. I got the idea that the file to edit might be /etc/X11/xorg.conf, but there seems to be nothing relevant in there (nor in man xorg.conf). :???:

I don't think I have done anything very special when I installed Ubuntu; I'm surprised no one else seems to have had the same problem. :confused:

---

### Post by David Olivier on 2006-04-19
With netstat, I came across the following socket:

```
ls -l /tmp/.X11-unix/X0

srwxrwxrwx  1 root root 0 2006-03-20 10:39 /tmp/.X11-unix/X0
```

I suppose that is the socket the X server is listening on?

That still doesn't tell me how to connect through the network!

---

### Post by David Olivier on 2006-04-19
Aaaaaaargh! :shock:  No one is replying! ](*,)  What can I do to get attention? :-\"

---

### Post by David Olivier on 2006-04-19
Jump? Shout? Whistle? :-\" :-\" :-\" :-\" :-\" :-\" :-\" :-\"

---

### Post by David Olivier on 2006-04-19
Ok, I give up. I'll stop pushing this thread up to top. =D>

---

### Post by David Olivier on 2006-04-20
Since no one cares, no one wants to answer me, everyone hates me, etc., :cry: I went back to google and got the answer myself. =D>

I finally found the magic phrase to Google for is "nolistent-tcp". It appears that in Ubuntu, for security reasons, all TCP access to the X server is disabled by default.

I edited the file /etc/X11/gdm/gdm.conf. In it was the line:

```
DisallowTCP=true
```

I changed that to:

```
DisallowTCP=false
```

(Just commenting out the line doesn't seem to work.)

(Before that I had also edited /etc/X11/xinit/xserverrc, to delete the "-nolisten tcp" parameters, but that wasn't enough, and is probably not useful.)

I am using Gnome. I understand that if you have kde, the file to edit is another one.

After modifying the /etc/X11/gdm/gdm.conf file, and rebooting, and issuing the proper xhost command, the xserver now accepts remote calls.

---

### Post by dcstar on 2006-04-20
And we all assume that System-Administration-Login Screen Setup-Security-Deny TCP connections is not set, don't we?

---

### Post by David Olivier on 2006-04-20
Hem I'm not very sure I know what the System-Administration-Login Screen Setup-Security-Deny TCP connections is... Another setting in the gdm.conf file?

Anyway I forgot to say that there seems to be an alternative, graphical, way to edit the gdm.conf file: the gdmedit utility. In the "security" flap you have the "Deny TCP connections to X server" checkbox. That sets or resets the DisallowTCP variable in the gdm.conf file.

You have to call the gdmedit utility as root or with sudo.

---

