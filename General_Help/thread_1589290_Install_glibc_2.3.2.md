---
title: "Install glibc 2.3.2"
date: 2010-10-06
forum: General Help
---

### Post by 1maddog on 2010-10-06
I need to have glibc 2.3.2 for the install of Oracle XE in my Ubuntu 10.04 OS. When I enter glibc into Ubuntu Software Center I only find "The Berkeley database routines [glibc 2.1/2.1 compatability]". I'm guessing a newer version of glibc would work as well. I've done some searches but no real joy. Any suggestions how to get a runtime install package of glibc 2.3.2 or greater?

Thanks...

---

### Post by mc4man on 2010-10-06
Not exactly sure what you're looking for - glibc is a source that produces several packages, most notably libc6
At this point ubuntu is well beyond glibc 2.3 (eglibc now, 2.11 in lucid)
[http://packages.ubuntu.com/search?searchon=names&keywords=eglibc-source](http://packages.ubuntu.com/search?searchon=names&keywords=eglibc-source)

check out the changlelog for libc6 in synaptic to see progression from dapper (glibc-2.6) to now

---

### Post by 1maddog on 2010-10-06
What I'm look for is to satisfy the requirement, according to Oracle's system requirements for Oracle XE, that packages "glibc - 2.3.2" and "libaio - 0.3.96" be installed. I checked Synaptic Package Manager as you suggested and it would appear that the current versions of the required packages are present. So for I will take this as the system is good to go and will proceed with the install.

Thanks for the info...

---

