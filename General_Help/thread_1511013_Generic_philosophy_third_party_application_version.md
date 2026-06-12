---
title: "Generic philosophy: third party application version management"
date: 2010-06-16
forum: General Help
---

### Post by Ewea on 2010-06-16
Even though I have been using Linux for quite some time now (as a  private web server), now that I want to create a new web server, I am willing to know exactly what is the philosophy of Ubuntu regarding package version management.

Let's use phpBB as an example, as I used it on my first server, and I intend to use it again on my new one.
[B]
phpBB is currently in version 3.0.7
In the official Ubuntu software repository, phpBB is currently in version 3.0.4
[/B]
Now I am facing a philosophical question: _should I simply download the official version and simply deal with it, or is it more 'the Ubuntu philosophy' to stick to the 'supported' version, 3.0.4, even though, this version is a year and a half old?_

I know that Ubuntu is based on Debian, which is itself a very secured Linux, which will only offer validated versions of software. And as such, man should not expect to always see the latest versions available.
However, I am now wondering, is it better, security-wise, to stick to the 'validated' 3.0.4 or to go use the original 3.0.7? Because as all the holes of 3.0.4/5/6 are now known, I am not quite sure that sticking to 3.0.4 is for the best.

Now it came to my mind that the philosophy might simply be to use APT to get the latest valid version, and then to simply use the internal upgrade tool of phpBB to upgrade to 3.0.7.
But as the phpBB as it is available for Ubuntu is really modified, in terms of files being splitted in many different folders, will the automated upgrade work?
And what will happen when Ubuntu will upgrade their version? What happens if they upgrade to a lower than latest version? Or to the latest (not even sure this would happen one day)?

And now finally, phpBB has an integrated upgrade feature, but what about all this for a software that doesn't have such a tool (MediaWiki for instance)?



I hope you will understand that I know exactly how to deal with the final versions manually, and that all I am looking for here, is an understanding on what a proper Linux server administrator is 'expected' to do?

Thanks

---

### Post by Ewea on 2010-06-17
No one can help me on this?

---

