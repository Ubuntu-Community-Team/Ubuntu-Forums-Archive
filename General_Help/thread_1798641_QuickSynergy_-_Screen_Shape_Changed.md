---
title: "QuickSynergy - Screen Shape Changed"
date: 2011-07-06
forum: General Help
---

### Post by AnotherBrian on 2011-07-06
When I start quicksynergy -f as a server (i.e., press execute) I get: 

INFO: CServer.cpp,1141: screen "abc" shape changed

What does this mean and does it indicate a problem? 

Also, when starting quicksynergy -f, the very first line display is

(quicksynergy:2994): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

Do either of these messages suggest why I can't get quicksynergy to work. 

Between my two machines, using wireshark, I can confirm the client application sends a TCP message over to the server machine and that the server application does not respond.   The same behavior is observed when reversing the roles of two machines, client and server.  

I am running lucid 10.04 and 64-bit 11.04 natty. 

Thx!

---

### Post by AnotherBrian on 2011-07-07
Here is a good troubleshooting procedure  - see step 5: 

[http://synergy2.sourceforge.net/running.html](http://synergy2.sourceforge.net/running.html)

In my case it was a firewall blocking incoming port connections.  
I opened up port 24800 on the server - just for my client. 

Thus the two  messages mentioned above  were of no consequence.

---

