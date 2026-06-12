---
title: "Kde remore desktop freezes PC"
date: 2006-01-30
forum: General Help
---

### Post by Gowator on 2006-01-30
Ive being trying to use the KDE remote desktop but it appears that as soon as it times out the slave machine just locks up.  
It shows activity on the NIC but I can't telnet or ssh into it or even ping it.  No error messages I can see it just completely stops responding and needs a power cycle.

---

### Post by jbus on 2006-01-30
I had a similar problem with Xephyr/xdmcp. I'm not sure if this will help you, but it stopped my PC from locking up when I attempted a remote connection to it with Xephyr.

To solve the problem I had had to make sure my /etc/kde3/kdm/kdmrc had Xdmcp enabled:

[Xdmcp]
Enable=true

And...

I had to uncomment this line in my /etc/kde3/kdm/Xaccess file
# * #any host can get a login window

So that it looks like this:
* #any host can get a login window

---

### Post by Gowator on 2006-02-10
Didn't work ..... hey ho..it has been a week but I guess I'll get slammed for bumping this

---

### Post by Gowator on 2006-02-15
Sorry, I know its only 4 days since the last bump but I am getting desperate on this (its almost 2 weeks since the first post) it causes a total lockup and I need to power cycle each time it locks.  

Has anyone tried this or is noone else using the krfb stuff?

---

### Post by Gowator on 2006-02-25
Please anyone, its now another week with no answer and everytime I try and go forwards I worry I am going to loose everything on my remote server.  I have no screen keyboard etc. and I have to power cycle each time it locks up so experimenting isn't easy.  

I don't understand, does no-one else use krdc or is my English not good enough? or is it just not an interesting topic or what?    

3 weeks and one partial answer ?

---

### Post by GeneralZod on 2006-02-25
[QUOTE=Gowator]
I don't understand, does no-one else use krdc or is my English not good enough? or is it just not an interesting topic or what?    
[/QUOTE]

Most likely, people here simply don't know the answer and/ or have never experienced the same bug as you.  

Approximately 1 time in 10, vnc'ing into my desktop from my laptop will cause my laptop to lock up, but CTRL+ALT+F1 still works for me so I can just kill krdc and everything's back to normal.

---

### Post by Gowator on 2006-02-26
Thanks ... General :D  at least someone finally answered, I guess the bug might be in the vnc packages if that is the case.  I was thinking of using NX instead but  it is probably easier to just install Deb unstable via kanotix since I then get my other bugbear's working like musicbrainz lookup etc.  problem is its a production server so hopefully will be backed up by the end of today for me to install Debian.

---

