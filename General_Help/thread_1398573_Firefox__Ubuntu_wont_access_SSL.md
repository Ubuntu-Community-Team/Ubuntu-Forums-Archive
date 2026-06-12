---
title: "Firefox / Ubuntu wont access SSL"
date: 2010-02-04
forum: General Help
---

### Post by cheadle on 2010-02-04
Hiya,

I have a problem that I have noticed for a while, however thought it was more to do with the internet at first than my setup. I have now though come to work out that it is something to do with Ubuntu / Firefox setup.

I am running 9.10 and when I go to visit a site on the internet that requires SSL access, it just wont connect and times out. Now ive checked to see if firewall was the issue - however when I looked it said that the default one wasnt enabled and im not aware of anything else running on the system.

So  I am now at a loss of what to try next. Im hoping someone here will know the solution to all my problems! :smile:

---

### Post by lovinglinux on 2010-02-05
Can you access the address below (it's a Google server)?

[https://74.125.45.104:443/accounts/](https://74.125.45.104:443/accounts/)

If yes, then try this:

[LIST]
[*]Type **about:config** in the address bar, press Enter.
[*]Find ***network.dns.disableIPv6*** and set it to true
[/LIST]

If not, then try this:

[LIST]
[*]Type **about:config** in the address bar, press Enter.
[*]Find ***network.dns.disableIPv6*** and set it to true
[*]Find ***network.http.pipelining*** and set it to true
[*]Find ***network.http.pipelining.ssl*** and set it to true
[*]Find ***network.http.pipelining.maxrequests*** and set it to 8
[*]Open Firefox preferences, go to the Security tab, then disable "Block reported attack sites" and "Block reported web forgeries".
[/LIST]

See if that solves the problem.

---

### Post by cheadle on 2010-03-04
No,

I have tired those suggestions however they havent made any difference.

Any other ideas?

---

### Post by e633 on 2010-03-04
Remember to re-enable "Block reported attack  sites" and "Block reported web forgeries" when you're finished.
How do you connect? Router? USB modem?
Have you ever tinkered with about:config before?
Can you try https with other browsers and\or systems from that same PC?
Are you using a proxy? Also please check 
```

network.proxy.ssl;
network.proxy.ssl_port;0
security.enable_ssl2;false
security.enable_ssl3;true

```

---

### Post by cheadle on 2010-03-14
No i've not changed anything in the about:config before.

However we do use a proxy server, so should that be in the code that you have posted above?

SSL works on other machines on the network - however these are on that nasty operating system. :p It seems like its the ubuntu machine that doesnt want to access SSL as no browser will access SSL on the box. :(

---

