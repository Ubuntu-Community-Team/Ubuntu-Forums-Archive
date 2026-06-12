---
title: "Can't remove virtual packages"
date: 2012-09-07
forum: General Help
---

### Post by Kopkins on 2012-09-07
Running bleach bit today and it picked up on a bunch of stuff from the opera browser. I thought oh I never use opera. So, ```
kyle@Kopkins:~$ sudo apt-get purge opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'opera' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kyle@Kopkins:~$ 

```

Then I think didn't I already do this. Open the dash and type opera, no results.

What is going on?

Thanks,
Kopkins

---

### Post by Epodx64 on 2012-09-07
I generally just use the rm command to remove .deb packages not sure if this is what you mean or not though?

---

### Post by Kopkins on 2012-09-07
Yeah, I remember getting a .deb to install opera, any idea where that would be?

Thanks, Kopkins

---

### Post by rockstarrem on 2012-09-07
Opera isn't even an installation candidate. If it is installed it's a different package.

```
snowtiger@snowtiger:~$ sudo apt-get install opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'opera' has no installation candidate

```

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by Kopkins on 2012-09-07
Yeah, I know it's not available through the default repo's. I grabbed a .deb from the opera webpage. Maybe it's just a line in a file somewhere telling my system that opera is still here. I did **sudo find / -name opera** and it didn't come up with anything. 

Sorry for the trouble, and thank you for your help. I'm marking solved.

Kopkins

---

### Post by Epodx64 on 2012-09-07
> **Kopkins said:**
> Yeah, I remember getting a .deb to install opera, any idea where that would be?

Thanks, Kopkins

[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

You can get 12.02 from there '.deb' file I think they have the beta version around there somewhere to

---

### Post by rockstarrem on 2012-09-07
> **Kopkins said:**
> Yeah, I know it's not available through the default repo's. I grabbed a .deb from the opera webpage. Maybe it's just a line in a file somewhere telling my system that opera is still here. I did **sudo find / -name opera** and it didn't come up with anything. 

Sorry for the trouble, and thank you for your help. I'm marking solved.

Kopkins

Sorry, didn't read the whole topic haha. Looks like Epodx64 has you covered.

---

### Post by Kopkins on 2012-09-07
> **Epodx64 said:**
> [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

You can get 12.02 from there '.deb' file I think they have the beta version around there somewhere to

Sorry, I meant where it would be on my system, so that I could get rid of it. 

Thank you,
Kopkins

---

### Post by Epodx64 on 2012-09-07
> **Kopkins said:**
> Sorry, I meant where it would be on my system, so that I could get rid of it. 

Thank you,
Kopkins

oh lol, yeah i think it's in /opt/opera

---

