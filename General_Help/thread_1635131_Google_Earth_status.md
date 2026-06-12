---
title: "Google Earth status"
date: 2010-12-01
forum: General Help
---

### Post by jwaclawsky on 2010-12-01
Anyone know what the status of Google Earth is? Is there a package anywhere I can do a clean install, no special commands or bug bypassing activities. Just a one (or few) steps that just works? If so, please provide a pointer. Thanks!

---

### Post by gandaran on 2010-12-01
right now with the new google earth release it's a bit difficult for less experienced linux users but if you can follow instructions you can do it, I recommend using the first option from this guide, 
[http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html#more](http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html#more)
you will have to install the .deb package after following the guide build commands, and don't worry about the time it takes to build the package.

---

### Post by ell02 on 2010-12-01
Yes the webupd8 way worked for me as well.

---

### Post by DeMus on 2010-12-01
Don't go downloading it, it is right here in the repositories. Use synaptic, type googleearth and install it. Works wonderful.

---

### Post by jwaclawsky on 2010-12-01
> **DeMus said:**
> Don't go downloading it, it is right here in the repositories. Use synaptic, type googleearth and install it. Works wonderful.

What repository???  I didn't find it anywhere. I get the message "there isn't a googleearth package in my current software sources" and Synaptic doesn't have it either (I have medibuntu in my software sources)

ALSO, As an ancillary question if I have a googleearth package already running on another machine can I just copy over the package or some file(s) and install it on a new machine? Has anyone tried doing that? Is it possible or too complex and won't work?

---

### Post by bkratz on 2010-12-01
> **jwaclawsky said:**
> What repository???  I didn't find it anywhere. I get the message "there isn't a googleearth package in my current software sources" and Synaptic doesn't have it either (I have medibuntu in my software sources)

ALSO, As an ancillary question if I have a googleearth package already running on another machine can I just copy over the package or some file(s) and install it on a new machine? Has anyone tried doing that? Is it possible or too complex and won't work?

that is how I did it too.  Once I had the medibuntu repository installed, I found it with that name and it worked well. I just checked and did a search for earth (lazy) and found it right away.
Don't know about the second question though.

---

### Post by jwaclawsky on 2010-12-01
Googleearth is not showing up when I click on Medibuntu in the Ubuntu software center???  In fact I only see 5 items in the list? Anyone have any idea what I might be doing wrong. I see the Medibuntu items listed under "other software" and the box is checked in front of the Medibuntu list items in software sources???

---

### Post by clhsharky on 2010-12-01
jwaclawsky

No two click solution (have no idea why)but copy/paste is not hard. I used googleearth-package method for latest stable,here
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

and GE6 beta testing here
[http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed](http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed)

Tried both I prefer stable version ATM.

Sharky

---

### Post by sgosnell on 2010-12-01
It's in the multiverse repository.

---

### Post by Agent ME on 2010-12-01
Ubuntu 10.10 even with multiverse and medibuntu repositories doesn't have the pre-built googleearth package. Which is strange since it seemed the 10.04 medibuntu repository had it.

---

### Post by jwaclawsky on 2010-12-02
How do I add the multiverse repository? Is there a link to some place explaining how?

---

### Post by gandaran on 2010-12-02
> **jwaclawsky said:**
> How do I add the multiverse repository? Is there a link to some place explaining how?
you already have the multiverse repository, check in software sources.
just to make it clear there is no google earth in any repository either multiverse or medibuntu for ubuntu 10.10, there is for ubuntu 10.04 from the medibuntu repository only ( if you could add the medibuntu 10.04 repository version to ubuntu 10.10 then yes you would find google-earth ready to install but would be an old version)
installing the new google earth package is not so difficult, look at it this way, you need to install only two packages from package manager (for 32-bits system only)

1º lsb-core
2º googleearth-package

then run the build deb package command in terminal
```
make-googleearth-package --force
```
wait till the deb package is ready then click the deb to install
is this difficult?

---

### Post by jwaclawsky on 2010-12-02
Thanks gandaran, for the clarification. I will do as you suggest. Many thanks for the assistance.

---

### Post by ranjan_mg on 2010-12-02
I installed google earth 6. The fonts are awful. I played with QT4 settings - it looks as though antialiasing is not working. 
Anyone else seen this issue ?

---

