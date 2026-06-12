---
title: "How do I limit/control bash completion of hostnames?"
date: 2010-01-17
forum: General Help
---

### Post by deconstrained on 2010-01-17
Greetings, 

I really love the way that the default configuration of bash in Ubuntu includes automatic tab-completion of host names, which makes ssh, scp and rsync across a LAN/VPN way easier. However, having recently added the contents of the legendary "[hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt)" to my /etc/hosts file in order to block advertisements, I find my completions cluttered with useless host names from that list.

I take it this means that bash tab completion is configured to include host entries in /etc/hosts. But what if I just want hosts from my ~/.etc/known_hosts to be included in the possible completions? How would I go about configuring bash completion so that it would ignore /etc/hosts? 

Also, might there be a way to point host name tab completion to a text file containing host names that I want included in the pool of possible completions?

Thank you very much for your time.

---

### Post by bodhi.zazen on 2010-01-17
See these two :

[http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1](http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1)

[http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_2](http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_2)

An alternate solution is to use Privoxy rather then a hosts file. I have recently started using privoxy and it does a very decent job of adblocking, so much so that I have given up on both a hosts.txt and adblock plus.

---

