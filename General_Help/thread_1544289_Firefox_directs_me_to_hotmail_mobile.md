---
title: "Firefox directs me to hotmail mobile"
date: 2010-08-02
forum: General Help
---

### Post by plitter on 2010-08-02
Hello, there's probably an easy fix to this problem, but it's really annoying. How can I get to the regular view on hotmail? Firefox always directs me to hotmail mobile... It works fine with google chrome.

---

### Post by plitter on 2010-08-03
Bump.

---

### Post by ahcox on 2010-08-04
> **plitter said:**
> Hello, there's probably an easy fix to this problem, but it's really annoying. How can I get to the regular view on hotmail? Firefox always directs me to hotmail mobile... It works fine with google chrome.
 
I installed user agent switcher( [https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/) ) and was able to see a desktop-style hotmail inbox while pretending to be using IE 6, 7, or 8. It didn't render correctly though, and I couldn't get to the bodies of my emails. It may be that the mobile site is the best that MS can offer right now.
A.

---

### Post by ahcox on 2010-08-04
> **ahcox said:**
> I installed user agent switcher( [https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/) ) and was able to see a desktop-style hotmail inbox while pretending to be using IE 6, 7, or 8. It didn't render correctly though, and I couldn't get to the bodies of my emails. It may be that the mobile site is the best that MS can offer right now.
A.

 Hmm, having logged-in pretending to be IE 6, I switched user-agent back to firefox, refreshed, and my inbox popped back into view in full working order. 
 A

---

### Post by plitter on 2010-08-05
I got in, but I cant do anything there, can't read email, delete, write or anything.... can mark the email though:P so u have the same problem? is it a problem for everyone having firefox 3.6.9pre?

---

### Post by LorenzC on 2010-08-07
I'm experiencing the same problem on 3.6.9pre and 4.0b3pre.

---

### Post by gopher38 on 2010-08-09
I'm also trying to find a fix for this.  I'm on Jaunty on a PowerPC, so I can't use Chrome (no PPC version).  I tried the user agent switcher.  Using IE 6, I could log into Hotmail normally, but couldn't open a message, reply or anything else.  Switching back to "default agent' and refreshing put me back into Mobile view.

---

### Post by claracc on 2010-08-10
I had the same problem with kmeleon browser in windows xp, it was solved changing the user agent to
Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.1) Gecko/20090624 Firefox/3.5, as it is said in kmeleon forum [http://kmeleon.sourceforge.net/forum/read.php?1,108969,109219#msg-109219](http://kmeleon.sourceforge.net/forum/read.php?1,108969,109219#msg-109219)

As kmeleon is a mozilla type browser, perhaps the same tip works with firefox. So you try to switch the user agent of your browser.

---

### Post by gopher38 on 2010-08-10
> **gopher38 said:**
> I'm also trying to find a fix for this.  I'm on Jaunty on a PowerPC, so I can't use Chrome (no PPC version).  I tried the user agent switcher.  Using IE 6, I could log into Hotmail normally, but couldn't open a message, reply or anything else.  Switching back to "default agent' and refreshing put me back into Mobile view.

OK, making progress.  The user agent switcher originally only has a few options.  Found a site where you can download a much longer list in xml and then tried Firefox 3.something and 3.5.5, both of which seem to work well, even though my Firefox is 3.6.8.  Only problem is that I can't set it to the default, so I have to use the switcher agent every session when I want to use hotmail.  

Does anyone know how to change the default?  I couldn't find a way to do it.  I also tried changing the agent in about:config, but it always goes back to the original.  Thanks.

---

### Post by pepitofernando on 2010-08-24
SO, to last user:

Can you say where you found the addon?

Thanks

To Everyone:

A dirty solution is to change the value  that microsoft hotmail looks to ban you ubuntu users from hotmail:

 Go to about:config

change the "general.useragent.vendor" from "Ubuntu" to "Firefox" (without the quotes)


Now you have a "nice" standard hotmail

(Solution From [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/219166/comments/9](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/219166/comments/9))

---

### Post by gopher38 on 2010-08-24
Sorry.  Do not remember exactly.  I think I got the switcher agent at the URL posted in the 3rd message of this thread.  If not, then I did a google search.  The XML browser list was through a google search.  I don't remember what keywords I used, but it was on the first or second page of replies, so it can't be hard to find.

---

### Post by C4K3 on 2010-08-31
> **pepitofernando said:**
> 

To Everyone:

A dirty solution is to change the value  that microsoft hotmail looks to ban you ubuntu users from hotmail:

 Go to about:config

change the "general.useragent.vendor" from "Ubuntu" to "Firefox" (without the quotes)


Now you have a "nice" standard hotmail

(Solution From [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/219166/comments/9](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/219166/comments/9))




Worked like a charm, didn't even have to restart Shiretoko/Firefox. I was literally just about to start a gmail and make the huge switch from my long-standing personal hotmail. I'll have to go to that about:config thing on my friends computers and then look at them and do my best evil laugh. That'll teach them to draw on me while I sleep!

---

### Post by mvz on 2010-09-20
The key part of the user agent string that seems to trip up hotmail is 'ppc'. I guess that gets interpreted as pocket-pc :(. Using user agent switcher to replace ppc with x86 solved the problem for me.

---

