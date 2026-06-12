---
title: "Empathy cant connect to Google Talk after upgared to 10.10"
date: 2010-10-20
forum: General Help
---

### Post by ilya222 on 2010-10-20
After I upgraded from 10.04 to 10.10 the Emapthy google talk account gives me "Network Error" and won't connect. I tried removing and adding again the account and even the whole program and it didn't help.
A faecebook account works fine.

---

### Post by ubudog on 2010-10-20
Do you have to use Empathy?  You could try Pidgin, which also supports encryption.  They have a package that's really easy to install too.

[http://pidgin.im/](http://pidgin.im/)

---

### Post by ilya222 on 2010-10-20
thanx but i really liked empathy, is there no solution for this? it seems i'm not the only one with this problem

---

### Post by ubudog on 2010-10-20
Hmm, well try this and see if it works:

Add this ppa: (to your software sources)

ppa:telepathy/ppa

And then start Update Manager and install the latest version.  That may/should fix it.  Good luck!

---

### Post by ThePhysician on 2010-10-20
Sadly, Empathy is one of the worst coded programs probably out there.

MSN fails to connect often, people have problems with Google Talk, **you can't see if someone is mobile or on their computer on AIM** (although you can on every other program in existence), just numerous issues.

---

### Post by ubudog on 2010-10-20
Reinstalling may help, but you may have to go with Pidgin.  Also if you don't like the way Pidgin looks, there are many themes floating around out there.

---

### Post by Nosferax on 2010-10-21
I can't connect with pidgin either... before upgrading both were able to connect to google talk just fine.

---

### Post by ubudog on 2010-10-21
Did you try updating Empathy yet?

---

### Post by Nosferax on 2010-10-21
Well, yes, everything is updated to the latest version in the ubuntu repositories. I'm not using the empathy ppa, if there is such a thing. 

Also, I found out that I am able to connect to google talk, but I need to leave empathy opened for a long time while it tries to connect, and after maybe 10 minutes it connects to google talk. I don't understand why it does this, since on the web interface of google talk (through gmail), it connects without any delay - so this rules out firewall matters.

---

### Post by ubudog on 2010-10-21
> **ubudog said:**
> Hmm, well try this and see if it works:

Add this ppa: (to your software sources)

ppa:telepathy/ppa

And then start Update Manager and install the latest version.  That may/should fix it.  Good luck!

Did you try that?

---

### Post by wcorey on 2010-10-22
I had just the opposite result. At home I upgraded to 10.10 from 10.4 and I can connect via Empathy to everything (google, and multiple Yahoo accounts). Yesterday I upgraded another machine from 9.10 to 10.4 and everything worked fine for a while then I lost connectivity to Yahoo...either acct with the dreaded "Network Error".  I do not seem to have that issue at home.

---

### Post by Nosferax on 2010-10-22
I added the telepathy ppa and upgraded to the newer packages available there. No difference. Still takes ages.

---

### Post by ubudog on 2010-10-22
Hmm... :-k

---

### Post by Nosferax on 2010-10-23
I also noticed that using the newer empathy versions from ppa broke messaging indicator support.

---

### Post by Poisonflash on 2010-12-05
I have had exactly the same error. It turned out to be moblock blocking google talk for empathy. Worked fine via web interface and on my other PC with 10.04 in exactly same setup. No idea why. Anyway, allowing Google in moblock fixed it

---

