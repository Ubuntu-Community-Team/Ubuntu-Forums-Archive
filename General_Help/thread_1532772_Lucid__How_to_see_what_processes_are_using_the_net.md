---
title: "Lucid:  How to see what processes are using the network?"
date: 2010-07-16
forum: General Help
---

### Post by 3boxes on 2010-07-16
I keep the network window of System Monitor active on my panel to see if anything is going on with the network.

After the last upgrade, lucid has been having nonstop short, small bursts of network activity, showing in system monitor as received data of approx 60 kb, then 0, then ~60, then 0, continuously.  This is occurring before any applications are opened.

Whatever it is, it starts to tie up the processor until performance is unusable.

The processes screen does not offer any clues, perhaps because the data transfers are so small and spaced out.  It still should indicate what is tying up the CPU, though.  In the attached screencap, you can see the network activity pattern in the system monitor window in the panel.

Is there any way to monitor what processes are accessing the network in order to see what is going on?

---

### Post by bodhi.zazen on 2010-07-16
Wireshark
ntop
netstat -ntulp
lsof -n -i -P

---

### Post by 3boxes on 2010-07-18
Thank you.

It looks like the culprit is my new Asus WL-500gp router.
Any idea why would it be doing this?

---

### Post by bodhi.zazen on 2010-07-18
> **3boxes said:**
> Thank you.

It looks like the culprit is my new Asus WL-500gp router.
Any idea why would it be doing this?

You can look at this :

[http://en.wikipedia.org/wiki/Spanning_tree_protocol](http://en.wikipedia.org/wiki/Spanning_tree_protocol)

---

