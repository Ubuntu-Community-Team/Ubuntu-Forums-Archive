---
title: "remote vnc"
date: 2011-01-29
forum: General Help
---

### Post by Qifor on 2011-01-29
I have just setup a spare computer running the desktop version of 10.04.1. I am able to connect via vnc fine when ive already logged in but not when attempting to use ssh to start the server.

I can ssh in fine and run the vnc server but when attempting to connect with vnc viewer nothing happens after entering the password. Then when I kill the vnc server I get an authentication error asking if I want to attempt to reconnect.

Any idea what im doing wrong?

---

### Post by prshah on 2011-01-29
Hello,

I'd like to jump in into this thread as well since I am facing the same problem, starting recently.

I was able to successfully use remote-desktop via ssh till about a week ago. Now, when I try to connect, I just end up with a black screen.

I am able to use SSH perfectly. If I use vnc4server to launch another vnc server (eg :9) I can correctly connect to it via SSH-forwarded ports.

Only remote desktop does not seem to work. I've not made any config changes except for applying updates as available.

---

### Post by Qifor on 2011-01-29
hmm well I gave up and dragged my monitor back over, turns out it wasn't even getting far enough due to an error with the graphics driver that needed sorting.

All seems to be working once again thankfully.

---

### Post by prshah on 2011-01-31
> **prshah said:**
> 
I was able to successfully use remote-desktop via ssh till about a week ago. Now, when I try to connect, I just end up with a black screen.

OK problem solved; details below for reference value for future seekers.

Remote desktop stores the access password in my keyring. If I do not unlock the keyring locally (eg, at startup), when I attempt a remote desktop access, the server waits for the keyring to be unlocked, to check the access password.

If you have not unlocked the keyring (or cancelled it at startup), it apparently decides to wait forever.
 
Ensuring that the keyring is unlocked before leaving the system has remote access working just fine.

---

