---
title: "install .rpm package 11.04"
date: 2011-05-09
forum: General Help
---

### Post by dale100 on 2011-05-09
I have Dell Inspiron 1420.  I installed Ubuntu 11.04.  Works great.  Even have wifi network connection.  (had an issue with that...no idea what I did, but it is working fine, for now anyhow)
Downloaded nerolinux-4.0.0.0b-x86.rpm from nero website.  (this is trial version)
Used alien to convert it to debian (sudo alien -d --scripts /location/nerolinux-4.0.0.0b-x86.rpm)
It converted with no apparent issues.
When I tried to install, it went to the software center installer, and I got the following message:
Lintian Check Results for location/fileneme: E:Nerolinux Maintainer-address-malformed.  Told me package is faulty, and could seriously damage my computer.  I re-downloaded the .rpm and went through the process again, with the same results.  Is the .rpm from the website faulty, or is there a problem with my computer?  I have talked to some who have had no such problems.  In short, what is this telling me?  Do I have a problem with my machine?  Thanks.

---

### Post by WorMzy on 2011-05-09
Why are you using converted rpms in the first place? Nero provide debs on their download page.

---

### Post by wojox on 2011-05-09
Download the [.Deb package]("http://www.nero.com/enu/downloads-linux4-trial.php")

---

### Post by dale100 on 2011-05-09
> **WorMzy said:**
> Why are you using converted rpms in the first place? Nero provide debs on their download page.

Because I'm a dunce, and did not see the rpm package.  Well, its right there, but I had been talking to someone who had used the rpm package, and I had a bit of tunnel vision.  That, and I am still learning my way around ubuntu.

Thanks for your input.

---

### Post by syedamaan on 2011-08-01
how to install nerolinux-4.0.0.0b-x86.rpm...in ubuntu 10.10??
and i want to install dc++ for sharring too..how to install it..
thnx in advance..:)

---

### Post by Mark Phelps on 2011-08-01
> **syedamaan said:**
> how to install nerolinux-4.0.0.0b-x86.rpm...in ubuntu 10.10??
and i want to install dc++ for sharring too..how to install it..
thnx in advance..:)

You can NOT install .rpm packages in Ubuntu. Period.  You have to use .DEB packages.

You can install alien -- but in my experience, it does a very poor job of converting .rpm's to .deb's.

---

