---
title: "Internet trouble"
date: 2006-04-17
forum: General Help
---

### Post by JoeeT on 2006-04-17
I connect to the internet through a router, to which my computer is connected via cable.

I can connect to my network fine. I am able to access my router's control panel, and I can download updates and applications using the synaptic package manager with no trouble.

However, when I use Firefox web browser, some pages take a while to load (eg the mozilla start page) and some just dont load at all. Firefox finds the page and then spends ages connecting to it, until it just times out.
This happens on mozilla web browser also.

I also try connecting to messenger services using the messenger app (I forget what it is called) but each time I try, the program is continually 'connecting' and progressing no further.

Everything works fine on my other computers, which both use Windows XP, and if it's of any importance, I have the same problem whether or not I used static or dynamic IPs

Does anybody have any idea what could be going on? Networking has never been my strong point!

---

### Post by presentt on 2006-04-17
Perhaps there is a proxy that FF is not configured to detect?

If so, you can configure proxy connections in Firefox 1.5 by Edit-Preferences-General-Connection Settings...

Try selecting "Auto-detect proxy settings for this network," or enter the settings manually.

---

### Post by handy on 2006-04-18
Do the following to remove **IPv6** from your Ubuntu system, **IPv6 **can cause your internet connection to be slow, or, as in my case, not work at all!!

Type **about:config** no quotes into the location bar in Firefox (this may work in Opera?)

Then type **ipv6** into the **Filter** field.

Double left click on the line that comes up to change it's boolean value to **True**

In a **Terminal** enter the following:

**sudo gedit /etc/modprobe.d/aliases**

Change this line: [B]alias net-pf-10 ipv6
[/B]
To this: **#alias net-pf-10 ipv6**

(# = commented out), [B]Save & Exit
[/B]
Now you can forget about **ipv6**, possibly for years.

**Note**: If you have organised to have a **Static IP Address** with your ISP the following does not apply to you.

Another thing that can slow your internet connection down, is if you have **Static IP Address** selected instead of **DHCP**, to check this:-

Goto - **Menu:** ***System/Administration/Networking*** double left click on your ethenet device - usually eth0, this will bring up the I**nterface Properties** dialogue.

Now check that **the Connection Settings - Configuration:** pull down says **DHCP**.

**DHCP** is much faster when changing connections from server to server.

If your setting is **Static IP Address**, it will take a long time to load a page from a New server. Once on that server the pages should load normally, until a page is called from a different server, then that page will be slow to arrive.

I hope this gets you out of trouble.:KS

---

### Post by JoeeT on 2006-04-19
Thanks, though I found the solution in a similar thread not so long ago :) The about:config method worked perfectly.

---

### Post by handy on 2006-04-19
[QUOTE=JoeeT]Thanks, though I found the solution in a similar thread not so long ago :) The about:config method worked perfectly.[/QUOTE]

I can't get internet **AT ALL**, without doing the **about:config** thing!!

Bizaare!!!

---

