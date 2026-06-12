---
title: "Firefox security"
date: 2012-03-07
forum: General Help
---

### Post by finite9 on 2012-03-07
Sorry, this post is not Ubuntu specific.  I hope someone has some suggestions though...

I started looking into browser security again, and looked at NoScript, AdBlocker Plus etc, and I saw the Collusion demo which I've been using to verify that the add-ons are working.

Then I came across the mvps hosts file solution: hosts file re-directs dodgy sites to my local 127.0.0.1 address.

I have a general question about these solutions:

When I have this hosts file in place (verified that traceroute does indeed point to my local IP), web browsing with Firefox _still_ shows in the status bar that it is trying to load sites like doubleclick.net, and sites still load slowly, as they try to load the page.

When I enable NoScript, I no longer see that Firefox is even trying to load those domains, and the pages load substantially faster.

Is using the hosts file "slow" compared to using NoScript, or is it just that NoScript disables a ton of other stuff that a hosts file does not catch?

---

### Post by Gremlinzzz on 2012-03-07
NoScript is a free and open-source extension for Mozilla Firefox, SeaMonkey, and other Mozilla-based web browsers, created and actively maintained by Giorgio Maone,[1] an Italian software developer and member of the Mozilla Security Group.[2] NoScript allows executable web content such as JavaScript, Java, Flash, Silverlight, and other plugins only if the site hosting it is considered trusted by its user and has been previously added to a whitelist. NoScript also offers specific countermeasures against security exploits:popcorn:

more info
[https://en.wikipedia.org/wiki/NoScript](https://en.wikipedia.org/wiki/NoScript)

---

### Post by finite9 on 2012-03-07
> **Gremlinzzz said:**
> NoScript is a free and open-source extension for Mozilla Firefox, SeaMonkey, and other Mozilla-based web browsers, created and actively maintained by Giorgio Maone,[1] an Italian software developer and member of the Mozilla Security Group.[2] NoScript allows executable web content such as JavaScript, Java, Flash, Silverlight, and other plugins only if the site hosting it is considered trusted by its user and has been previously added to a whitelist. NoScript also offers specific countermeasures against security exploits:popcorn:

more info
[https://en.wikipedia.org/wiki/NoScript](https://en.wikipedia.org/wiki/NoScript)

I honestly don't know why you responded with info from the Wiki.  It doesn't answer any of my questions.

---

### Post by Dangertux on 2012-03-07
> **finite9 said:**
> Sorry, this post is not Ubuntu specific.  I hope someone has some suggestions though...

I started looking into browser security again, and looked at NoScript, AdBlocker Plus etc, and I saw the Collusion demo which I've been using to verify that the add-ons are working.

Then I came across the mvps hosts file solution: hosts file re-directs dodgy sites to my local 127.0.0.1 address.

I have a general question about these solutions:

When I have this hosts file in place (verified that traceroute does indeed point to my local IP), web browsing with Firefox _still_ shows in the status bar that it is trying to load sites like doubleclick.net, and sites still load slowly, as they try to load the page.

When I enable NoScript, I no longer see that Firefox is even trying to load those domains, and the pages load substantially faster.

Is using the hosts file "slow" compared to using NoScript, or is it just that NoScript disables a ton of other stuff that a hosts file does not catch?

To answer these questions direectly, NoScript will not load scripts, which often pull content from other sites. So if a script is pointing to doubleclick.net or whatever and the script is never loaded. The request to that site is never made, so the content is not loaded.

The hosts file targets a different aspect, it basically blocks the content by making the hostname doubleclick.net resolve to localhost. Your browser still loads the script and still tries to load the content, has to wait for doubleclick.net (localhost) to timeout, then continue. So it can slow down performance considerably.

Hopefully this answers your question.

---

