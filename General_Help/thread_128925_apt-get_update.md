---
title: "apt-get update"
date: 2006-02-12
forum: General Help
---

### Post by TomB on 2006-02-12
Apt was updating perfectly until today, when it give this:

Fetched 192B in 2s (82B/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

Anyone else had this problem? Any way to fix it?

---

### Post by MiD-AwE on 2006-02-12
Yes. I get but I'm still a noob and don't know what to do.

---

### Post by Jaygo333 on 2006-02-12
I get the same error.
It seems a majority of the people also get it. 
Recently, the US Archives in the repositiories have been having problems and shutdown.
I've been told to go to my souces.list file and remove the word "us" from the beginning of repos with it and that makes them use all the other archives from different countries other than us.

I don't know if it works because I haven't tried it yet.

:h34r: Jaygo333 :h34r:

---

### Post by TomB on 2006-02-12
My sources list is gb as I am from England :)

---

