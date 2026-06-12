---
title: "Desktop and Server"
date: 2011-02-28
forum: General Help
---

### Post by cbjmar on 2011-02-28
I have two HDs onboard (150GB each) one is running the desktop version. Possible to load up the server addition onto the other HD?  Would like to learn the server version, but not sure this is possible or will cause issues.. Thanks

---

### Post by blueridgedog on 2011-02-28
You should be able to do an install to the other hard disk and grub will present you with options for each disk on boot.  However, there is nothing on the server install that you cannot install on your desktop install...your desktop install has a GUI which the server install will not, otherwise, you can install any server package that you want to get familiar with on the desktop OS.  If you install server, all you have to do is:

```
sudo apt-get install ubuntu-desktop
```

And you will have gnome.

As an aside, for learning, a virtual machine (I like Sun Virtualbox) is a better bet for a teaching aid as you can run it while in your desktop environment and can wipe it with little or no fuss.

---

### Post by cbjmar on 2011-03-10
Thanks for the help.....

Just so I'm clear (new to ubuntu and all)  I have successfully loaded and am using 10.10 desktop.  Would it be better for learning to just load whats missing vs. server or load server to the second HD and utilize the virtualbox?

I take it the list of whats on the server vs. desktop is on the website?

Really... thank you

---

### Post by 3rdalbum on 2011-03-11
Server is literally Desktop but with no GUI. It's up to you to add packages to the server version anyway. If you want a web server, you can install Apache, etc.

---

