---
title: "hp-setup cannot find wireless printer"
date: 2010-04-13
forum: General Help
---

### Post by trubliphone on 2010-04-13
Hello.  

My Kubuntu laptop is unable to detect my wireless HP OfficeJet J6480.  As with most computer problems, everything was working fine yesterday and I didn't change anything.  Prior to this, from time to time, it would complain that the printer was not connected.  But I would simply run hp-setup again and re-install it.

This problem is more serious though.  hp-setup cannot detect any wireless printers at all.  And, when I look at my printer configuration from the KDE  Control Module there is nothing there (previously cups-pdf, j6480, and j6480_fax were all there).

I  have upgraded my version of hplip (this failed several times until I uninstalled some libxml-sax-perl packages).  According to the printer, it is connected to my wireless router.  But still whenever I try running hp-setup, I am unable to detect I am running Kubuntu.

Any ideas on what to try?  

Thanks.

---

### Post by Untitled_No4 on 2010-04-13
Did you try to ping the printer?

In case I'm speaking Chinese: find the network settings on the printer and the find the printer's IP address. Then in Konsole ping this address. Assuming your printer IP address is 192.168.168.60 you need to do the following:
```
ping 192.168.168.60
```

If you don't get a reply then your computer can't see the printer and the problem is somewhere between the router and the printer.

Otherwise, here are some things I would try:
1. Turn the printer on/off. Sorry if it's obvious and you tried it already.
2. Remove hplip, clean apt database, reinstall hplip.
3. When you run hp-setup choose the second option (Network/Ethernet/Wireless network and click on Show Advanced Options, tick Manual Discovery and input the printer's IP address manually and see if this helps.

---

### Post by trubliphone on 2010-04-13
Thanks for your suggestions.

The IP address given for the wireless printer is 192.168.1.3.

When I type 'ping 192.168.1.3' I get the following response:

PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
...

I'm not sure why it switches from 192.168.1.3 to 192.168.1.2, but at any rate it is unreachable.

Regarding your other suggestions, I had already tried suggestions 1 & 3.  I've just tried suggestion 2 and it had no effect.

---

### Post by trubliphone on 2010-04-14
Hmmm... I guess something I did worked.  The next day, having rebooted the laptop it was able to recognize the printer.  It was already listed in the KDE control module.  And setting it up via hp-setup worked fine.

---

### Post by trubliphone on 2010-04-14
However, although I could print test pages from hplip, KDE printer config, and CUPS, I couldn't actually print any documents.  After much scratching of the head I noticed the following in the CUPS error logs:

E [14/Apr/2010:07:27:45 -0700] Syntax error on line 10 of printers.conf.

And when I tried to print from lpr I got the following error:

lpr: Bad job-sheets value ""!

Doing a search on the internet led me here [[https://bugs.launchpad.net/ubuntu/+source/kdeadmin/+bug/403169]](https://bugs.launchpad.net/ubuntu/+source/kdeadmin/+bug/403169]), which showed me how to edit /etc/cups/printers.conf and restart cups.

This worked fine.

Hooray!

---

### Post by trubliphone on 2010-04-27
An update...

After working fine for a while, my printer could not be detected again.  I tried all of the above steps and nothing happened.

It turned out that I had to change the channel that the router was broadcasting on.  Now everything is back to normal.

Any idea why this sort of problem occurs?  What would making a working configuration stop working because of problems with the channel?

Thanks.

---

### Post by MattJG on 2010-11-14
i turned my Photosmart 4580 off and left it 20secs, turned it back on and it worked.

@[Untitled_No4]("http://ubuntuforums.org/member.php?u=648191"): thanks for the reminder! i had truble with the printer on one of our windows 7 systems and the number of times it been off and on again ive forget. then i forgot to try it for Ubuntu. i should know better. lol







edit: wow. i joined Oct 2009 and this is my first post. :???: what a noob.

---

