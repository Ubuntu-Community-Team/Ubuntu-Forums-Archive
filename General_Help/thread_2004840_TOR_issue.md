---
title: "TOR issue"
date: 2012-06-16
forum: General Help
---

### Post by z3rO88 on 2012-06-16
Hi, i have installed tor on my ubuntu and having issues with the interface vidalia (GUI) for tor, when i load the tor up it comes up with this error:

[http://img225.imageshack.us/img225/2402/50931897.png](http://img225.imageshack.us/img225/2402/50931897.png)

The logs shows this:

[http://img546.imageshack.us/img546/2045/12921653.png](http://img546.imageshack.us/img546/2045/12921653.png)


Anybody know any idea the problem with this, i have tried un-installing an re-installing the software , tried updating the software but all i can find is the source package

---

### Post by Redblade20XX on 2012-06-16
Sorry I don't really know what your problem is but it seems as if it's  a permission conflict.

I wouldn't recommend TOR on a Ubuntu box (if your using it as your main os, ie. personal information, banking, private stuff etc) it just defeats the purpose of TOR.

I would suggest you look into a distribution called TAILS. It is specifically designed for privacy (built in TOR) and is acknowledged by FSF.

Here's a link if you want to check it out: 
[https://tails.boum.org/about/index.en.html](https://tails.boum.org/about/index.en.html)

-Red

---

### Post by z3rO88 on 2012-06-16
thanks very much for the info ill look into it :) if get stuck could i pm you ?

---

### Post by Redblade20XX on 2012-06-16
> **z3rO88 said:**
> thanks very much for the info ill look into it :) if get stuck could i pm you ?

According to the forums, it's discouraged because other people wouldn't be able to view helpful info.
.
But with me, I'm okay with it. :)

-Red

---

### Post by z3rO88 on 2012-06-16
thanks your a star, i am on my last year in uni an creating a project this going to be part of my toolkit on ubuntu distro

---

### Post by z3rO88 on 2012-06-16
ah just properly read tails, its a iso its own OS, damm i need one that i can integrate into ubuntu

---

### Post by Redblade20XX on 2012-06-16
> **z3rO88 said:**
> ah just properly read tails, its a iso its own OS, damm i need one that i can integrate into ubuntu

Sorry about that.

It's based on debian which Ubuntu is already based on. You can install it on a usb or burn it to a dvd to just check out TOR if you want and then use your hdd for Ubuntu development.

-Red

---

### Post by z3rO88 on 2012-06-16
ye ill still check it out but still grateful for the help :) basically my project is to provide tools to a network administrator which will keep the network secure, any idea on tools to put into it :)

---

### Post by haqking on 2012-06-16
> **z3rO88 said:**
> ye ill still check it out but still grateful for the help :) basically my project is to provide tools to a network administrator which will keep the network secure, any idea on tools to put into it :)

TOR has nothing to do with security (though there is encryption), it is about privacy and some anonymity which are different topics.

I would not use TOR for security

---

### Post by z3rO88 on 2012-06-16
ah oke, thanks any idea on other tools to use ?

---

### Post by haqking on 2012-06-16
> **z3rO88 said:**
> ah oke, thanks any idea on other tools to use ?

Security is a process and not a product.

My first question would be why does a network admin not know how to secure their network in the first place, and why you are tasked with doing so if you dont know how to ?

The type of network, OS in use, data type and value, compliance or law are all essential elements to take under review before deciding on and implementing technical controls as part of a security  framework.

You need to be more specific.

Peace

---

### Post by Redblade20XX on 2012-06-16
> **z3rO88 said:**
> ah oke, thanks any idea on other tools to use ?

Oh your doing a security project. Yeah then as haqking has said you'll probably not want to use TOR. Try looking up a penetration distro for ideas...

-Red

---

### Post by z3rO88 on 2012-06-16
Hi, i am creating a distro on security that will be implemented into the distro, this would keep a network secure does anybody have any suggestions on what programs to include into the distro

so far i have

nmap/zenmap
w3af
wireshark
john the ripper

few more any suggestions on more ?

---

### Post by haqking on 2012-06-16
> **Redblade20XX said:**
> Oh your doing a security project. Yeah then as haqking has said you'll probably not want to use TOR. Try looking up a penetration distro for ideas...

-Red

Penetration distros do not provide security, they are suites of tools for penetration testing and security auditing.

Infact due to the services they are often running then secure browsing or network activity is not recommended from them unless you know what are you doing, which i am assuming is not the case from the posts so far, all due respect to all of course.

Peace

---

### Post by codemaniac on 2012-06-16
BackTrack has an good list of security tools available in it's offering .You can try extending/customizing backtrack and include the tools you feel need to be added .

---

### Post by haqking on 2012-06-16
> **z3rO88 said:**
> Hi, i am creating a distro on security that will be implemented into the distro, this would keep a network secure does anybody have any suggestions on what programs to include into the distro

so far i have

nmap/zenmap
w3af
wireshark
john the ripper

few more any suggestions on more ?

This is a continutation of your other thread here [http://ubuntuforums.org/showthread.php?t=2004840](http://ubuntuforums.org/showthread.php?t=2004840)

duplicate posting on same topic is not recommended.

However those tools do not make a network secure, it is the knowledge of the person using them.

Also if you need help on this then it is not likely to be of any use to anyone.

In addition there are already industry standards for these distros such as Backtrack 5 currently in release 2,

Cheers

---

### Post by nothingspecial on 2012-06-17
merged

---

