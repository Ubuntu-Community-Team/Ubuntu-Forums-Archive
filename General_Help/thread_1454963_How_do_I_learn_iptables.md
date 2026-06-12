---
title: "How do I learn iptables"
date: 2010-04-15
forum: General Help
---

### Post by ant2ne on 2010-04-15
I'm looking for a good instructable on using the command line iptables. I'm broke and can't afford a book so an informative website would be great. It would need to have an instructable that took me from knowing very little to the more advanced concepts and features.

Any suggestions?

And if anyone suggests "man iptables" I'm going to hurt them ;-[

---

### Post by bwhite82 on 2010-04-15
The best source seems to be netfilter

[http://www.netfilter.org/documentation/index.html#documentation-howto](http://www.netfilter.org/documentation/index.html#documentation-howto)

---

### Post by Sef on 2010-04-15
Start [here]("https://help.ubuntu.com/community/IptablesHowTo") for a tutorial on IP Tables.

---

### Post by gmargo on 2010-04-15
> **ant2ne said:**
> And if anyone suggests "man iptables" I'm going to hurt them ;-[

Why, are you allergic to knowledge? :)  It's a really good source of information, but not a beginner text. There is a lot of documentation included with the **iptables** package, look under **/usr/share/doc/iptables/html/**.

The Wikipedia entry has about the best diagram I've ever seen for the iptables packet flow.  Understanding the packet flow is the key to understanding iptables.

[http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)
[http://en.wikipedia.org/wiki/File:Netfilter-packet-flow.svg](http://en.wikipedia.org/wiki/File:Netfilter-packet-flow.svg)

And of course, Google points to lots of nice stuff.  This tutorial looks good: [http://www.faqs.org/docs/iptables/](http://www.faqs.org/docs/iptables/)

---

### Post by ant2ne on 2010-04-16
> **gmargo said:**
> but not a beginner text. That is my point exactly. I don't consider myself a linux beginner, but iptables has been one of them areas where I'd cheat and use firestarter or other gui firewall builder. I'd like to get a firm grasp of iptables.

---

### Post by gmargo on 2010-04-16
> **ant2ne said:**
> I'd like to get a firm grasp of iptables.

I learned a tremendous amount by writing my own firewall script (shell script driving iptables), back before I had an external router device.  My Linux box _was_ the firewall machine (two ethernet interfaces, one running PPPOE for a DSL link, one for the internal network.)  That was great because I got to see all the raw traffic coming from the internet.  It is quite eye-opening to see the huge volume of cracking attempts.

I've since moved my firewall script to a Shorewall implementation, plus got an external router.  I don't know if my original script (from 2001) would be of general interest so I won't post it, but I'd be happy to email you a copy if you want it.

---

### Post by ant2ne on 2010-04-16
> **gmargo said:**
> I learned a tremendous amount by writing my own firewall script (shell script driving iptables)
That is basically what i intend to do, after I get an understanding
 >  I won't post it, but I'd be happy to email you a copy if you want it.Sure, shoot me at tony at computerant dot com.

---

