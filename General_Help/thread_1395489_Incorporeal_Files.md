---
title: "Incorporeal Files"
date: 2010-01-31
forum: General Help
---

### Post by dougHines on 2010-01-31
I am attempting to setup a server to host a diskless cluster.  I have been making my way through a HOWTO but have hit a frustrating snag.

One of the instructions says to create a director /nfsroot/kerrighed/ to store the bootable systemfiles in

Here's my snag:  I created /nfsroot... and /kerrighed.  However /kerrighed does not show up on a ls command, nor does the system seem to know it exists.  Nothing shows up in the /nfsroot.  So its not like I mistyped it.  I figured it was a hiccup in the system so I tried to make the directory again... except that the system complains it already exists!... wtf?

Anyway, I have essentially hit a brick wall until I can get this resolved.  Does anyone have any guru knowledge that can help me speed me on my way?

Doug

---

### Post by falconindy on 2010-01-31
Without posting any output of your / or /nfsroot directories, I'm just going to guess that based on what you've said, you've created /nfsroot and /kerrighed both in the root directory, but you're looking for /nfsroot/kerrighed.

What happens if you do `mkdir -p /nfsroot/kerrighed;ls /nfsroot`?

---

### Post by dougHines on 2010-02-01
Well this is solved.  For some reason my system didnt like the command from /:
sudo mkdir /nfsroot/kerrighed/

But it had no problem with me doing the same thing in two separate commands
sudo mkdir /nfsroot/
sudo mkdir /nfsroot/kerrighed/

---

