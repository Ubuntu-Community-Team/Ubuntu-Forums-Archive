---
title: "Help!  I can't uninstall/Remove an app"
date: 2011-06-05
forum: General Help
---

### Post by Max-Tyson on 2011-06-05
Help Me!  I have been trying to remove Platinum arts sandbox game making program for a while now.  I have tried using the terminal command:  sudo apt-get remove dpkg

But I keep getting an error message:

E: Could not get lock /var/lib/dpkg/lock -open (11: resource Temporarily Disable)
E: Unable to unlock the administration directory (/var/lib/dpkg/), is another process using it?

Then I typed:  /var/lib/dpkg/lock -open

Then I got the following message:

bash: /var/lib/dpkg/lock: permission denied

What does all of this mean?  Can someone help?  How come this file is locked and requires admin permission?  Please help!

---

### Post by TeoBigusGeekus on 2011-06-05
First of all, did you have Synaptic or Software Centre open while giving the command? If yes, close them.

Secondly, did you really give
```
sudo apt-get remove dpkg
```
If yes, then you're lucky it didn't work - this would have uninstalled dpkg which is a crucial package for ubuntu.

The correct command would be
```
sudo apt-get remove name_of_package
```
Replace name_of_package with whatever applicable.

---

### Post by Max-Tyson on 2011-06-05
Thanks for telling me that.

I put this into the terminal: sudo apt-get remove sandboxgamemaker

Then I got the following error message:


E: Could not get lock /var/lib/dpkg/lock -open (11: resource Temporarily Disable)
E: Unable to unlock the administration directory (/var/lib/dpkg/), is another process using it?

What I am going to do now is just turn off then on my cpu and retry.  Any other ideas?

---

### Post by Max-Tyson on 2011-06-05
Ok I got this error message after turning off, then on my cpu

[IMG]https://1059339755729925169-a-1802744773732722657-s-sites.googlegroups.com/site/maxthelinuxuser/updates/errormessages/help2.png?attachauth=ANoY7cqyxfYOUI5lQKo5CLv_NtTeO-9sz0Fksb2Uz38XJdEY4OP-ZCY1C_4Qgl0d9Dxi1KrBOTfUUjfNPQ8sPYLsDU1VL9s9usy8qaaU7zDKHVNWD4I3SuJmBxDQa2k9-9Wz1wmRtjijfbDar_r0L4jWgC2LjnpxMV2a4xtWx3_KXh4AGC-gtZ8c__7vZ4gZAuYRW8wR9CzTrvgsFdDtvjWTnGmjgJ28vr5LvqRqB2uSe15iKEDDo3U%3D&attredirects=0[/IMG]

---

