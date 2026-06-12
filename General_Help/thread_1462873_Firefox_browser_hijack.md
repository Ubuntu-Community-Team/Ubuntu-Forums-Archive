---
title: "Firefox browser hijack"
date: 2010-04-26
forum: General Help
---

### Post by StuartN on 2010-04-26
I seem to have some kind of browser hijacking running in a fresh install of Ubuntu 10.04 with Firefox 3.6.3

It seems to be badly written because mostly I get a dialog box saying "The URL is not valid and cannot be loaded." and on other occasions I get invalid URLs such as [www.].com](www.].com)

When successful it has opened fscstore.com, tony.com and [www.ubuntu.com](www.ubuntu.com) (!)

I have not seen behaviour like this in Ubuntu previously (and I have no additional software installed), so I am wondering if these hijacks are being triggered by a (possibly defaced) web site that I have open, or is anyone else experiencing similar activity?

---

### Post by kerry_s on 2010-04-26
sounds like bad dns to me.
if your running any extensions, try disabling them.

---

### Post by .:PiXi²:. on 2010-04-26
Strange thing, Firefox is working fine over here.
Traceroute ubuntu.com, that could say more.

---

### Post by StuartN on 2010-04-26
> **kerry_s said:**
> sounds like bad dns to me.
if your running any extensions, try disabling them.

I don't think it is a DNS problem. The page that I am reading is suddenly replaced (without me doing anything) by another page, perhaps twice an hour. The latest successful transfer was to never.com, but most are unsuccessful and just call up the "not valid" dialog.

I have no extensions running - I have not installed any and I have disabled the Ubuntu Firefox extensions. This is literally a few-days old release candidate installation, and my web browsing is very limited.

I suspect another (previously trustworthy) forum that I visit. Where should I look for something like this? Javascript on the suspect site?

---

### Post by kerry_s on 2010-04-26
have cleared all your cache,cookies,history?
maybe better off just deleting your ~/.mozilla folder & start new.

---

### Post by utnubuuser on 2010-04-26
You might try disabling ipv6

---

### Post by v1ad on 2010-04-26
take kerrys advice

---

### Post by lovinglinux on 2010-04-27
Delete ~/.mozilla/firefox and start from fresh with a clean profile. If it doesn't help, then it is probably a dns issue.

---

### Post by StuartN on 2010-04-27
> **lovinglinux said:**
> Delete ~/.mozilla/firefox and start from fresh with a clean profile. If it doesn't help, then it is probably a dns issue.

I actually had my system taken down by the initramfs bug [http://ubuntuforums.org/showthread.php?t=1463032](http://ubuntuforums.org/showthread.php?t=1463032) yesterday, so I am on a clean install again, with no redirected browser windows.

I do not understand what you mean by "a dns issue"?

More importantly, where would someone hide code that redirects the active browser page to another site? I am assuming that this was simply javascript inserted into a page that I trusted, or possibly that it was an error in an advertising script (the redirected pages all look like legitimate retail).

---

### Post by lovinglinux on 2010-04-27
> **StuartN said:**
> I actually had my system taken down by the initramfs bug [http://ubuntuforums.org/showthread.php?t=1463032](http://ubuntuforums.org/showthread.php?t=1463032) yesterday, so I am on a clean install again, with no redirected browser windows.

I do not understand what you mean by "a dns issue"?

More importantly, where would someone hide code that redirects the active browser page to another site? I am assuming that this was simply javascript inserted into a page that I trusted, or possibly that it was an error in an advertising script (the redirected pages all look like legitimate retail).

Depending on the DNS service you use, you get redirected when Firefox cannot reach the web site due to 404 error or when the DNS server cannot resolve the address. For instance my ISP redirects me to the Telecom user page, which is something I shouldn't even see, since here we have to contract the service directly from the Telecom but authenticate through the ISP (content provider). Anyway, I only see the Telecom page when my ISP DNS is screwed and it looks like a scam site. Other DNS services, like OpenDNS, redirects you to custom search pages. So perhaps the redirection is messed up, taking you to weird addresses. Who knows...

---

### Post by StuartN on 2010-04-27
> **lovinglinux said:**
> So perhaps the redirection is messed up, taking you to weird addresses. Who knows...

That does not fit with the symptoms. It is as if there is a page-refresh that replaces the active page with a retail site.

---

### Post by lovinglinux on 2010-04-27
> **StuartN said:**
> I actually had my system taken down by the initramfs bug [http://ubuntuforums.org/showthread.php?t=1463032](http://ubuntuforums.org/showthread.php?t=1463032) yesterday, so I am on a clean install again, with no redirected browser windows.

So, install [NoScript](https://addons.mozilla.org/en-US/firefox/search/?q=NoScript) and move on.

---

### Post by StuartN on 2010-04-27
> **lovinglinux said:**
> So, install [NoScript](https://addons.mozilla.org/en-US/firefox/search/?q=NoScript) and move on.

That does not help with locating the site that causes the redirection and, if appropriate, informing the site operator.

---

### Post by DawieS on 2010-04-27
I have found **Adblock Plus** to be a very useful tool to 'fine-tune' the behavior of a website exactly the way I want it.

If you open the **Blockable Items** at the bottom of the screen, and reload the screen while blocking different redirections, you will soon find the offending one.

It is possible that the website in question has been updated with a bug, or even hijacked with malware.

I do not use any default block-lists, but have created my own list, which is suited for the websites I regularly use. I also use it interactively to unblock certain features which I may want from time to time (for example, I just unchecked ***yui.yahooapis.com*** in **Preferences** and clicked **Apply** before making this post).

It is also easy to copy/paste an existing block-list to and from a text file, in order to quickly customize a new installation.:smile::smile:

---

### Post by Vaphell on 2010-04-27
isn't that a problem related to middlemouse.contentLoadURL in about:config?
when you have that enabled and middle-click firefox tries to load the clicked text as an URL, which usually is a random thing if you do that by accident. I've seen that "The URL is not valid and cannot be loaded" message dozens of times before disabling that option.

---

### Post by StuartN on 2010-04-27
> **Vaphell said:**
> isn't that a problem related to middlemouse.contentLoadURL in about:config?

Thank you for your helpful response. My middlemouse.contentLoadURL is set to false, but browser.tabs.opentabfor.middleclick (and three other middlemouse.* options) are set to true.

I am not experiencing any sudden and unexpected switches of my active window content at the moment (since reinstalling), but will test these settings if it recurs. I do not have a middle mouse button, but of course the hardware (Synaptic touchpad) could still be generating the events.

---

### Post by MIJ-VI on 2010-08-04
Hmm... I wonder if the Firefox hijack discussed here is related to the wider browser hijacking hair-pull in this thread:

Firefox is being redirected to _xxxxxxxxxxxxxxxx_
[https://support.mozilla.com/en-US/forum/1/739986#threadId745211](https://support.mozilla.com/en-US/forum/1/739986#threadId745211)

---

### Post by StuartN on 2010-08-04
> **MIJ-VI said:**
> Hmm... I wonder if the Firefox hijack discussed here is related to the wider browser hijacking hair-pull in this thread:

I don't know - I never had that problem before installing 10.04 and have not had it again since a full re-install. It seemed like a very poor attempt to direct accesses to an online shop (tony.com and others), probably for advertising revenue. I did not receive any useful responses at all in this thread.

---

