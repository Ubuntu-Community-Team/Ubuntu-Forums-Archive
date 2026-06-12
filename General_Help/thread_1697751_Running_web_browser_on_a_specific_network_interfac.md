---
title: "Running web browser on a specific network interface"
date: 2011-03-01
forum: General Help
---

### Post by pawelch on 2011-03-01
Dear users,

Its my first post thus let me say big welcome to everyone first.
The title corresponds to a problem I am facing right now. Suppose, that I have a machine with multiple network interfaces,say eth0,eth1,...ethn. What I want to achieve is to be able to specify which interface is used given my preferences. For example, if I want to run an application (in this case web-browser) via interface 5 I type in, say:

```
lynx eth5 nw_add
```Of course it does not work at the moment but maybe it is possible to be run with extra help of some scripts or something. Do you know any way I can specify network interface for applications?

It is possible for some applications:

```
ping -I eth1 host
```or
```
wget --bind-address=nw_add
```However, I have to use it for different applications (explicitly for these where a TCP connection is established and user perform additional operations rather than wgetting only.)
I need it for my research purpose thus it might pose as a strange question.

Thank you anyone for any suggestion and help.

Cheers!

p.s. I have done some searching before and even started a similar thread at **[LQ]("http://www.linuxquestions.org/questions/linux-newbie-8/%5Blinux-any%5D-running-web-browser-on-a-specific-network-interface-865129/")** but it remained silent for a while and It think it is dead now.

---

