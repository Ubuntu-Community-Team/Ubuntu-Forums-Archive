---
title: "Website Loading Issues"
date: 2006-06-15
forum: General Help
---

### Post by happyponcho42 on 2006-06-15
For some reason, certain websites either take literally ages to load, or do not load at all on my Ubuntu desktop using any browser (Firefox 1.5, Opera, Epiphany, Internet Explorer).  I have concluded that it is definitely not an issue with faulty hardware either in the computer itself nor in the network equipment due to this system dual-booting Windows; I tested this many times whereas certain websites do not load at all on Lnux, but loading up Windows on the same machine, I can visit any site flawlessly.

To see whether it was a configuration issue, I formatted my hard drive and reinstalled Ubuntu fresh and continue to have the same issues.  A couple of months ago, I had my old Linksys router and ran Ubuntu fine, with no issues loading websites.  The Linksys router, however, began acting funny so I replaced it with a Netgear WGR614 v5 router and am wired connected to it.  As I mentioned earlier, when I switch to Windows on this dual-boot machine, no issues are present.  Ubuntu, however, is on the total opposite spectrum as all I run into is problems loading up certain websites.  Perhaps the Netgear WGR614 v5 router does not like Linux using it to route through to the internet?

Is there any way I can detect the source of this problem?  I load up firefox in the terminal but no relevant error messages come up.  Anything I can do to make my Netgear WGR614 v5 router become more 'compatible' with Linux as I am absolutely 100% sure that this issue does not exist when I load up on Windows and did not exist when I was on my Linksys router?

Please help as I would hate for this to be one of the contributing factors of returning to Windows.


Thank You


If this is the incorrect forum, please suggest/move this post to the more appropriate forum where I can get the right attention.

---

### Post by mscman on 2006-06-15
Any chance that you have Insight Broadband service, and that your service just underwent an upgrade?  This was my issue that I've been dealing with for the past week, and have finally pinpointed that it is an issue with Insight's DNS servers.  I tried convincing customer support of this, but I was assured that it was a "problem with my Linux configuration", even though the service has worked perfectly up until a few days ago.  To test my theory, I set my router to use Purdue University's DNS servers instead of Insight's, and what do you know, I WAS RIGHT!

If you do happen to have Insight's service, please let me know, as this is an issue I would like to see addressed.

---

### Post by happyponcho42 on 2006-06-15
Nope, I use Comcast.  Also, I mentioned that this is a dual-boot machine.  On Linux, I encounter this issue whereas booting up in Windows, the issue does not exist.  I am looking to find anyone who can point me in the right direction in finding whatever configuration or file is getting in the way.

I think that maybe the new Netgear WGR614 v5 router does not like communicating with Linux since it works flawlessly with Windows.  Does Linux send and receive requests from the router and network differently then how Windows handles them?  My old Linksys did not seem to mind Linux whereas it seems this Netgear does?

---

### Post by mscman on 2006-06-15
You can set static DNS nameservers on your router and see if that helps.  Log in to your router, and (on mine it's on the first page, you may have to hunt a little bit) instead of automatic DNS nameservers, choose to enter your own and add:

4.2.2.2
and 
4.2.2.3

See if this helps at all.  It won't slow down your Windows side at all either, don't worry.

---

### Post by happyponcho42 on 2006-06-16
Unfortunately, the problem still persists.  I don't see why the DNS nameservers would be an issue as I said earlier, this is an issue ONLY present on Linux.  On all my other computers running Windows, there is NO problem.  This machine I am on can dual-boot into Windows and the issue does not exist, however, booting into Ubuntu, I cannot view some websites due to extremely long loadng times or just not loading at all.

Any other suggestions?

---

### Post by mscman on 2006-06-16
The reason why I suggested different DNS servers is because that's what solved the problem for my computers (and some other people's).  They acted perfectly fine in Windows, but the Linux side was *slower than DIAL-UP!!!*  I think this is due to a problem with Insight's servers interpreting the requests from Linux.

As far as other suggestions, I'm not really sure what to tell you.  Have you checked to see if local network activity is still the same speed?  Also, has your download speed decreased at all?

---

### Post by happyponcho42 on 2006-06-16
For those experiencing similar issues, the problem seemed to have subsided following the disabling of ipv6.  Refer to [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4) for disabling ipv6.

I will update if the problem persists but for now, I feel as if all light has been shed; the problem seems to have been the result of ipv6 not being supported by certain websites.

---

