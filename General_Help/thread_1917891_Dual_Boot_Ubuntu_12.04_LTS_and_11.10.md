---
title: "Dual Boot Ubuntu 12.04 LTS and 11.10?"
date: 2012-01-30
forum: General Help
---

### Post by chughes27 on 2012-01-30
Is it possible for me to dual boot Ubuntu 12.04 and Ubuntu 11.10? Because I like my Ubuntu 11.10, but would also like to install 12.04 to fully try it out. 

If it is not possible, what are the major differences between 12.04 and 11.10, and which is better performance-wise?

---

### Post by overdrank on 2012-01-30
> **chughes27 said:**
> Is it possible for me to dual boot Ubuntu 12.04 and Ubuntu 11.10? Because I like my Ubuntu 11.10, but would also like to install 12.04 to fully try it out. 

If it is not possible, what are the major differences between 12.04 and 11.10, and which is better performance-wise?

Hi and yes you can dual boot. You may also choose to use a virtual machine to test 12.04. :)

---

### Post by Bucky Ball on 2012-01-30
One's released and one is not. 12.04 LTS is still testing and will be until April. Don't expect reliability or stability. You would be testing the release and helping developers by reporting any bugs. You wouldn't use the release for production machines, put it that way. The next update might kill everything ... or improve some things. It's like that and shouldn't be an unexpected outcome with a testing release (so don't complain if that happens, just report the problems and move on). If you're looking to learn you will by trying to fix any probs that occur.

[http://www.ubuntugeek.com/the-ubuntu-release-cycle.html](http://www.ubuntugeek.com/the-ubuntu-release-cycle.html)

This link gives a better idea of the release cycle. Take note, 12.04 LTS is not there yet and will appear in April 2012 sometime (thus the 12.04 release number). One other (main) difference is that LTS releases are supported for three years, server version five, intended to be stable and for use on production machines. 

Good luck. ;)

---

### Post by chughes27 on 2012-01-31
What I actually did was install it to a usb and boot it from there without installing it on my HDD. Works fine for my original purpose of just testing it out.

---

### Post by Paqman on 2012-01-31
> **overdrank said:**
> Hi and yes you can dual boot. You may also choose to use a virtual machine to test 12.04. :)

You can, but it's more useful to use the testing branch on bare metal. Testing in a VM won't identify any hardware issues.

---

### Post by chughes27 on 2012-01-31
After testing it from the usb, I didn't really notice a whole lot of differences. Should there have been major differences in 12.04 to anyone who has installed and fully tested it?

---

### Post by Paqman on 2012-01-31
> **chughes27 said:**
> Should there have been major differences

Nope, it's just a few tweaks and updated packages. The LTS releases tend to be a bit more conservative about introducing major new features, the focus is on polishing and extra testing for existing stuff. That's why you saw Unity being introduced over the last couple of releases, so that it would be ready before the LTS.

---

