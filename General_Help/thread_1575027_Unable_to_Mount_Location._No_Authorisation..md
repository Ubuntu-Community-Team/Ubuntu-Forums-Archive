---
title: "Unable to Mount Location. No Authorisation."
date: 2010-09-15
forum: General Help
---

### Post by wetinwales on 2010-09-15
Ubuntu 10.04 64bit. Strictly Dedicated Ubuntu machine. All OK for many months. I keep the operating system on one sata HDD and all stored files on two other sata HDDs 
Twice in the last few weeks the following has happened after the nightly update:-

I am unable to access the two storage HDDs, an external HDD and any ext USB drives.
The message is common to all:- 

[B]Unable to Mount Location
No Authorisation[/B].

A re start corrected the isue two weeks ago. Today it would not resolve.

A search through the forum [http://ubuntuforums.org/showthread.php?t=1484700]("http://ubuntuforums.org/showthread.php?t=1484700") revealed a similar issue where Ubuntu and Windows were dual booted.
However I tried the command:-
 
```
sudo ufw disable
```

re started machine and the problem was solved.
I then enabled ufw and the HDDs are accessible.

I post this as I could not find any reference to this exact problem - so it may help someone else.
Any comments ?:)

---

