---
title: "Evolution won't connect to exchange server"
date: 2009-07-24
forum: General Help
---

### Post by zippyties on 2009-07-24
I am trying to get my Microsoft Exchange server email in Evolution.  So far no luck whatsoever.

I've tried using the address for the in-browser "netmail" that the company set up for home use.

I've tried connecting to the server directly through the VPN (server.domain.net) and some variations of this on like inserting https:\\ in front of it.

So far no luck.

What's weird is, I can get my blackberry to connect no-problem.  The blackberry connects using the netmail feature(https:\\netmail.domain.net\exchange).

I know very little about networking.  So please let me know if you see any errors in my approach.

/edit/  I forgot to mention that I checked to see how Outlook 2007 was configured on my windows system.  It is connected to; server.domain.net (please forgive the generic server names I doubt the company would want their names posted in a public place)

Thanks,

---

### Post by t4thfavor on 2009-07-24
Did you set it up to use a plaintext password? Its not secure, but I have found it doesn't work without it.

I take that back, I just set my password up as a secure password, and it still works. 

Maybe post your config, without the secure bits, and I will verify it against mine. Which has been working for almost a year now.

---

### Post by zippyties on 2009-07-24
@t4thfavor Thanks for the advice.  I have been using the Evolution wizard.  It doesn't appear to give an option for this.  How do I set up the option you mentioned?

---

### Post by zippyties on 2009-07-24
I found a tut for setting up Thunderbird to use Exchange.  From this tut I learned how to extract your Incoming and outgoing server names.

my incoming seems to be ABC.domain.net
and my outgoing is server.domain.net

It didn't work for thunderbird though,

(my company has a website complete with domain eg. [www.mycompany.net](www.mycompany.net), and all of the email and the like uses the same domain.  It just connects to different servers connected to the domain)

I have been using the wizard to try to set up the account, and it just isn't able to validate the OWA.

/edit/ I am willing to bet that I am just missing some trivial bit of syntax which is gumming up the whole thing.  After all the Blackberry manages to make it.

---

### Post by t4thfavor on 2009-07-24
After your done with the Wizard, select Edit->Preferences, and verify all is well. you should have a username without the @domain.net behind it, and an [https://youcompany.net/exchange](https://youcompany.net/exchange) in the OWA url.

---

