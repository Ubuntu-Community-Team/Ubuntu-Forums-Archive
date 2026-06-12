---
title: "packages.medibuntu.org down?"
date: 2010-04-20
forum: General Help
---

### Post by AnotherMuggle on 2010-04-20
I am trying to run the script 

"sudo /usr/share/doc/libdvdread4/install-css.sh"

to get encrypted DVD playback but it looks like the repository at packages.medibuntu.org is down.  

Are there any official, or at least guaranteed safe, mirrors I can use?

---

### Post by agnes on 2010-04-20
[Link]("http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html")
Don't know about how up-to-date for Lucid those mentioned are, but I bet for DVD playback on 9.10 it would be ok.
Safe... no guarantee but I would assume if they were not, people in the comments in the article would complain... the sites of the repos also look professional.

---

### Post by Velvet Karuda Leopard on 2010-04-20
Ok.  I just tried several methods to get dvd playback, including all the medibuntu stuff I have read, and nothing.

I just now gave up on my fifth attempt at adding the medibuntu repositories.  Every time I try I get timed out or I get a myriad of errors.

I just tried the above link and all three mirrors failed.  They all three still went to packages.medibuntu.org.

Is something wrong with my 9.10?

Can someone help me get my dvd playability back?

---

### Post by coffeecat on 2010-04-20
> **Velvet Karuda Leopard said:**
> I just tried the above link and all three mirrors failed.  They all three still went to packages.medibuntu.org.

Many people are using that link to change the medibuntu mirror. I wouldn't be surprised if they are getting overloaded and the mirror admins are redirecting the traffic back to the main Medibuntu sever.

Last word I heard is that it was hoped that the main Medibuntu package server will be back up tomorrow.

> **Velvet Karuda Leopard said:**
> Is something wrong with my 9.10?

Nothing's wrong except a repository server problem.

---

### Post by AnotherMuggle on 2010-04-21
> **coffeecat said:**
> Many people are using that link to change the medibuntu mirror. I wouldn't be surprised if they are getting overloaded and the mirror admins are redirecting the traffic back to the main Medibuntu sever.

Last word I heard is that it was hoped that the main Medibuntu package server will be back up tomorrow.



Nothing's wrong except a repository server problem.

Thanks for the heads up.  I will try again this evening and resolve this thread if all is well.

---

### Post by Morbius1 on 2010-04-21
Another explanation:

> **Morbius1 said:**
> I read in another forum somewhere that the problem is not that medibuntu.org is down - it's a DNS problem. "packages.medibuntu.org" can't be converted to an ip address. This might explain why it's been going on for so many days now. Medibuntu can't fix it because it's not their problem.

Anyway, to fix it add the following line to your **/etc/hosts** file:

```
88.191.101.8 packages.medibuntu.org
```That's the ip address of the repository so it doesn't have to use DNS to convert it.

---

### Post by coffeecat on 2010-04-21
> **Morbius1 said:**
> Another explanation:

Yes, I can confirm that works. I was able to do a 'sudo apt-get update' without a hiccup with Medibuntu, and install a Medibuntu package using Synaptic.

That 'back by Wednesday' (which came from a Launchpad bug thread) will be optimistic if this is a DNS problem. :(

Interestingly, if you don't do that /etc/hosts edit and do a 'sudo apt-get update', apt-get tries to get the Medibuntu metadata from 88.191.82.11.

---

### Post by Velvet Karuda Leopard on 2010-04-21
> Morbius1  	
Re: packages.medibuntu.org down?
Another explanation:

Quote:
Originally Posted by Morbius1 View Post
I read in another forum somewhere that the problem is not that medibuntu.org is down - it's a DNS problem. "packages.medibuntu.org" can't be converted to an ip address. This might explain why it's been going on for so many days now. Medibuntu can't fix it because it's not their problem.

Anyway, to fix it add the following line to your /etc/hosts file:

Code:

88.191.101.8 packages.medibuntu.org

That's the ip address of the repository so it doesn't have to use DNS to convert it.

I have just now gotten online and tried this.  Worked the very first time.  My Apt-get is still giving me three warnings I would like to fix, but I think that will go into another post when I get back in.  Now I can watch my collection of over 1,000 legally obtained DVDs on my PC.

Off the subject, I have always wondered why Linux was not allowed to play my DVDs.  I own no DVD player and only use my PC for media.  I couldn't watch my movies for the longest and they are paid for.  Is there some kind of strange capitalist law in place or something?

---

### Post by Morbius1 on 2010-04-21
In case anyone is interested it appears that although my recommendation works it was not for the reason I mentioned. It has nothing to do with DNS.

If you were to do a Vulcan Mind Meld with the internet itself you would have easily found this notice: [http://feeds.launchpad.net/medibuntu/announcements.atom](http://feeds.launchpad.net/medibuntu/announcements.atom)
> Medibuntu Announcements
Main server down
04/21/2010 04:50 AM

The main front-end providing <http://packages.medibuntu.org> is currently down. It might be brought back online in the next hours/days.

In the meantime, you can still access Medibuntu packages by using one of the workarounds explained in the bug report: <https://bugs.launchpad.net/medibuntu/+bug/565810/comments/6> and <https://bugs.launchpad.net/medibuntu/+bug/565810/comments/12>.
So either switching to the mirrors in sources.list or using 88.191.101.8 in /etc/hosts will work and are apparently sanctioned workarounds.

---

### Post by AnotherMuggle on 2010-04-21
Brilliant stuff.
DVD playback working without a hitch.
Thanks to all :D

---

### Post by Morbius1 on 2010-04-22
FYI, It appears as though the medibuntu server is back up:

> Main server back online
04/21/2010 03:23 PM

The server hosting the main archive has been restarted a few minutes ago (apparently, the culprit was the network driver that had crashed). Everything should be back to normal in a few hours, when all mirrors are in sync.

Sorry for the inconvenience, and thanks for your patience.
I commented out the line in /etc/hosts and reloaded synaptic without incident,

---

