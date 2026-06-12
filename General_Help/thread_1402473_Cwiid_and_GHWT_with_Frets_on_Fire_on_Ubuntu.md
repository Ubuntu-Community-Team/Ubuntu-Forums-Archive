---
title: "Cwiid and GHWT with Frets on Fire on Ubuntu"
date: 2010-02-09
forum: General Help
---

### Post by sidrit on 2010-02-09
hello there everyone.
i have a small problem i would like to work out.

I have been trying to set up Frets on Fire with my guitar from Metallica Edition (which somewhere up and down i read was of the GHWT breed).
On windows, with bluesoleil and GlovePie i have been able to successfully get it running with the aid of a script elaborated in the fretsonfire.net forum.

My issue is that i wanted to run this on my ubuntu box (that is my media center).
I successfully added and compiled the latest Cwiid from git, installed it and my guitar connects just fine and works correctly as a mouse.

The problem the GH3 script that is posted everywhere just won't do. The guitar is simply dead when i run wminput with that script.

I know it too late to make this short but my question is, has anyone got this running Fof with GHWT on Ubuntu (or any linux for that matter)?

thank you in advance
best regards
subaru
Member
 
Posts: 1
Joined: Sat Feb 06, 2010 8:49 am

---

### Post by sidrit on 2010-02-10
ooooooookay.
finally got it sorted.

downloaded the source of cwiid 0.6.
patched the hci_red function.
patched and removed the decode function and add the headers for the ghwt and compiled. now it works.

here's a write-up about it 
[http://sidrit.wordpress.com/2010/02/10/frets-on-fire-with-guitar-hero-world-tour-ghwt-on-ubuntu/]("http://sidrit.wordpress.com/2010/02/10/frets-on-fire-with-guitar-hero-world-tour-ghwt-on-ubuntu/")

solved.

---

