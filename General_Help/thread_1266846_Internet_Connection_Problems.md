---
title: "Internet Connection Problems"
date: 2009-09-15
forum: General Help
---

### Post by rangerman on 2009-09-15
[SIZE=2]Hello from a newbie – I have a problem that I would greatly appreciate help with.[/SIZE]
 

 [SIZE=2]I have two Acer Aspire One A150-AW netbooks which originally came with Linpus Linux Lite, but have subsequently been changed to run Ubuntu Netbook Remix 9.04 (Jaunty Jackalope) and both of which are configured in exactly the same way.  Both were running fine until my wife inadvertently killed the wireless internet connection a few weeks ago.  This required reconfiguring and on advice from the provider the name was changed, although the WEP key remains the same.  Both netbooks pick up the and will connect to the wireless router, however, the problem is that on one netbook although it will connect to the wireless router and you get a good signal, when you open Firefox and get the Ubuntu/Google startpage, 9 times out of 10 the connection from there will either time out or take an inordinate amount to time to connect to the desired webpage.  This is also the case when you directly type in a web address.  This netbook additionally has problems trying to receive updates (probably attributable to the net connection problem) and often quotes excessive time for the downloads to update.[/SIZE]
 

 [SIZE=2]It is totally stumping me how to resolve this; I can have both netbooks running side-by-side, the one works seamlessly whereas the other won’t!  The wireless connection on the troublesome netbook also works fine on my work wireless connection. Any advice on how to fix this would gratefully be received.[/SIZE]

---

### Post by P4man on 2009-09-15
hmm.. the fact that it works fine at work, suggests something is wrong with the router (or configuration). could it be an IP address conflict with a third device? Perhaps you can post the output of

ifconfig and iwconfig on both machines?

Also, on the "troubled" netbook, if you connect to the router's web configuration page (usually 192.168.1.1 or similar), does it behave properly?

---

