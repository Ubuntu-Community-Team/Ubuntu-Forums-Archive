---
title: "Apache2 localhost not available when no internet connection"
date: 2010-06-12
forum: General Help
---

### Post by buddhika75 on 2010-06-12
Dear All,

I am a new comer to Ubuntu, but during the last few months, I have enjoyed it very much.

I am running the version 10.4. As I am learning mySQL and PHP, I installed Apache2, mySQL and PHP, as discribed in this [link]("https://help.ubuntu.com/community/ApacheMySQLPHP").

The problem is I have to have any sort of Network, either LAN, WiFi or Mobile Broadband to access my localhost. When I am connected to internet, my local host works fine, without any problem, but ***[COLOR="DarkRed"]as soon as I get disconnected from internet, localhost is not available[/COLOR]***.

I have googled a lot, but could not find a solution.

A help will be greatly appreciated.

Thanks in advance

---

### Post by eggdeng on 2010-06-12
Have you checked this?
[http://www.ghacks.net/2009/04/20/linux-solutions-why-does-firefox-start-in-offline-mode/](http://www.ghacks.net/2009/04/20/linux-solutions-why-does-firefox-start-in-offline-mode/)

---

### Post by buddhika75 on 2010-06-12
Dear eggdeng,

Thank you very much for the answer. I followed that and now I can access localhost even when I am not connected to internet through firepox. It solved the problem, but I will be glad if anyone can resolve the actual issue as it still do not work with google chrome, and I have addicted to chrome.

---

### Post by dcstar on 2010-06-12
> **buddhika75 said:**
> Dear All,

I am a new comer to Ubuntu, but during the last few months, I have enjoyed it very much.

I am running the version 10.4. As I am learning mySQL and PHP, I installed Apache2, mySQL and PHP, as discribed in this [link]("https://help.ubuntu.com/community/ApacheMySQLPHP").

The problem is I have to have any sort of Network, either LAN, WiFi or Mobile Broadband to access my localhost. When I am connected to internet, my local host works fine, without any problem, but ***[COLOR="DarkRed"]as soon as I get disconnected from internet, localhost is not available[/COLOR]***.

I have googled a lot, but could not find a solution.

A help will be greatly appreciated.

Thanks in advance

Manually add the loopback entries to the /etc/network/interfaces file:

```
auto lo
iface lo inet loopback
```
and /etc/hosts should contain:
```
127.0.0.1	localhost
```

---

### Post by buddhika75 on 2010-06-12
Dear Devid,

My /etc/network/interfaces file already had those lines.

My /etc/hosts files contain these lines

[COLOR="Navy"][I]127.0.0.1	localhost
127.0.1.1	buddhika-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/I][/COLOR]

buddhika-laptop is my computer name. So I had nothing to change, I suppose.

Thank you,

Hoping a favorable replay,

Buddhika

---

### Post by dcstar on 2010-06-12
> **buddhika75 said:**
> Dear Devid,

My /etc/network/interfaces file already had those lines.

My /etc/hosts files contain these lines

[COLOR="Navy"][I]127.0.0.1	localhost
127.0.1.1	buddhika-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/I][/COLOR]

buddhika-laptop is my computer name. So I had nothing to change, I suppose.

Thank you,

Hoping a favorable replay,

Buddhika

If you can ping localhost when there is no connection then it should work.

Try setting a Static IP address.

---

