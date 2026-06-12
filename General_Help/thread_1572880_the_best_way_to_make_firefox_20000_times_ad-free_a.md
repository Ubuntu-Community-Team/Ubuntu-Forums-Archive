---
title: "the best way to make firefox 20000 times ad-free and fast"
date: 2010-09-11
forum: General Help
---

### Post by f6e9a on 2010-09-11
i will help u make 2 things fast ur download speed and ur normal browsing speed.

for network speed connections


[LIST]
[*]Type **about:config** in Firefox address bar to open the  advanced preferences
[*]Type **network.http.max** in the filter field and hit enter
[*]Right-click on **network.http.max-connections** and change the  value to **48**
[*]Right-click on **network.http.max-connections-per-server**  and set the value to **24**
[*]Right-click on **network.http.max-persistent-connections-per-server**  and set the value to **12**
[/LIST]
for pipelining 

[LIST]
[*]Type **pipelining** in the filter field and hit enter
[*]Double click **network.http.pipelining** in order to set it as **true**
[*]Double click **network.http.pipelining.firstrequest** in order to  set it as **true**
[*]Right-click on **network.http.pipelining.maxrequests** and change  the value to **8**
[*]Double click **network.http.pipelining.ssl** in order to set it  as **true**
[*]Double click **network.http.proxy.pipelining** in order to set it  as **true**
[/LIST]
 and to stop firefox from loading for a long time

[LIST]
[*]Type **network.dns.disableIPv6 **in the filter field and hit  enter
[*]Double click **network.dns.disableIPv6 **in the results in order  to set it as **true**
[/LIST]




now to make firefox ad- free install this addon
[http://addons.mozilla.org/en-US/firefox/addon/1865/](http://addons.mozilla.org/en-US/firefox/addon/1865/)

---

### Post by kerry_s on 2010-09-11
those been around forever.

network.http.pipelining.maxrequests user set integer 200
network.http.max.persistant-connections-per-server user srt integer 200

200 hundred is to high, your going to get yourself blocked for flooding the server, you can actually be making it slower cause your flooding your own connection to, 8 & 10 is good enough.

you also forgot to disable ipv6 in there.

network.dns.disableIPv6 true

---

### Post by lovinglinux on 2010-09-12
> **kerry_s said:**
> 200 hundred is to high, your going to get yourself blocked for flooding the server, you can actually be making it slower cause your flooding your own connection to, 10 is good enough.

I agree. Before changing Firefox advanced configurations and recommending to others, check the maximum values allowed and the caveats at [http://kb.mozillazine.org](http://kb.mozillazine.org)

For instance, you cannot set *network.http.pipelining.maxrequests* to anything above 8.

[http://kb.mozillazine.org/Network.http.pipelining.maxrequests](http://kb.mozillazine.org/Network.http.pipelining.maxrequests)

Please correct your post. Also check [my tweaks]("http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html") if you don't want to research the subject.

---

### Post by kerry_s on 2010-09-12
i didn't know they hard coded it to 8 now, been along while since i used firefox, only just starting to use it again.

corrected it in my previous post to 8 & 10.

---

### Post by lovinglinux on 2010-09-12
> **kerry_s said:**
> i didn't know they hard coded it to 8 now, been along while since i used firefox, only just starting to use it again.

corrected it in my previous post to 8 & 10.

Most of my post was directed to the OP, but I forgot to quote him :) Sorry.

There are tons of Firefox tutorials on the web with wrong values.

---

### Post by kerry_s on 2010-09-12
> **lovinglinux said:**
> Most of my post was directed to the OP, but I forgot to quote him :) Sorry.

There are tons of Firefox tutorials on the web with wrong values.

i figured that, i did look over your tweaks.
i don't do the cache, history, memory & count tweaks. i always thought firefox handled those fine.

---

### Post by f6e9a on 2010-09-12
fixed it

---

### Post by lovinglinux on 2010-09-12
> **f6e9a said:**
> fixed it

Thanks.

---

