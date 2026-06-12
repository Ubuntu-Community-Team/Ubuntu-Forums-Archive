---
title: "Can I use an Outlook Anywhere account for Exchange 2010 in Ubuntu?"
date: 2011-11-15
forum: General Help
---

### Post by ingramproductions on 2011-11-15
Everything I've researched says NO, but I thought I'd give it one last try.

Evolution has the option to use a Microsoft Exchange account through OWA, but it apparently only works with Exchange 2000/2003. I get the following error message:
"The Exchange Server is not compatible with Exchange Connector. The server is running Exchange 5.5. Exchange Connector supports Microsoft Exchange 2000 and 2003 only."

There is an old plugin/server called [Brutus]("http://linux.softpedia.com/get/Communications/Email/Brutus-evolution-brutus-20729.shtml"), but it requires that you have a server setup to work with Exchange, so I can't do that.

Is there a way to use an Outlook Anywhere account in Linux/Ubuntu at all, or am I just out of luck?

---

### Post by jjbasken on 2011-11-15
I don't know if you are already aware of this or if your Outlook Anywhere isn't setup for it but I am able to access Outlook Anywhere using a browser and find that to be very useful. 

It works well with Firefox and works with Chromium also but I am only able to use it in light mode on Chromium.

---

### Post by ingramproductions on 2011-11-15
Yea,I can do that, but I'd rather use a mail client like Evolution or Thunderbird, as they are more feature rich and integrated into the desktop

---

### Post by collisionystm on 2011-11-15
Well.
You could cheat the system.
Setup a gmail account. Have it auto fetch POP email from your exchange account. You can set it up to download all email. It will retrieve it to your gmail account which you can then sync in thunderbird. You can also send emails from your exchange address.

---

### Post by ingramproductions on 2011-11-15
> **collisionystm said:**
> Well.
You could cheat the system.
Setup a gmail account. Have it auto fetch POP email from your exchange account. You can set it up to download all email. It will retrieve it to your gmail account which you can then sync in thunderbird. You can also send emails from your exchange address.

If I were going to go through all that trouble, I would just set up a pop account to my Exchange server directly, which would have the same results as what you described (Thunderbird would sync with gmail through pop anyways).

I'm strictly trying to find out if it's possible to setup an Outlook Anywhere account through an email client on Ubuntu?

---

### Post by HermanAB on 2011-11-16
Short answer: No.

I'd be happy if you would write an Exchange to IMAP adaptor for us!

---

