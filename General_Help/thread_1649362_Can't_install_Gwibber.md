---
title: "Can't install Gwibber"
date: 2010-12-20
forum: General Help
---

### Post by iosuna86 on 2010-12-20
I am running Ubuntu 10.10.

So I decided to remove Gwibber from the Software Center and now I want it back on. I go to Ubuntu Software Center and try to install it, but the following message appears:

> Package dependencies could not be resolved 

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details:
gwibberI tried installing other things from Software Center and they all get installed. 

And this is what I get from the terminal:

```
iosuna86@iosuna86-M70Vn:/$ sudo apt-get install gwibber
[sudo] password for iosuna86: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gwibber : Depends: gwibber-service (= 2.32.0.2-0ubuntu1) but 2.32.2-0ubuntu2 is to be installed
E: Broken packages
```


Anyone knows what's wrong?

Thanks in advance.

---

### Post by iosuna86 on 2010-12-20
I figured it out on my own. 

I went to Synaptic and removed gwibber-service.

Now I went to the terminal apt-get install gwibber and everything is back as usual.

---

