---
title: "Distrowatch forbidden 403"
date: 2011-11-07
forum: General Help
---

### Post by Luxx on 2011-11-07
I have an unresolved issue with getting an error message ONLY on one computer in my home's network when trying to access Distrowatch.com/. It only happens on the Ubuntu computer, using Firefox. The others are Windows - IE and Firefox bring up the website fine on those. 

The error is:
Forbidden
You don't have permission to access / on this server.

I get different results on my Ubuntu computer using different settings for my User Agent Switcher, but I still can't get the website to come up. Using a proxy I get an error that the website is unaccessible. I either get the error or it simply keeps loading and times out with a Firefox message stating it took long to respond.
After looking around I have found others having the same problem and getting replies stating the site seems to be working fine.

Is there possibly a certain user agent the Distrowatch server is looking for?

Thanks.

---

### Post by davdo2004 on 2011-11-07
I think the site maybe down. I can't get it to load and checking with [http://www.downforeveryoneorjustme.com](http://www.downforeveryoneorjustme.com)  I get  "It's not just you!  [http://www.distrowatch.com]("http://www.distrowatch.com/") looks down from here."

---

### Post by Rodney9 on 2011-11-07
[http://www.distrowatch.com/](http://www.distrowatch.com/)  works fine for me.

Rodney

---

### Post by coffeecat on 2011-11-07
About an hour after the previous posts, I'm getting "Server not found" for distrowatch.com with Firefox.

---

### Post by Luxx on 2011-11-18
I was able to get to the website from another computer (Windows) in the same house, on the same network while I wasn't able to get to it from my Ubuntu comp, so I know the site wasn't actually down,but the test pages suggested it was from my Ubuntu comp, which I thought was odd.

I couldn't believe what the problem was. Distrowatch collects useragent info from browsers to determine the OS/browser users are viewing their website in. From what I understand this is for statistical OS information, how many users are using which versions of Linux,or something like that.

Apparently they are picky about certain words that might be in that useragent information.

I had changed a string in Firefox - about:config, general.useragent.extra.firefox - and the random string I put in contained a naughty word. I had made the change to stop Google Instant from forcing mispelled searches on me when I tried to correct the spelling of a search. Google Instant Search was reverting my correction back to the original incorrect spelling EVERY time I tried to correct it and wouldn't let me search for what I was actually looking for.

I only changed the naughty word and suddenly Distrowatch came up as soon as I restarted the browser. That was the only change I made.

---

