---
title: "Running 2 x-servers"
date: 2010-06-22
forum: General Help
---

### Post by V-600 on 2010-06-22
I am not sure the best place for this but here it is.

Is it possible to connect an application (x-client) to two x-servers simultaneously. One x-server will be running on the local computer (desktop) and output to a TV screen, the other will be running on a networked laptop and will connect via ssh.

Currently I have x-forwarding working via ssh, so the laptop can display programs running on the desktop. However it would be nice to have these programs displayed on the TV screen at the same time.

Is this possible and can anyone point out how to do it?

Many thanks

---

### Post by bodhi.zazen on 2010-06-22
Take a look at VNC.

---

### Post by V-600 on 2010-06-22
Thanks. I had been advised similar on another forum but thought I would swing by here and see if there was any other advice.

I have never used VNC, or had cause to look into it so will be starting from scratch pretty much.

---

### Post by bodhi.zazen on 2010-06-22
Just be sure to secure VNC , VNC is one of the most commonly cracked servers.

I advise you tunnel VNC over ssh.

---

### Post by V-600 on 2010-06-25
I tried VNC. Unless I am missing something, all it does it give me a remote desktop.

It doesn't mirror the desktop on the local/remote machine. Also it is substantially slower than just using x-forwarding to remotely run just one app.

---

### Post by bodhi.zazen on 2010-06-25
> **V-600 said:**
> I tried VNC. Unless I am missing something, all it does it give me a remote desktop.

It doesn't mirror the desktop on the local/remote machine. Also it is substantially slower than just using x-forwarding to remotely run just one app.

It is slower. You can speed it up if you use compression.

It gives a desktop, that is true.

But, from there there is variation. Some VNC servers give you a new, independent X session, you do not want that.

You want a VNC server that allows you to share a X session. Try x11vnc .

---

### Post by V-600 on 2010-06-26
Ah, I didn't know that. As I was installing remotely via the command line I didn't read any of the descriptions. I just went for the first server to pop up after typing VNC and letting it autocomplete. From memory I think it was called vnc4server.

---

