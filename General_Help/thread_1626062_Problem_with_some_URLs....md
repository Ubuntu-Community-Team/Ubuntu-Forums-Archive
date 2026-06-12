---
title: "Problem with some URLs..."
date: 2010-11-19
forum: General Help
---

### Post by EloRampage93 on 2010-11-19
When I try to access an url that contains a hyphen (-) as the first character the browser says that it can't find the website. And I know the url is well written... I thinks is an ubuntu general problem because a friend has the same issue.

Why does this happen?

for example: -alexinwonderlandd.tumblr.com

---

### Post by Kulshrax on 2010-11-19
A valid domain name cannot begin with a hyphen. This is explicitly mentioned in the IETF's RFC 1035 on the Domain Name System: [http://tools.ietf.org/html/rfc1035](http://tools.ietf.org/html/rfc1035)

> The labels must follow the rules for ARPANET host names.  They must
start with a letter, end with a letter or digit, and have as interior
characters only letters, digits, and hyphen.  There are also some
restrictions on the length.  Labels must be 63 characters or less.

---

### Post by papibe on 2010-11-19
It seems is known bug: [doesnt recognize dash "-" in URL]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/122848") and [unable to access URLs (doesnt recognize dash "-" in URL)]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/121467").

**Although**, according to Internet standards, all host names must start with a letter.

Regards.

---

### Post by EloRampage93 on 2010-11-20
So, because ubuntu is following the rules, I can't access sites with a hyphen... There should be restriction in the websites...

But ain't there someway to remove this restriction from ubuntu?

BTW: Thanks for the answers.

Regards!

---

### Post by dcstar on 2010-11-20
> **papibe said:**
> It seems is known bug: [doesnt recognize dash "-" in URL]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/122848") and [unable to access URLs (doesnt recognize dash "-" in URL)]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/121467").

**Although**, according to Internet standards, all host names must start **and end** with a letter

Exactly, so the "bug" is the **other** browsers which should not be working with illegal URLs, not Firefox.

---

### Post by mc4man on 2010-11-20
> for example: -alexinwonderlandd.tumblr.com
Not a clue as to what 'should' be at that address, but have you tried simply removing the - ?

---

### Post by EloRampage93 on 2010-11-20
Removing the '-' will only take you to another URL that answers to that name.

---

### Post by phill3006 on 2011-01-28
I know exactly what you're talking about.
On my windows machine, I use google chrome.  If I tried to navigate to a site that had an "illegal" url directly, it would say page not found or some such thing.  If you searched for it [the url] using the omnibar, and clicked the link provided in the search results, it would usually take you to the website.

[http://www.chromeboard.com/showthread.php?t=35383](http://www.chromeboard.com/showthread.php?t=35383)
[http://www.google.com/support/forum/p/Chrome/thread?tid=0cdd13a869180943&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=0cdd13a869180943&hl=en)
Allegedly, 'dig' can get you the website.
I'm not sure of the actual legality of this though, or of the actual dig command (-g -n -a -m, etc.) that you would have to use.

The url I'm having problems with has the dash at the end of the hostname, or domain name.  I don't know what it is.  I'm still learning about everything on a pretty basic level.

XXXXX-.tumblr.com/

*bump* I guess?
Sorry for resurrecting a dead thread.  I'm still not very sure of the finer points of forum etiquette.

---

### Post by phill3006 on 2011-01-28
Ok, so I don't really know how to use dig, but it can querey the address, I don't know if it can actually open the webpage.

---

### Post by Neon Lights on 2011-03-03
I'm having this problem as well. Is there anything to do to fix this?
Considering the same versions of google chrome and firefox work with these sites on Windows, but not Ubuntu, is this related to something else?

---

