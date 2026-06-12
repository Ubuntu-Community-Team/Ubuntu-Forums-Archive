---
title: "more than 7 bluetooth devices"
date: 2011-01-30
forum: General Help
---

### Post by drdanielfc on 2011-01-30
Hello,
I am planning on investing some time into a project that involves communication with 8 wii remotes. On wikipedia, ([http://en.wikipedia.org/wiki/Bluetooth#Communication_and_connection](http://en.wikipedia.org/wiki/Bluetooth#Communication_and_connection)) it states that only 7 devices can connect to one master at a time. Would it be possible to have 8 communicate with my computer all at once? I plan on using a dedicated ubuntu system on a netbook. I would appreciate any ideas.

Thanks,
Dan

---

### Post by hansdown on 2011-01-30
Hi drdanielfc.

That article suggests, that you can connect two or more piconets to form a scatternet.

---

### Post by drdanielfc on 2011-01-31
I thought of that, but seeing as the Wii Remotes are proprietary, i do not think that I would be able to modify them like that. Would it be possible using two bluetooth dongles and having 4 connect to each?

Thanks for the response,
Dan

---

### Post by hansdown on 2011-01-31
I'm assuming that would work, though I've never tried it.

I came across some info that may be useful.

[http://www.google.com/search?client=ubuntu&channel=fs&q=connecting+2+piconets+to+form+a+scatternet&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=connecting+2+piconets+to+form+a+scatternet&ie=utf-8&oe=utf-8)

---

### Post by drdanielfc on 2011-02-05
Sorry to revive a (slightly) old thread but i'd just like to post my solution.

It IS possible with multiple dongles. Here is some information I got from a the very helpful AirCable:

> Daniel,
Each Bluetooth dongle can handle 7 devices at a time. Certainly an infinite amount, if 
you keep only 7 connected at a time.
Then you add more Bluetooth dongles, each handling 7 connections.
Linux supports 15 AIRcable Host XR3 per machine, gives you over 100 connections.
Hope that helps
Regards
Juergen
Wireless Cables Inc.

and also:
> no, sorry Windows and OSX cannot handle multiple dongles


some tricks exist to do 2 dongles, but not more


USE LINUX!!!!! you are better off anyway with that...


Edit:
Also pointing out these pages:
[http://bluecove.org/bluecove/apidocs/com/intel/bluetooth/BlueCoveImpl.html#useThreadLocalBluetoothStack()](http://bluecove.org/bluecove/apidocs/com/intel/bluetooth/BlueCoveImpl.html#useThreadLocalBluetoothStack())
[http://markmail.org/message/7fbina4722qojywy#query:useThreadLocalBluetoothStack+page:1+mid:7fbina4722qojywy+state:results](http://markmail.org/message/7fbina4722qojywy#query:useThreadLocalBluetoothStack+page:1+mid:7fbina4722qojywy+state:results)

---

### Post by hansdown on 2011-02-05
Glad you got it sorted, drdanielfc.

Good job.

---

