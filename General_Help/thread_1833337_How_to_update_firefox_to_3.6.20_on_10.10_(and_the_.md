---
title: "How to update firefox to 3.6.20 on 10.10? (and the related apparmor questions)"
date: 2011-08-25
forum: General Help
---

### Post by nnn= on 2011-08-25
On 10.10, the current firefox is 3.6.18. I'd like to update to 3.6.20. How to do so?

In /etc/apparmor.d there is a profile called usr.bin.firefox. Inside it, there is code saying: /usr/lib/firefox-3.6.18/firefox-*bin.
So when I update firefox, will the profile get updated also? I don't know how this profile got there; probably it was installed along with the firefox package. Is that so?

---

### Post by nnn= on 2011-08-26
Still need help.

---

### Post by hasardeur on 2011-08-26
Have you tried:

```
sudo apt-get update && sudo apt-get upgrade
```

The apparmor profiles will be updated automatically. You don't need to edit them.
Does this answer you question? I get the feeling that I didn't quite get what you are trying to do.

---

### Post by garvinrick4 on 2011-08-26
Why not install the mozill ppa stable and use the last stable release of firefox
is a big difference from 3.6 in appearance. Just a thought is all.
[http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable?dist=maverick](http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable?dist=maverick)

---

### Post by nnn= on 2011-08-28
> **hasardeur said:**
> Have you tried:

```
sudo apt-get update && sudo apt-get upgrade
```The apparmor profiles will be updated automatically. You don't need to edit them.
Does this answer you question? I get the feeling that I didn't quite get what you are trying to do.

It doesn't update past 3.6.18.

> **garvinrick4 said:**
> Why not install the mozill ppa stable and use the last stable release of firefox
is a big difference from 3.6 in appearance. Just a thought is all.
[http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable?dist=maverick](http://www.ubuntuupdates.org/ppa/mozilla_team_firefox_stable?dist=maverick)

Because some of my extensions are incompatible with that, and I like 3.6 better.

---

### Post by raja.genupula on 2011-08-28
open synaptic manager , in search box type firefox . then its gonna show you current version and latest update . there you can go

---

### Post by VanR on 2011-08-28
Frankly I wouldn't update past Firefox 6. 6 seems stable while Firefox 7 and 8 kept crashing on me and had to go bye-bye.

---

### Post by nnn= on 2011-08-29
I got it fixed, it wasn't updating the db. Thank you everyone for your answers. It was they who lead towards the solution.

---

