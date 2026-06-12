---
title: "Help with GIVER"
date: 2010-01-19
forum: General Help
---

### Post by earthtoclinton on 2010-01-19
Hi there,

I have searched around about this but have had no luck - I have two laptops both running Mint 8, and I would like to use Giver to send files from one to the other. When I bring up Giver on each laptop, it only sees itself, not the other computer. Both computers are connected to the same router for internet access. How do I go about setting the network up? I don't need any advanced network stuff - I simply would like to use Giver. Any help would be much appreciated.

---

### Post by sliketymo on 2010-01-19
[http://forums.linuxmint.com/viewtopic.php?f=47&t=29489](http://forums.linuxmint.com/viewtopic.php?f=47&t=29489)

---

### Post by earthtoclinton on 2010-01-20
Thanks a lot for that, unfortunately though it didn't really help me. Anyone else have an idea?

---

### Post by 3rdalbum on 2010-01-20
Have you maybe turned off Avahi/Bonjour/ZeroConf? This is needed on both machines in order for Giver to work. It's present on a default Ubuntu install unless you actually stop it running.

Also, turn off any personal firewalls. And don't turn them back on - you're already behind a router.

Try pinging the other computer and see if you get a response through ping.

And finally, Giver isn't the most perfect piece of code. Try setting up a simple Samba share.

EDIT: A little bit off-topic, but if you have a website or social networking profile you should check out [www.internetblackout.com.au](www.internetblackout.com.au) - it's a protest against the Australian government's internet censorship plan. The protest is being organised by Jeff Waugh, who used to work on Ubuntu and still works on Gnome.

---

