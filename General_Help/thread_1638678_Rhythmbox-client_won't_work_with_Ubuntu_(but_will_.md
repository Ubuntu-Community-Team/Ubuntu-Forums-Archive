---
title: "Rhythmbox-client won't work with Ubuntu (but will work with Mac!)"
date: 2010-12-05
forum: General Help
---

### Post by djmac on 2010-12-05
I am trying to play music on an ubuntu pc over a local network using:

```
~$ ssh -X user@localhost
~$ rhythmbox-client
```

A rhythmbox window opens, with all the music in it etc. But it doesn't play properly (i.e. it 'plays' silently).

The weird thing is, from a Mac terminal, the EXACT same commands work, and I get a functioning rhythmbox in an X11 window, that plays music on the server flawlessly.

This seems really bizarre to me . . . . :-s

Any ideas on why it is not working in ubuntu? Cheers.

---

### Post by metalf8801 on 2010-12-06
It could be a audio codec problem what formate is the music in? 

I hope this helps
Dan

---

### Post by djmac on 2010-12-06
The vast majority are just mp3's. 

Just to clarify: The music plays fine on the host machine when you manually / directly play them. 

They also play fine (on the host) when a guest mac user opens the rhythmbox-client (via ssh)

It just does not seem to work when a guest ubuntu tries to open rhythmbox-client (via ssh).

---

### Post by metalf8801 on 2010-12-08
> **djmac said:**
> The vast majority are just mp3's. 

Just to clarify: The music plays fine on the host machine when you manually / directly play them. 

They also play fine (on the host) when a guest mac user opens the rhythmbox-client (via ssh)

It just does not seem to work when a guest ubuntu tries to open rhythmbox-client (via ssh).

Have you installed the Fluendo codecs to decode mp3s on your Ubuntu guest?

---

### Post by djmac on 2010-12-08
I am not trying to play the music through the guests speakers 

(I have no problems plating mp3's on the guest using a local rmythmbox).

---

