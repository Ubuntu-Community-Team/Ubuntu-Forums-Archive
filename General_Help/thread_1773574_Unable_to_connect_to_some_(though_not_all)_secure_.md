---
title: "Unable to connect to some (though not all) secure sites"
date: 2011-06-02
forum: General Help
---

### Post by anubeon on 2011-06-02
[B]Greetings All!

[/B]As of approximately 1 month ago I have been unable to access a selection of secure websites (see below) or connect to my University VPN. I have attempted to access these websites (from my Ubuntu partition) using the latest versions of both Firefox 4 and Chromium 11, but both browsers give a 'connection refused' error almost immediately. There doesn't appear to be any substantive period of negotiation by either Firefox 4, Chromium 11 or Network Manager (where VPN is concerned).

I know with some certainty that this isn't a firewall and/or network issue, as I have been receiving the same error messages (under Ubuntu) at home, at my home University and at my host University in Italy. I have also been able to access these secure websites (see below) and connect to my University VPN from my Windows 7 partition from all of these locations.

So it seems that this is an issue with my Ubuntu partition. I am at a loss as to what, if any, configuration changes I might have made a month ago that could have resulted in this issue. Especially considering that it seems to only effect a handful of secure websites (and by no means all of them).

Here are the sites that are affected by this issue:

[http://www.bbk.ac.uk/mybirkbeckprofile](http://www.bbk.ac.uk/mybirkbeckprofile)
[http://www.bbk.ac.uk/its/password](http://www.bbk.ac.uk/its/password)
[https://www.securesuite.co.uk/](https://www.securesuite.co.uk/)
[https://www.nectar.com/]("https://www.nectar.com/account/viewCurrPointsUpdate.nectar")

*The [https://www.securesuite.co.uk/](https://www.securesuite.co.uk/) is particularly annoying as it means that Halifax Secure authentication is inoperable under Ubuntu. In order to buy anything or pay my bills I have to boot into my Windows 7 partition.

I'm running the latest version of Firefox 4.0 and Chromium (from their respective official repositories) under Ubuntu 11.04 (x86-64) sans Unity (i.e. Gnome2 environment).

Any assistance or advice you could provide would be greatly appreciated. Even if it's just a means of obtaining a more detailed error message that 'connection refused'.

[B]Kind Regards,

Lee.

P.S.: [/B]In my haste I submitted a bug report (Launchpad Bug #778985) although this may turn out to be a local configuration issue rather than a bug proper.

---

### Post by anubeon on 2011-07-07
This is still an issue for me, in fact periodically Ubuntu will refuse **any and all** secure connections (including HTTPS and secured IMAP). 

Again, I can't think of anything I could have done to cause this. So... **BUMP!**

---

