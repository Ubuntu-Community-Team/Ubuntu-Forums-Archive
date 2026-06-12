---
title: "Firefox, Flashgot and JDownloader"
date: 2010-10-23
forum: General Help
---

### Post by nrabett on 2010-10-23
Hi,
like many other users, I am experiencing a small problem when using the Firefox extension Flashgot with the Java download manager JDownloader. Flashgot does not seem to be able to launch JDownloader automatically. I have already posted this in a thred on another forum, withouth results. I suspect that security issues are the reason why JDownloader cannot start. 

See this thread:

[http://forums.informaction.com/viewtopic.php?f=6&t=3262]("http://forums.informaction.com/viewtopic.php?f=6&t=3262")


Suggestions?

---

### Post by CharlesA on 2010-10-23
Not a security question.

*Thread moved to **General Help**.*

We'd need more info to help you.

---

### Post by nrabett on 2010-10-23
Basically, the Flashgot log (as quoted in the last post in the linked thread) shows that Flashgot (Firefox) attemts to launch JDownloader through Java. 

When using the terminal, I am able to launch JDownloader by writing 

/usr/lib/jvm/java-6-sun-1.6.0.22/jre/bin/java -Xmx512m -jar  /home/morten/.jdownloader/JDownloader.jar -- async

... this is the command that is displayed in the Flasgot log, but Flasgot is apparently not able to launch JDownloader unsing this commant.

---

### Post by recauchutado on 2010-11-27
I had the same problem trying to make jdownloader work with flashgot.

After checking the file flashgot.js in the folder ".mozilla" I realized that this app was connecting through localhost as:

**pref("flashgot.dmsopts.JDownloader.url", "http://127.0.0.1:9666/flashgot");**

My mozilla is configured through proxy and I use the system proxy configuration in ubuntu and for mozilla. I checked manual proxy configuration on mozilla and there you see how localhost is configured without the proxy.

That was my problem. Localhost with no proxy was my solution.
Probably no proxy is working for most of the people with the same problem.

Hope is useful

---

### Post by nrabett on 2011-01-10
recauchutado, 

did this change make JD start by itself when you sent links from FlashGot, or do you mean that you solved the problem of sending links to JD by changing the settings? 

To me, it seems like you mean the latter. Are you also able to open JD automatically when adding links with FlashGot?

---

### Post by nrabett on 2011-01-10
Double post.

---

### Post by nrabett on 2011-04-19
Hi, did a fresh install of Ubuntu 10.10 and JD today. It turns out that the solution is (and probably has always been) very simple: You don't only need Sun Java, but you also have to ensure that Firefox uses the Sun Java plugin. 

By default, Firefox does not use it, and refuses to do  so even after I installed Sun Java. 

There are several guides for this - basically, it requires a symlink from the FF plugins directory to the libnpjp2.so file in the Sun Java folder. There is a nice guide on the Sun Java homepage - search for Firefox Linux.

On Ubuntu 10.10, the symlink goes from 

/usr/lib/firefox-addons/plugins/libnpjp2.so 

 to 

/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 

This enables the Sun Java plugin for all users.

---

