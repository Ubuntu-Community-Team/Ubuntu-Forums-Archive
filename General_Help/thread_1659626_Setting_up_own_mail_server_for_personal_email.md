---
title: "Setting up own mail server for personal email"
date: 2011-01-04
forum: General Help
---

### Post by VorpalBunny on 2011-01-04
Hi there!

I would like to be able to have email sent directly to my computer at home (i.e. run some kind of mail server on it) instead of having to rely on Gmail, Yahoo or someone else. From what I've read it should be possible, but most of the guides out there seem to be oriented to enterprise-class setups, or at the very least a small business, and I think that a lot of that would be overkill for just getting my personal mail. The minimum *I think* is 

- register a domain name, with the DNS pointing to my public IP (which is dynamic, so one question I have is whether I would have to use DynDNS or is DNS at any registrar going to be flexible enough to modify if/when my IP changes?)

- something about MX records (I'm really unsure here, what exactly are these and where do I set them up? I don't think a free DynDNS account lets one handle this, does someone know which of their account types supports setting this up?)

- Install sendmail and postfix (which seems like a PITA, but much documentation appears to be available)

- Profit?

Is that everything I need to do, or have I overlooked something? Also, any general advice or tips or comments on whether this is a good/bad idea would be welcome. 

Thanks!

---

### Post by sptrsn on 2011-01-04
Email generally wont work with a dynamic ip. most ISP's will flag it as spam. You'll spend more time jerking around with it that it's worth. especially with free gmail 3 minutes away.

I keep trying, thinking it's going to be better, but, it's just so much harder than you think it's going to be.

If I were to try it again, I would take an unused machine and follow this recipe...
[http://nanotux.com/blog/the-ultimate-server/](http://nanotux.com/blog/the-ultimate-server/)

Just follow it closely and you'll have a great web and mail server at the end. I used that build for my webserver and it is rock solid. 

My ISP blocks port 80, so I use an alternate port and only use it for my personal CRM. I also use it for web development work until it's ready to move into production.

I can't truly vouch for the mail server portion of the build, since I don't use it for email, but if it's anything like the web services portion, it should be good.

---

### Post by VorpalBunny on 2011-01-04
Well, I don't *think* my ISP blocks any ports, but I haven't tried using port 80 with this ISP yet. 

The hassle of setting everything up vs. Gmail in 10 seconds is the main reason I've not attempted this before, but lately I've just got fed up with everything we do going through some mega corporation that has no qualms about (indeed, builds their business model around) mining data for advertisement purposes and selling personal information to the highest bidder. 

Meh, maybe I'm too paranoid :confused:

Anyway, thanks for the link, it looks like it will be helpful.

---

