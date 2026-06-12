---
title: "Can't get Jabber to work with Empathy"
date: 2010-01-17
forum: General Help
---

### Post by intermentals on 2010-01-17
I'm using 9.10 on a laptop as a server - it is not currently connected to a router/clients

I have installed a Jabber server and created a new account online but when I try to connect using Empathy I get a "Network Error" message

I'm presuming I have to point it at my server somehow but I'm completely lost as to how

Any help or ideas would be muchly appreciated thanks

---

### Post by intermentals on 2010-01-17
bump

---

### Post by jamesisin on 2010-01-17
How is your laptop/server connected to the Internet?

How does your other machine (the client machine) connect to the Internet?

In the Empathy New Jabber Account dialog, you will need to go into Advanced and add server.domain information.

---

### Post by intermentals on 2010-01-17
it is currently connected by a home router but when it is in situ it will be connected by a rack mounted cisco router

is the problem because I'm trying to use the laptop as both the client and jabber server?

---

### Post by jamesisin on 2010-01-17
In order to do that you will still need an Internet connection (unless you configure things oddly) so that the client application can go out and then back to the server via the normal routes.

---

### Post by intermentals on 2010-01-17
the reason I want to use jabber is as for internal IM in my office - do you know how to configure this please?

edit - for the purposes of fiddling now the home router is providing an internet connection

---

### Post by jamesisin on 2010-01-17
I suppose I should have said "network connection"; strictly speaking you needn't connect to the Internet.

That being said, your machines will need to be able to communicate with your Jabber server so it will of course be attached to your office network.  You can call out that server in the dialog I mentioned above using either its IP or more preferably (assuming you have a DNS server) a jabber.domain.local address.

Does this help you out some?

---

### Post by intermentals on 2010-01-17
That does help a great deal thank you

I have the bind9 packages installed but I'm having some difficulty configuring them - I'm currently trying to work out how to set the zones in the named.conf.local file, what I need to do in named.conf.default-zones and what to do as regards the db.* files - I'm still putting networking together in my head I don't have a full understanding yet

when I've done all that I'll be able to input those settings into Empathy and I'm sure that will fix it

---

### Post by jamesisin on 2010-01-17
There is a lot of information out there:

[http://www.google.com/search?client=opera&rls=en&q=set+up+jabber+server&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=set+up+jabber+server&sourceid=opera&ie=utf-8&oe=utf-8)

Just glancing down the page I saw several what appear to be promising results.  Even some Ubuntu forum hits.

---

### Post by intermentals on 2010-01-27
thank you very much for the help - I'd actually searched google quite extensively before posing this question though - I just wanted to see if a fresh explanation from a non-static information source cleared things up for me

---

