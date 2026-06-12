---
title: "openoffice downgrade"
date: 2009-11-17
forum: General Help
---

### Post by gnuplot on 2009-11-17
Hi folks!
I just upgraded to Ubuntu 9.1. As many of you know, there is a very annoying bug in openoffice 3.1, which occurs when one is using subscripts or superscripts in impress ( [http://www.openoffice.org/issues/show_bug.cgi?id=106609](http://www.openoffice.org/issues/show_bug.cgi?id=106609) ). This makes impress unusable for my purposes. 

My question is, what is the best way to downgrade to say the openoffice version in ubuntu 9.04? Adding the 9.04 repositories to my current ones? Or perhaps wiping out the entire openoffice and installing the latest version from Sun (it doesn't have the bug). I sort of tried the latter on another computer running 9.04 but openoffice keeps crashing.

Any insights? Thanks a lot!

---

### Post by Hagar Delest on 2009-11-17
Have you tried to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403)? but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

The Sun version has always worked fine on my xubuntu boxes.

---

### Post by gnuplot on 2009-11-17
Thanks for the reply! I tried it, still the same problem...
It is really frustrating that Ubuntu doesn't care enough to fix something which will probably take them 10 min to do. Right now they are losing a lot of people who would like to use openoffice 3.1 for scientific presentations that include subscripts and superscripts.

---

### Post by Hagar Delest on 2009-11-18
And have you tried with the Sun version? See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by gnuplot on 2009-11-19
Well, I was already talking about Sun's version. Actually, good news, I also installed the desktop integration package and now the program doesn't crash. I had completely overlooked it, and I didn't think it was important anyway. 

Then I did the same thing on another computer and openoffice kept crashing again, but that went away after I removed the old .openoffice directory. I had tried this before on my laptop and it had not solved the problem until I installed the desktop integration package. It seems to me that the problem was a combination of having the old .openoffice folder and not installing the desktop integration.

Thanks for your replies!

---

