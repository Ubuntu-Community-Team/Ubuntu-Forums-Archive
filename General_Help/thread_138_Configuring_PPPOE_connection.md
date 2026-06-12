---
title: "Configuring PPPOE connection"
date: 2004-10-11
forum: General Help
---

### Post by misGnomer on 2004-10-11
I've yet to install Ubuntu on hard disk but took the (Oct. 02) livecd for a test ride. I couldn't get the PPPOE connection up and would like to know what is Ubuntu-live's lineage wrt. Gnoppix/Morphix/Knoppix? Apart from the desktop environment, how closely are the backends related?

Anyway, for comparison I downloaded the latest Knoppix (3.7 PC-Welt) from last month and after configuring network card and running pppoeconf, and having to manually reset the default gateway (I wonder why though...), Knoppix obeyed "pon dsl-provider" just fine.

Ubuntu-live however failed to keep ppp0 up more than a few seconds (verified with a quick "ifconfig") before vanishing in thin air. I haven't seen anyone complain about Ubuntu's pppoe setup so I was wondering if there was some method to the madness of setting up pppoe connections?

Secondly, since internet connectivity is one of the major reasons for people to try Ubuntu, are there any plans to try and make configuring network connections easy enough for even technophobes to dare try it? Ideally there would be a HIGified utility where all stages of setup would be concentrated (and any error messages relayed to, plus a troubleshooting guide) along with an on/off panel applet and net traffic indicator.

PS. Would it be a good idea to add dates to the preview betas to prevent them from getting mixed up and to help the switchover from one torrent to the next? E.g.  "live-i386.iso"  --&gt;  "live-i386-041002.iso" or something. A centralized graphical tracker would also be handy...

misGnomer

---

### Post by misGnomer on 2004-10-12
Well, I'm posting this from the Gnoppix 0.8.1b7 (Oct. 08 ) liveCD so if Ubuntu-live is derived from it then my PPPOE setup woes might soon be history as "ifconfig eth0 up" followed by "pppoeconf" worked just fine.

I had other problems with Gnoppix, such as apps not starting at all (like Firefox) or dying while starting (Mozilla) and X failing to initialize originally leading to automatic reboots until I tried Failsafe mode but we'll see about those when the next version of Ubuntu-live is released...  :^)

PS. how does one direct the bootup messages e.g. to a floppy so they could be re-examined in case of such spontaneous rebooting during the boot sequence?

---

### Post by junme on 2004-10-25
am having same problem reluctant to install  main iso

---

### Post by HiddenWolf on 2004-10-26
I am severely dissapionted that the installer does not take care of the networking process.

This installer, like the Debian Sarge one, tries to configure the network by dhcp, and finds your internal network IP, then it just assumes there is an outbound connection.

In my humble opinion, it should try and ping ubuntulinix.org to confirm the connection, then if that fails, offer the option to configure the network manually.

I think it is a severe overview not to give the option to set up rp-pppoe at this stage.
I had to cut off the stage2 installer before it would go and time out waiting for archives and security.ubuntulinux.org.

As it is, I have X, ALSA, printing, everything but pppoe

---

### Post by Hazzl on 2004-11-05
This is [bug 2825](http://https://bugzilla.ubuntu.com/show_bug.cgi?id=2825) . The work around is to ```
~# ln -f /etc/pppd/resolv.conf /etc/resolv.conf
```

---

### Post by HiddenWolf on 2004-11-13
I finally got mine to work flawlessly.

---

### Post by mayonesiac on 2005-09-18
hi, i'm completely new to linux and have just installed ubuntu. could someone please walk me through with setting up a pppoe connection? during the ubuntu instalation i chose not to configure the network settings

---

### Post by predator on 2005-09-24
yes, I believe networking should by much easier from the start with ubuntu for n00bs..

When I ran the installer, it was way too debian like, which I had just installed 2 days earlier, gave up, and deleted.

---

### Post by drogoh on 2005-09-24
PPPoE has always been an iffy thing to get working with Linux in general.  If you have an external router, always use that for PPPoE and just set up DHCP for your LAN.  Your frustration gland will thank you and it will "just work", as long as the router is working properly.  If you don't have an external router, my suggestion is to consider looking into one.

---

### Post by billyswong on 2005-09-27
In windows, I can install ras-PPPoE and everything afterward is easy.  Why can't Linux do something similar?

Today I tried out the Ubuntu liveCD after seeing those excellent screenshots.  It looks great and newbie-friendly.  But the browser returns me a page from my ISP with instuctions on how to get PPPoE works in Windows and just windows.  I am stuck.

---

### Post by mr_niceguy on 2005-12-08
[QUOTE=billyswong]In windows, I can install ras-PPPoE and everything afterward is easy.  Why can't Linux do something similar?[/QUOTE]

[mini-rant]Oh, **Linux** is not to blame here, **Ubuntu** is. Fedora is great with DSL and dial-up. This is simply an issue Ubuntu appears to have relegated to the "unimportant" pile. Apparently every man, woman and child on this planet who doesn't use a router is a second class citizen. There is simply no way the good engineers at Ubuntu couldn't include the same kind of simple interface Fedora uses - especially since it is OPEN SOURCE.[/mini-rant]

All in all, Ubuntu is very good and the developers get my sincere kudos but this detail is disappointing.

---

### Post by mr_niceguy on 2005-12-12
[QUOTE=mayonesiac]hi, i'm completely new to linux and have just installed ubuntu. could someone please walk me through with setting up a pppoe connection? during the ubuntu instalation i chose not to configure the network settings[/QUOTE]

OK, I realize I vented on the user-friendliness problem but never actually bothered to answer the question :)

Open up a terminal and:

```
sudo pppoeconf
```

It's very straightforward and good defaults are all given. When you're done go to "System > Administration > Networking" and select the device (usually ethernet) you use to connect to the internet. Click "Properties" and check the box which says "Enable this connection". If your provider uses DHCP you should also select "DHCP" under the "Configuration" option. Click "OK". It may take a while but just wait it out. Then back at the main "Network Settings" dialogue you can set the "Default gateway device" to match the device you're using to connect. Click "OK" again and you should be set.

One more thing...

If you want the connection to start at boot you will need to select that option when it is presented by "pppoeconf". If that doesn't work you will also need to 

```
sudo gedit /etc/init.d/bootmisc.sh
```

before the final 

```
: exit 0
```

Add the line

```
pon dsl-provider
```

Now, I ask you, what could possibly be more newb-friendly than that? :confused:

---

### Post by DeLfynu on 2006-04-19
I still lose my pppoe connection when I restart my computer :( ](*,)  what sould I do?

---

