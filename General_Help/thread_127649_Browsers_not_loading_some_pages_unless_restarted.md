---
title: "Browsers not loading some pages unless restarted"
date: 2006-02-09
forum: General Help
---

### Post by mmissire on 2006-02-09
I use Breezy on two machines, and have this problem on both.

Ubuntu 5.10 comes with Firefox 1.07, which mostly worked fine for me. I became irritated that the fonts seemed to jiggle around when I highlighted text on certain pages (like Slashdot).

I used Automatix to upgrade to Firefox 1.5, and to install Opera as well. I believe that is when the trouble started, on both machines (although I've not yet rolled back to verify this).


It seems that I cannot load some web pages, after a page or two has been loaded. For example:

1) In Firefox, I go to java.sun.com. It loads.
2) I click on the J2SE Core/Desktop link, which points to [http://java.sun.com/j2se](http://java.sun.com/j2se). It never loads. I just get a white page. The throbber goes for a while, then gives up.
3) I quit Firefox, and restart. I note that I can surf directly to java.sun.com/j2se, and it loads fine. But subsequent pages on that site then give me trouble.

I have noticed only certain web sites give me this problem. In all cases, I can load the troublesome pages if I quit the browser and restart it, and paste in the URL. The problem seems to "kick in" after loading a page or two of some sites.

I tried the same pages in Opera, and had similar trouble. This made me think it's something to do with the network configuration, but I am unsure.


I don't see anything interesting in /var/log/messages.

I am using an old Linksys router; I wonder if this is causing the issue?
One PC uses wireless and WEP, but the other does not use wireless at all.
I dual boot Windows XP on each machine, and Firefox 1.5 has no trouble with the same sites and pages.

I Googled a bit, and found some people complaining about long delays and page load problems relating to IPV6 and ubuntu and Firefox. I tried disabling IPV6 both in Firefox "about:config" (there's some IPV6 DNS lookup setting you can turn off, I think) and the OS level... but I put things back the way they were because it didn't make a difference.


I tried moving ~/.mozilla and restarting with a fresh profile. No change.


My next step will probably be to go back to Firefox 1.07 and be sure it did not happen there. However, I much prefer Firefox 1.5, and would rather solve this another way.

Has anymore else had any similar troubles? Especially with [http://java.sun.com](http://java.sun.com) and then clicking the "J2SE Core/Desktop" link in the upper left?

Thanks!

---

### Post by dcstar on 2006-02-10
[QUOTE=mmissire]
.........
Has anymore else had any similar troubles? Especially with [http://java.sun.com](http://java.sun.com) and then clicking the "J2SE Core/Desktop" link in the upper left?

Thanks![/QUOTE]
That site works fine on my FF 1.5.0.1.

I can only suggest you use one of the other methods to install FF 1.5 other than Automatix, it is a reasonably simple process, here's how I did mine:

[http://www.ubuntuforums.org/showpost.php?p=633942&postcount=315](http://www.ubuntuforums.org/showpost.php?p=633942&postcount=315)

And I did have problems with my FF 1.5 loading certain sites, but the .mozilla profile rename fixed that in my case.

---

### Post by nanotube on 2006-02-10
hmm, strange. maybe automatix did something weird...? i installed firefox by following these instructions:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
and it works without any problems for me. (and is much faster than the stock 1.0.7 install). try removing the automatix version, and installing again, manually?

---

### Post by mmissire on 2006-02-11
Thanks for the replies.

I noticed by Linksys router's firmware was at version 1.45.<something>, dating from 2003.
There was an update to version 1.52.02 available on the support page of their web site.
This is for a BEFW11S4_v4.

Updating the firmware on the Linksys  completely resolved the problem.

---

