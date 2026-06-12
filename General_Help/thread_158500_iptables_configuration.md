---
title: "iptables configuration"
date: 2006-04-11
forum: General Help
---

### Post by HereInOz on 2006-04-11
I am new to Ubuntu.  

I have noticed that the default firewall configuration in Ubuntu stealths all the ports, but the machine still responds to pings.

I am not particularly good with iptables, so I wonder if anyone can give me the clues on how to set up iptables to drop ICMP packets.  I have had a look through the how-to's in /usr/share/doc/iptables, but can't make a lot of headway there.

Hope you can help.

Cheers,

Alan

---

### Post by Ramses de Norre on 2006-04-11
sudo apt-get install firestarter
It's a gui frontend to edit iptables.

---

### Post by frodon on 2006-04-11
My guide isn't completely finished (90% done) but you should have a look to it : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

Thanks to for any kind of feedback.

Firestarter is really good for beginners it's painless to use/install, but it's not as secure than a custom iptables script i think.

---

### Post by HereInOz on 2006-04-11
I reckon I need to download Firestarter, but when I go to the firestarter site, it directs me back to the ubuntu site, with no apparent place to actually download the file.  When I follow the directions to add extra repositories, the file I need to open, (sources.list) is completely blank, and doesn't look anything like the example given.

All I get is the message "can't find firestarter" when I run apt-get as you suggest.

Any thoughts?

Alan

---

### Post by HereInOz on 2006-04-11
Thanks for the link to the guide - I will have a look through it and see what I make of it.  Good for the education - many thanks.

Alan

---

