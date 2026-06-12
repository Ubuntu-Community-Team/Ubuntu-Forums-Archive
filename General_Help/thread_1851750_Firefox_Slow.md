---
title: "Firefox Slow"
date: 2011-09-28
forum: General Help
---

### Post by mao3 on 2011-09-28
Hey,  I wasn't sure where to post this, I thought wireless and networking, so if you guys think that this question is better suited there, let me know.  I'm using Ubuntu 11.04 and Firefox 6.0.2, and it's being really slow.  It is not this slow on Windows, so I know my connection is not the problem.  I tried making the changes described here [http://tinyurl.com/36xozsh](http://tinyurl.com/36xozsh) but it only made it a little bit better. 

Occasionally I will get an unable to connect to server , and there's no specific website where this occurs.  I'm a little worried there's something wrong, but mostly I just find this annoying because it was not this slow before and I did not make any changes before the slowdown aside from installing the noscript add-on, and it was a while after doing that before it started happening.  Any help would be greatly appreciated.

Also, I have 6 gigs of ram, so that's probably not the problem.

---

### Post by daniele80 on 2011-12-31
I have the same problem

---

### Post by tlu on 2011-12-31
You might have problematic extensions. Open a console, execute

firefox --safe-mode

and disable all addons.

If that doesn't help, there might be another problem with your profile. Open a console, execute

firefox -p

and create a new profile. Check if this improves the situation. You can then selectively copy your data from your old profile to the new one - see [http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

### Post by 2F4U on 2011-12-31
It may help to disable IPv6, if you haven't done so already.

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

I would start by trying Method 2 in the article and doing it just in Firefox. This is often sufficient.

---

### Post by murataht on 2012-01-12
Thanks, that did the work.

---

