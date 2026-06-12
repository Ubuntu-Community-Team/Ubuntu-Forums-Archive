---
title: "Getting the latest Firefox security updates in Hardy"
date: 2009-10-30
forum: General Help
---

### Post by oldjack on 2009-10-30
I'm using Hardy Heron 8.04 LTS and I don't see *anything* in Synaptic to patch Firefox from my 3.0.14. What am I missing? No new version of Firefox, no "shir" anything. 

I am newbie to Linux and Ubuntu, but I do think it's a great thing if some of these security kinks can be worked out. 

Oh, and BTW, anyone running 3.0.14 should feel unnerved. I'm running Opera until I can patch Firefox properly. At least it's upgraded.

THX!

---

### Post by aysiu on 2009-10-30
> **oldjack said:**
> I'm using Hardy Heron 8.04 LTS and I don't see *anything* in Synaptic to patch Firefox from my 3.0.14. What am I missing? No new version of Firefox, no "shir" anything. 

I am newbie to Linux and Ubuntu, but I do think it's a great thing if some of these security kinks can be worked out. 

Oh, and BTW, anyone running 3.0.14 should feel unnerved. I'm running Opera until I can patch Firefox properly. At least it's upgraded.

THX!
*firefox-3.5* is not available for Hardy.

More details here:
[http://packages.ubuntu.com/search?keywords=firefox-3.5&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=firefox-3.5&searchon=names&suite=all&section=all)

If you want to upgrade, follow these instructions:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by oldjack on 2009-10-30
Thanks, aysiu.

Can anyone explain or point to an explanation of why this is? I suppose I'm not the 1st to ask but I don't see the reason yet.

I understand that Hardy Heron is the current "Long Term Support" version and Firefox was a part of that distribution. What this means exactly, as I understood it, was that security patches would be delivered, if nothing else. Perhaps I made a mistake.

This makes me question the viability of Ubuntu as a "securable platform". There are serious issues with Firefox, even 3.5, and resorting to 3rd parties or workarounds to get patches is not acceptable for security issues. If I do that I might as well blindly go on with Windows.

With this situation it also is clear that the 1st 2 sentences of the info at the psychocats link is wrong. All Firefox users should now be clicking a button or link to upgrade to version 3.5.4, which fixes 6 (!) Critical security flaws in 3.5.3.

Any pointers as to who is integrating Firefox into the Ubuntu distribution? I find scripts and other workarounds to be unacceptable for security reasons. I hope I can help do something to improve this situation which is a critical OS flaw for me.

j

---

### Post by oldjack on 2009-10-30
BTW, the Firefox vulnerabilities are detailed at:
[http://www.mozilla.org/security/known-vulnerabilities/firefox35.html#firefox3.5.4](http://www.mozilla.org/security/known-vulnerabilities/firefox35.html#firefox3.5.4)

j

---

### Post by Arafel93 on 2009-10-30
I'm new to Ubuntu as well. A few weeks ago, I installed 9.04, and liked it, so yesterday, when the prompt came up to upgrade ... I clicked "install." Seems to be a LARGE mistake for me.

After fighting the much-hailed "upgrade" for the better part of a day, now my Firefox Web Browser just disappears from the Applications list. Using the Synaptic ... it says it's installed, but it is nowhere to be found to run or use.

Since I'm new to this OS I have no clue how to fix it, but it's irritating to see some really great things that were in 9.04, wasted in such a bug-filled release of an "upgrade."

---

### Post by aysiu on 2009-10-31
Firefox 3.0.15 is the latest Firefox 3 release and contains security fixes:
[http://www.mozilla.com/en-US/firefox/3.0.15/releasenotes/](http://www.mozilla.com/en-US/firefox/3.0.15/releasenotes/)

It's also the version available in Hardy right now:
[http://packages.ubuntu.com/hardy/firefox](http://packages.ubuntu.com/hardy/firefox)

So I don't see what security has to do with it.

---

### Post by oldjack on 2009-10-31
Saying that v 3.0.15 is the latest version is just not true. Version 3.5.4 is the latest version as of today and I'd recommend it because it's a lot faster. 

To quote the Mozilla site:
"Firefox 3.0.x will be maintained with security and stability updates until January 2010. All users are strongly encouraged to upgrade to Firefox 3.5."

[[http://www.mozilla.com/en-US/firefox/all-older.html]](http://www.mozilla.com/en-US/firefox/all-older.html])

So 3.0.15 will get you by for 2 more months.

But in my case, even after clicking Reload, Synaptic still shows the latest version as 3.0.14. So what am I doing wrong or what can I do to even get 3.0.15?  Any idea?

j

---

### Post by aysiu on 2009-10-31
> **oldjack said:**
> Saying that v 3.0.15 is the latest version is just not true. Version 3.5.4 is the latest version as of today and I'd recommend it because it's a lot faster. I didn't say 3.0.15 was the latest version.

I said 3.0.15 is the latest version of Firefox 3 (as opposed to Firefox 3.5).

Even if Mozilla itself doesn't maintain Firefox 3 beyond January 2010, Ubuntu will still offer security updates to Hardy users until April 2011.

---

### Post by oldjack on 2009-10-31
OK. The package manager on my machine has finally offered up the 3.0.15 version. It seems that some received it a day or 2 ago. In any case, it's now to date. Thanks.

---

