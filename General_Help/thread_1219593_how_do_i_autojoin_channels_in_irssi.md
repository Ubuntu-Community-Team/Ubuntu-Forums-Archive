---
title: "how do i autojoin channels in irssi"
date: 2009-07-21
forum: General Help
---

### Post by UnsafeData on 2009-07-21
I have the latest IRSSI.

How do I auto join a server, identify myself to nickserv, and connect to a channel when I start irssi?

I had this set up before but I FORGOT to backup my CONFIG. I know it's easy, I just can't figure out how I did it. This shouldn't take long. :popcorn:

---

### Post by UnsafeData on 2009-07-21
I got it working by following this:
[http://www.wlug.org.nz/IrssiNotes](http://www.wlug.org.nz/IrssiNotes)

Don't forget to **/save**.


EDIT: I'll just paste the instructions here:

Irssi needs to know the addresses for servers on this network, so add some: /SERVER ADD -auto -ircnet Undernet eu.undernet.org 6667

Now set up some channel preferences: /CHANNEL ADD -auto #wlug Undernet

For those channels require password, append the password to the end of command.

    /CHANNEL ADD -auto #wlug Undernet secret

Now make Irssi remember this information beyond closing it: /SAVE

settings are stored in ~/.irssi/config

---

