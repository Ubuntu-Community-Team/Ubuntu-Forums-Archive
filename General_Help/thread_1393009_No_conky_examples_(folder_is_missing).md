---
title: "No conky examples (folder is missing)"
date: 2010-01-28
forum: General Help
---

### Post by CJN on 2010-01-28
/usr/share/doc/conky/ has no examples folder... so I am wondering if I messed up the install (I used sudo apt-get install conky) or if this was removed recently and where to get it from if that is the case.

---

### Post by ankspo71 on 2010-01-28
Hi,
I don't know the answer to the missing folder question, because I'm not using conky, but I can tell you that there is a huge forum thread here giving screenshots and configurations of conky that you can use as examples. My only possible advice to your question is if you can run conky ok, then you shouldn't need a reinstall. You can reinstall conky any time you like though. 
Here's the thread:
[B]Post your .conkyrc files w/ screenshots 
[/B][http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by stinkeye on 2010-01-28
> **CJN said:**
> /usr/share/doc/conky/ has no examples folder... so I am wondering if I messed up the install (I used sudo apt-get install conky) or if this was removed recently and where to get it from if that is the case.
The config that comes with conky is in 
```
/etc/conky/conky.conf
```

In terminal```
conky 
```
will load ~/.conkyrc 
or if you don't have a  .conkyrc  it will load /etc/conky/conky.conf

```
conky -c /path/to/your/conkyconfig 
```
will load the conky config you specify.

You are better off downloading conky-all through synaptic 
because it is a full conky with most compile options enabled.

This is a good guide to setting up conky:
[_**[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]**_]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

