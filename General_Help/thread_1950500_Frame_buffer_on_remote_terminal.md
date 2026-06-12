---
title: "Frame buffer on remote terminal?"
date: 2012-03-31
forum: General Help
---

### Post by nickajeglin on 2012-03-31
I have an old computer running 10.04.4 lts in my living room, it runs a minecraft server for friends, and I use it for mudding, etc. I ssh in to the server daily, and I find myself wishing I could see images via the terminal. When I am physically present at the computer, fbi works fine, but over ssh, it gives me "ioctl VT_GETSTATE: Invalid argument (not a linux console?)"

I'm assuming that the issue is me being remote, but is there any work around, or perhaps another route entirely to see images over ssh?

---

### Post by dcstar on 2012-03-31
> **nickajeglin said:**
> I have an old computer running 10.04.4 lts in my living room, it runs a minecraft server for friends, and I use it for mudding, etc. I ssh in to the server daily, and I find myself wishing I could see images via the terminal. When I am physically present at the computer, fbi works fine, but over ssh, it gives me "ioctl VT_GETSTATE: Invalid argument (not a linux console?)"

I'm assuming that the issue is me being remote, but is there any work around, or perhaps another route entirely to see images over ssh?

The ssh session is probably not passing the correct VT terminal emulation value, so the program that depends on it is barfing or just not compatible with anything but a direct host terminal session.

---

### Post by nickajeglin on 2012-03-31
I was under the impression that putty was an xterm emulator, but it is obvious from your reply and the error message that it is not giving fbi what it needs. As the error message says, this is definitely not a linux console. I'm afraid I am to ignorant about terminal emulation to know whether this is even a possibility or not though. I'll probably just drop it for the time being, as it's definitely not a necessity.

Edit: I appreciate your speedy reply in any case, thank you.

---

### Post by HiImTye on 2012-04-01
```
ssh -X
```
will let you view X windows over SSH, if that is what you are looking for

---

### Post by nickajeglin on 2012-04-01
> **HiImTye said:**
> ```
ssh -X
```
will let you view X windows over SSH, if that is what you are looking for

I found this tutorial: [http://vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

While not exactly what I was looking for, this will work for my purposes. Thanks.

---

### Post by dcstar on 2012-04-01
> **nickajeglin said:**
> I found this tutorial: [http://vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

While not exactly what I was looking for, this will work for my purposes. Thanks.

Man, 2003! I found the comments on Gnome amusing.

---

