---
title: "dependency issues"
date: 2011-10-08
forum: General Help
---

### Post by boeckelr on 2011-10-08
I have what is probably (hopefully) an easy problem for one of you Ubuntu gurus to fix.

OK I am trying to install Snort 2.9.9.1 on Ubuntu 10.043 32bit.

Snort and its support app DAQ require libpcap version greater than 1.  

Of course Ubuntu installs libpcap0.8, right with its default install, and there are lots of packages that depend on it.

What do I do?  

Do I do an "apt-get remove libpcap".....and have Ubuntu remove it along with everything that depended on it....then compile from source libpcap 1.1.1....?  If I do that can I then go and reinstall all of the packages Ubuntu originally installed that relied on libpcap?

Or something else?

I have been trying various things and have been getting symbolic link errors, among other things,

Any help that you can give will be greatly appreciated.

Thanks,
Mike

---

