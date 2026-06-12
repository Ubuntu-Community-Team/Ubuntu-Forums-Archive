---
title: "VNC problems"
date: 2011-07-24
forum: General Help
---

### Post by Dr.iCe on 2011-07-24
I have a dedicated server which I have SSH access to
I have do "sudo apt-get install vnc4server"
and launched it, when connecting to it remotely using VNC Viewer (on my Windows 7 laptop) I connect but I only get a grey screen with a little grey terminal on in the upper-left corner.

I tried the ```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```
to enable graphical desktop but it says "command not found"

What I want is remote graphical desktop control over the dedicated server. can anyone help me out on this?

---

### Post by mikewhatever on 2011-07-24
The server edition doesn't include any graphical packages by default. If you want a desktop environment, it would make sense to install the desktop edition instead.

---

### Post by Dr.iCe on 2011-07-24
> **mikewhatever said:**
> The server edition doesn't include any graphical packages by default. If you want a desktop environment, it would make sense to install the desktop edition instead.

would you be so kind that you would make a small guide for me on how to do this?

---

### Post by Dr.iCe on 2011-07-24
shameful selfbump

---

### Post by Dr.iCe on 2011-07-24
bump

---

### Post by mikewhatever on 2011-07-24
There is a guide on how to install the desktop edition of Ubuntu:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

To help us help you, perhaps you could explain what you want to control graphically on the server. Would a window manager and a file browser be enough?

---

### Post by Dr.iCe on 2011-07-24
see my thread @ [http://ubuntuforums.org/showthread.php?p=11082771#post11082771](http://ubuntuforums.org/showthread.php?p=11082771#post11082771)

---

### Post by HermanAB on 2011-07-25
Well, on Linux, VNC is almost always the wrong solution and on a server it always is...

To administer the server install webmin and use your Windoze web browser.

---

