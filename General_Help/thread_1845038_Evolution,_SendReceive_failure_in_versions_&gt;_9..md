---
title: "Evolution, Send/Receive failure in versions &gt; 9.04"
date: 2011-09-16
forum: General Help
---

### Post by laidback on 2011-09-16
I certainly need help. I'm trying to install Ubuntu v10.04LTS, all was going fine until I tried the email (Evolution v2.28.3). I cannot get it to send or receive.

I have it working in my previous installation, v9.04, which is on a different HDD but same pc (I can swap HDD's) but it will not respond at all in v10.04.

I've imported the settings from 9.04 via the Evolution Backup/Restore system as well as trying a freshly typed in set of details, indeed I've even tried to get it working in Ubuntu v11.04, Mint 11 and Puppy, I cannot get any response at all. I've also tried Thunderbird, same outcome, just a time out.

As my original system (9.04) still works it seems hard to see fault with my ISP and they have confirmed that the settings are correct (I assume that means at their end).

I use POP and SMTP with no encryption.

I'm completely lost so need help. Any suggestions gratefully received.

Kindest Regards
Laidback

---

### Post by howefield on 2011-09-16
It's hopelessly unlikely but you aren't working in offline mode ?

Bottom left corner as per screenshot.

---

### Post by laidback on 2011-09-16
Sorry but I'm online, it's the sort of thing that can happen though so thanks for the thought.

---

### Post by laidback on 2011-09-16
At last I have some success.
I have no idea what was (is) wrong but I reckoned that it was a comms/network issue. Despite repeated attempts at redefining my POP and SMPT connections I got no where. So in desperation I changed my network from DHCP to manual, no success, BUT, when I changed it back to DHCP, bingo, immediate success.

I've sent a few messages to myself and it appears to be working now, time will tell.

Now I need to go back to my original v9.04 to see if that still works.

---

### Post by laidback on 2011-09-16
Bad news, doesn't withstand hybernation.
Back to not working.

---

### Post by laidback on 2011-09-16
Spoke too soon, my enthusiasm got the better of me.
Doesn't survive a reboot and the above "cure" hasn't worked a second time.

---

### Post by SparTacux on 2011-09-16
Does your browser work ?    Try pinging your mail server.    Also try changing your POP and SMTP mail server names to direct IP addresses so that it doesn't have to do a DNS lookup.

---

### Post by laidback on 2011-09-16
Dear SparTacux,

You are really onto something here. Basically it works with the direct addresses, and I can ping the addresses and direct addresses. 

My browser (FF) has always worked although I did get a 'no go' just after I started pinging for the first time. It seems to have settled down again now.

I've rebooted once and all was well. Time will tell and I'll certainly do what I can to see if it's reliable.

But what's going on?, why should this 10.04LTS (and later) version not like the ip address? I understand the DNS lookup but why would it stop working?

You're a star.

I'll set this thread to solved when I'm convinced that the issue is really sorted.

Kindest Regards
Laidback

---

### Post by SparTacux on 2011-09-16
Well - it's good to see you have got a work around the problem. It sounds like some sort of DNS issue - I'd be looking at your POP and SMTP mail server names you typed in, also look at your DNS settings in your network connections and also look at the DNS settings in your modem. Other than that - try creating another temporary user account and log on as that new user and go through the process of setting up Evolution again except this time type the details in manually rather than restoring from a backup file.

Hope that helps

---

### Post by laidback on 2011-09-17
Still working.

SparTacux,
Thanks for the extra suggestions. I did try to enter the details manually and with a new account when I first started the 10.04LTS installation but hit a brick wall. I can't tell you how many times I've re-entered the data. I've also tried other OS's all to no avail. I also tried Thunderbird but that doesn't let me create an account unless it can get a response over the internet to a query it seems to insist on running based on my email id so no go there either.

I agree that it would appear to be a DNS issue, not sure how to view/alter DNS settings on the PC, Network Connections doesn't appear to have an option for that. I'll take another look at the router/modem but changing anything there fills me with horror.

But never mind, if all else fails at least I now know how to effect a workaround until something else comes along thanks to you.

Kindest Regards and many thanks. I'll keep you posted.

---

### Post by laidback on 2011-09-18
Still working with the direct IP addresses set, Brower is fine using DNS!

So it's not fixed such that I understand what's wrong but I do have a very useful work around.

---

### Post by SparTacux on 2011-09-18
good stuff.   Out of curiosity - what exactly were you typing in Evolution as the POP and  SMTP server names. Do you have any firewall set up in either your computer or modem/router?

---

### Post by laidback on 2011-09-19
Firewall on the router, as supplied in Ubuntu for v10.04LTS

Also see email .

---

