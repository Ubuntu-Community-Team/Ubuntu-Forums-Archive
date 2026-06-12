---
title: "No Internet"
date: 2010-07-31
forum: General Help
---

### Post by silaflex on 2010-07-31
Hi,
I have just installed 10.04 on Acer laptop 5630.

I can not get my internet going when I connect to my Dlink DSL 502T.

The network indicator changes from little arches to up and down arrows when I plug the router in which leads me to believe I have a connection.

I can ping addresses ok.

But when I open firefox i just get "connection has timed out"

I have tried changing various network settings but nothing seems to work.

Can anyone help?

---

### Post by lovinglinux on 2010-07-31
Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

---

### Post by silaflex on 2010-07-31
That's huge.

Thanks so much.

Whats the problem with ipv6?

---

### Post by lovinglinux on 2010-07-31
> **silaflex said:**
> That's huge.

Thanks so much.

Whats the problem with ipv6?

I guess it mess things up if you don't have ipv6 support on your network.

---

