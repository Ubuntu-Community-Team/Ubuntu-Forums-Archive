---
title: "NX client display problem"
date: 2012-02-06
forum: General Help
---

### Post by ajs1 on 2012-02-06
I'm running the NoMachine free NX server on a 64-bit machine running Ubuntu 11.04, and the NX client on a 32-bit machine running Ubuntu 10.04. It has worked very well for a long time, but recently the display on the client has become a window into a desktop the same size as on the server, instead of using a desktop of the size specified in the client configuration. I can only see the top left corner of this desktop display, because my client display is smaller in pixels than the server one. This is a real nuisance. In particular, I can't see the Gnome panel along the bottom of the NX window.

I hadn't changed the NX installation for some time before this happened, but I have applied all the recommended Ubuntu updates. After it happened I reinstalled NX, but that hasn't fixed the problem.

I have tried changing the display size in the NX configuration, but that doesn't help. If I select a smaller size, an X window of that size appears briefly, but then the window onto part of the server display appears instead.

Any suggestions welcome.

---

### Post by iceback on 2012-02-20
what happens if you maximize the client?  Can you not resize the client window?

---

### Post by ajs1 on 2012-02-20
The client window is already maximized. I can resize it, but it's always a window into a server screen that is bigger than the client screen.

---

### Post by iceback on 2012-02-20
How about using "full screen" on the client.  Ctrl-Alt-F I think.  I know that connecting from my laptop (1 head) to machine at work (2 heads) I get a single full screen (not a port to the servers monitors). Perhaps you are connecting to a running nx session on the target machine?

---

### Post by ajs1 on 2012-02-21
Thanks for the suggestion. Ctrl-Alt-F does improve things a little -- I can see part of the panels along the top and bottom of the screen, but I still don't see the full height or width. (The server has a bigger screen than the client, but previously I was getting a gnome session to fit the client screen instead of a partial view of a gnome session suitable for the server screen.)

Other things I have tried: I emptied the cache of old sessions kept on the server. I purged the nxclient package from the client and reinstalled it. I purged it again and installed an older version that used to work. I logged out of the session that I usually leave running on the server in case I was getting a view into that. None of these things helped. I also checked that the only NX processes on server and client were the ones I had just started up.

---

### Post by iceback on 2012-02-21
Sorry I can't be of more help.  Am having all sorts of fun with gnome-3 and nx myself (and finding some help out there) but not the issue you're seeing. 

There is the is the Display setting on the Configure/General tab. Have you played with those at all? Available area v. Full Screen v. Custom et al?

---

### Post by ajs1 on 2012-02-21
Ah, yes, I have also tried lots of different display settings. Something seems to be over-riding anything I set there.

---

