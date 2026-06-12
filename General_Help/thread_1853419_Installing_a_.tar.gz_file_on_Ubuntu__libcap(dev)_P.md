---
title: "Installing a .tar.gz file on Ubuntu / libcap(dev) Package"
date: 2011-10-02
forum: General Help
---

### Post by hollowterror on 2011-10-02
Hi, I am currently trying out Ubuntu on a virtual machine and I am having a problem with getting a particular program that I downloaded to run (I downloaded it in .tar.gz format).

After I extracted the program in the Downloads folder, I opened the console and typed ./configure (in the Downloads path). However an error comes up telling me:

"libcap (dev) is required for this program".

I then opened the Synaptic Package Manager and installed all the libcap packages that I found (libcap-ng-dev, libcap2-bin and libcap-dev). However when I typed the ./configure command again, I still got the same error. I tried restarting the machine but the error still comes up.

So what do I need to do in order to solve this error?

Thanks in advance, any help will be greatly appreciated.

---

### Post by oldos2er on 2011-10-02
What is the program you downloaded? Which version of Ubuntu are you using?

---

### Post by hollowterror on 2011-10-03
> **oldos2er said:**
> What is the program you downloaded? Which version of Ubuntu are you using?

I am using the 32-bit version of Ubuntu 11.04. I have been trying to install this program [http://sourceforge.net/projects/ddosim/](http://sourceforge.net/projects/ddosim/) which is a DDOS simulator; so maybe I can have a better and more practical understanding of DDOS attacks.

---

### Post by oldos2er on 2011-10-03
Check here: [http://stormsecurity.wordpress.com/2009/03/03/application-layer-ddos-simulator/](http://stormsecurity.wordpress.com/2009/03/03/application-layer-ddos-simulator/)
scroll down a bit more than halfway through the page and you'll see a post titled 'Installing in Ubuntu 10.10'

Hope that helps.

---

### Post by hollowterror on 2011-10-03
> **oldos2er said:**
> Check here: [http://stormsecurity.wordpress.com/2009/03/03/application-layer-ddos-simulator/](http://stormsecurity.wordpress.com/2009/03/03/application-layer-ddos-simulator/)
scroll down a bit more than halfway through the page and you'll see a post titled 'Installing in Ubuntu 10.10'


Thanks for the link. I did try out the steps shown in that particular comment, however the package ([libnet0-dev_1.0.2a-7_amd64.deb]("http://mirrors.us.kernel.org/ubuntu//pool/universe/libn/libnet0/libnet0-dev_1.0.2a-7_amd64.deb")) that the user suggests to install is only valid for 64-bit machines. Is there any equivalent libnet0 package for the 32-bit version of Ubuntu? I googled the package for the 32-bit version but I wasn't able to find anything useful.

---

### Post by azmyth on 2011-10-03
libnet0-dev has been replaced by libnet1-dev. Unfortunately, the function names changed so you can't just install libnet1-dev to make it work.

---

### Post by hollowterror on 2011-10-04
> **azmyth said:**
> libnet0-dev has been replaced by libnet1-dev. Unfortunately, the function names changed so you can't just install libnet1-dev to make it work.

Is there any way to go around this problem? If no, what was the latest version of Ubuntu that had the libnet0-dev package so that I could use that one instead.

Thanks.

---

### Post by oldos2er on 2011-10-04
You can search here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

