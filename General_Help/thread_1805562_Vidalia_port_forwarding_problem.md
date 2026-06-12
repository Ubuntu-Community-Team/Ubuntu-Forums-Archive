---
title: "Vidalia port forwarding problem"
date: 2011-07-16
forum: General Help
---

### Post by robbiemacg on 2011-07-16
Hi all. I've been using TOR for years, giving back by running a relay (and managing it with Vidalia) for about the last year or so. I've recently come up against a problem I can't seem to get me head around:

All of the sudden, Vidalia seems to be unable to configure port forwarding, and my node's not showing up as an active part of the network.

TOR/Polipo appear to be functioning normally.
I can access the TOR network as a client using TORButton, etc.
Vidalia reports that it can connect to the network, and there's nothing in my error logs.

BUT, when a do a TOR check ([https://check.torproject.org/](https://check.torproject.org/)), I get the "Sorry. You're not using TOR." message. Usually, if you're running a relay that page will display your correct public IP and an affirmative message (cause packets/traffic originating from your IP are exiting the network).

I've checked my Vidalia settings, and the only thing that seems out of the ordinary, is that yesterday Vidalia seemed unable to set up port forwarding (despite router settings being correct and UPnP being enabled). 

Any thoughts on where I should go from here? I'm feeling really bad about my relay being down.

I'm on 11.04 (64 bit) and my system's up to date.

---

### Post by robbiemacg on 2011-07-16
A quick update and bump. 

The exact error message I'm receiving is "**Failed to add a port mapping**." An image of the dialogue is attached. I'll also upload this issue to the Vidalia mailing list I subscribe to, report back if that group has feedback.

Now I'm going for a run.

R.

---

### Post by Dangertux on 2011-07-16
Have you considered enabling port forwarding manually?  I believe only the TOR port needs to be forwarded 9050/tcp is default iirc. 

Did anything change in your ufw/iptables/netfilter/any other firewall you may be using?

---

### Post by robbiemacg on 2011-07-18
Thanks for your reply, [Dangertux]("http://ubuntuforums.org/member.php?u=1322416"). 
I'm not much of a networking guy, so I'm pretty cautious when it comes to changing setting and mucking about with my router. As a result, I tend to keep back ups of my settings, keep logs, etc. 
I just restored my settings from a file I had and now things seem to be working OK... I think.

After your post, I started thinking about what could have caused a change in the way my router was handling traffic. I realized that a friend who was recently visiting (who works for a big mobile tech company) had been doing work over their Co.'s VPN. I'm not sure what might have happened, but, know a little bit about those networks and how packets get in and out of them, I'm thinking there could have been some correlation. The timing makes sense anyway.

I'm still curious, but I'm marking this thread **[Solved]** since port forwarding is now working as advertised.

R.

---

