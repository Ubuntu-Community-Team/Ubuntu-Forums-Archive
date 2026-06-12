---
title: "Question about multiple users, SSH, and X"
date: 2009-09-23
forum: General Help
---

### Post by IsmailBhai on 2009-09-23
I use FreeNX to connect to my laptop at home and I login with my only username.  If i start up a program like pidgin or thunderbird and I leave work without logging off it is still running in the background when i come home and run ps -e.  My question is if I can just bring this program on the screen (i am using gnome) or would i have to kill the process everytime and restart it?  any help would be appreciate it.

---

### Post by XCan on 2009-09-23
It feels like you'll have to kill it, at least I haven't found any good solution for this.

---

### Post by IsmailBhai on 2009-09-23
thanks. hopefully someone knows how to.

---

### Post by IsmailBhai on 2009-09-24
no one?

---

### Post by mad_jack on 2009-09-24
> **IsmailBhai said:**
> I use FreeNX to connect to my laptop at home and I login with my only username.  If i start up a program like pidgin or thunderbird and I leave work without logging off it is still running in the background when i come home and run ps -e.  My question is if I can just bring this program on the screen (i am using gnome) or would i have to kill the process everytime and restart it?  any help would be appreciate it.

Edit $HOME/.bashrc and add:

export TMOUT=3600

This will cause the shell to self terminate after 30 minutes. Any sub processes such as firefox, t-bird etc. should be brought down with it.

---

### Post by XCan on 2009-09-24
Wouldn't that cause all shells to kill themselves even if the user is sitting at the machine locally?

---

### Post by bodhi.zazen on 2009-09-24
I am not certain about FreeNX, but it sounds as if FreeNX is using a separate X session. My guess is that it would be possible to access the separate X sessions, but doing so would probably be a security risk, especially considering you are using FreeNX over the internet.

So you could connect to your FreeNX session , from home, and manage things from there or kill them via the command line.

The other option would be to use command line tools and use screen to attach / detach sessions. But then you would be using ssh and not FreeNX ;)

---

### Post by IsmailBhai on 2009-09-24
> **bodhi.zazen said:**
> I am not certain about FreeNX, but it sounds as if FreeNX is using a separate X session. My guess is that it would be possible to access the separate X sessions, but doing so would probably be a security risk, especially considering you are using FreeNX over the internet.

So you could connect to your FreeNX session , from home, and manage things from there or kill them via the command line.

The other option would be to use command line tools and use screen to attach / detach sessions. But then you would be using ssh and not FreeNX ;)

hmm.. thanks. not really sure what you mean tho.  I know freenx sessions are usually on :1000 or :1001 or something.  another option I have is to use shadowing but i havent figured that out yet.

---

### Post by bodhi.zazen on 2009-09-24
When you connect you either connect to a shared X session. In this case, if you have tow users, one local and one remote, they see the same screen and same set of running applications. They share a mouse and keyboard.

An example is vino, the default VNC server in Ubutnu. Another example is x11vnc.

The other way is that each user has a separate X session and they do not see the same application and do not share a keyboark or mouse. An example is vnc4server

I suspect FreeNX is similar to vnc4-server and thus you do not share a X session.

---

### Post by mad_jack on 2009-09-25
> **XCan said:**
> Wouldn't that cause all shells to kill themselves even if the user is sitting at the machine locally?

Sorry, I wasn't clear - that should have read: This will cause the shell to self terminate after 30 minutes ***of inactivity***.

---

### Post by IsmailBhai on 2009-09-25
> **bodhi.zazen said:**
> When you connect you either connect to a shared X session. In this case, if you have tow users, one local and one remote, they see the same screen and same set of running applications. They share a mouse and keyboard.

An example is vino, the default VNC server in Ubutnu. Another example is x11vnc.

The other way is that each user has a separate X session and they do not see the same application and do not share a keyboark or mouse. An example is vnc4server

I suspect FreeNX is similar to vnc4-server and thus you do not share a X session.

yes, freeNX doesnt share an X session it makes a new one on port 1000.  I believe sharing is possible with the shadowing feature which I do not know how to use.

So its not possible to move a program from one X session to another with the same user?

---

