---
title: "evolution and NHSnet (MS Exchange 2007)"
date: 2009-07-18
forum: General Help
---

### Post by refdoc on 2009-07-18
This might be a bit specific for these fora, but it bugs me endlessly and is one of my current main IT problems.

The British NHS migrated earlier this year its sluggish but functional standards compliant Email system to MS Echange 2007. 

IMAP access is not available if you are outside the confines of NHS.
To access email you can though use Outlook OWA.

I have been trying unsuccessfully to configure Evolution to do just this.

I am using the Echange OWA plugin and configured it like this:

username: <myusername>@nhs.net
OWA url: [https://web.nhs.net/owa](https://web.nhs.net/owa)

I will then move through two password dialogues firstly asking for my password for <myusername>@nhs.net and then asking again for a password for <myusername>. Finally I will get a message which reads:
[I]Could not configure Exchange account because 
an unknown error occurred. Check the URL, 
username, and password, and try again[/I]

Now username (including the "@nhs.net") and password *are* correct as I use them with Firefox and at work via IMAP.

If I run evolution from the console I get some intriguing error messages for the above exchange:

[I]** (evolution:20452): DEBUG: EI: SHELL STARTUP
component_id:OAFIID:GNOME_Evolution_RSS:2.26

(evolution:20452): Gtk-CRITICAL **: gtk_list_store_get_path: assertion `iter->stamp == GTK_LIST_STORE (tree_model)->stamp' failed

(evolution:20452): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(evolution:20452): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
EI: MAIL PREFS
(evolution:20452): camel-CRITICAL **: camel_service_get_path: assertion `service->url' failed
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Exchange'
  
[/I]

I would be delighted to get some clue from you lot. I understand that Evolution MS Exchange support is pretty hard to figure out, but I am also aware that NHS net has done all they could do to bugger it up for us who use Linux, so there might well be (I assume there are) some special NHSnet pitfalls.

Thanks guys.

---

### Post by txcrackers on 2009-07-18
I haven't been able to get Evolution to connect up to Exchange 2007 at all - so right now I'm using Outlook *(ew!)* in Crossover for Linux.

---

### Post by GrumpyBob on 2009-07-20
Yes, my work email is now on Exchange 2007, and I have to resort to OWA to get my email.

I read about the Brutus plugin, but it seems to have disappeared from the web.

Robert

---

### Post by fishy6969 on 2009-10-20
Sorry to drag up an old thread

Did you ever get this to work?? I've be trying to get this to work (and with android)

---

### Post by GrumpyBob on 2009-10-20
I tried again yesterday after a bunch of Evolution updates appeared (Karmic daily updates).  Evolution just crashed as soon as I entered my Exchange account details.  Haven't had time to investigate further.

Robert

---

### Post by freeatlast on 2009-10-23
I am having the same issues, I can connect via IMAP without any problem, but need to connect as an exchange server because I really need the calandar functionality.  I tried Kontact but can't get that to work either, any suggestions?

---

### Post by fishy6969 on 2009-10-24
No luck so far. I have managed to connect from an android phone using the HTC Work Email program. Sadly it's closed source so I can't delve into how it's doing it.

---

### Post by SAABdriver on 2009-11-04
There is another OWA url which bypasses the keyboard entry bit but I still have not had any luck.
[https://outlook.nhs.net/owa](https://outlook.nhs.net/owa)

---

### Post by mrchumpley on 2011-07-12
I too have just moved to nhs.net mail and have been trying to configure Evolution. I wonder if the problem lies in the Java Applet Whale security that needs to run in the background? 

Has anyone ever managed to sort this out?

---

### Post by lennoni on 2012-11-21
Some clues

I'm using evolution 3.4.4

Using the default Evolution add account settings, I can't connect: it's not resolved

I pinged outlook.nhs.net and got back the IP address 62.208.144.129

I then replaced the "exchange.nhs.net" with the IP and set authentication to "basic" (note: it looked up the address itself from somewhere!)

Restarting evo then requests your password which I entered. 
The problem is then that this stalls and can lockup evolution, preventing it from logging out.

This feels nearer, but not working yet

---

### Post by wildmanne39 on 2012-11-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

