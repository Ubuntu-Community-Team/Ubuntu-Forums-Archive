---
title: "Firefox 3.5 with Ubuntu 8.10???"
date: 2009-07-04
forum: General Help
---

### Post by FMJammo on 2009-07-04
Hello!

I tried to install Firefox 3.5 on Ubuntu 8.10, i got this error quoted in terminal: 

''Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  firefox-3.5: Depends: xulrunner-1.9.1 (>= 1.9.1) but it is not going to be installed
               Depends: libasound2 (> 1.0.18) but 1.0.17a-0ubuntu4 is to be installed
               Depends: libgtk2.0-0 (>= 2.16.0) but 2.14.4-0ubuntu1 is to be installed
               Depends: libnspr4-0d (>= 4.7.3-0ubuntu1~) but 4.7.1+1.9-0ubuntu4 is to be installed
E: Broken package''

Maybe i need to upgrade...but i don't want right now because AMD has still not released drivers for my video card for Ubuntu 9.04. Or maybe they are somewhere...if someone could point me.


Thanx alot.

---

### Post by wojox on 2009-07-04
How exactly did you install it?

---

### Post by FMJammo on 2009-07-04
> **wojox said:**
> How exactly did you install it?

I have followed these instructions: [http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)

---

### Post by mc4man on 2009-07-04
The firefox your trying to install was built for jaunty (libgtk2.0-0 (>= 2.16.0, ect.

There are some ppa's that have firefox 3.5  for both intrepid and hardy.
Can't vouch for them though, may try on a tester

Ex.
[https://edge.launchpad.net/~fta/+archive/ppa](https://edge.launchpad.net/~fta/+archive/ppa)

[https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

[https://edge.launchpad.net/ubuntu/+ppas?name_filter=Firefox+3.5](https://edge.launchpad.net/ubuntu/+ppas?name_filter=Firefox+3.5)

It may show up as a backport at some point (3.5

went with method in next post, not that keen myself on using ppa's for certain things (firefox, video drivers

---

### Post by aysiu on 2009-07-05
This will help you get Firefox 3.5 installed in Ubuntu 8.10:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by binbash on 2009-07-05
[http://www.ubuntu-inside.me/2009/05/daily-firefox-35-36-repository-for.html](http://www.ubuntu-inside.me/2009/05/daily-firefox-35-36-repository-for.html)

---

### Post by aysiu on 2009-07-05
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/05/daily-firefox-35-36-repository-for.html](http://www.ubuntu-inside.me/2009/05/daily-firefox-35-36-repository-for.html)
I believe that's what the OP tried already. Isn't that specifically for Jaunty users and not Intrepid users?

---

### Post by mc4man on 2009-07-05
Went with the link in post 5 (for hardy), used the Ubuntuzilla script method. (.deb)

Worked flawlessly, is easily updated when available and can be reverted if desired.

---

