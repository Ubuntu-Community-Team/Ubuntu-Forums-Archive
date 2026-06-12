---
title: "Really weird internet bug"
date: 2009-07-03
forum: General Help
---

### Post by ashen on 2009-07-03
Hi all,

I am currently encountering a really weird internet bug and I wondered if any one had any ideas to solve it.  I have recently upgraded my laptop to Jaunty (with a fresh install) from Intrepid and now cannot access some websites (notably [www.metoffice.gov.uk](www.metoffice.gov.uk) to check the weather!).  

The weird thing is that on my desktop machine (sat right next to my laptop) that is still running Intrepid and is on the same network I have no problems!  I tried installing Opera in case it was a Firefox problem, but that seem to have made no difference.

Does anybody have any idea why this might be?

Cheers,

ashen

---

### Post by blueridgedog on 2009-07-03
What error do you get?

How is the laptop connected to the Internet?

If it is wireless, can you try a wired connection and verify that it is not a wireless issue?

---

### Post by ashen on 2009-07-03
I don't really get any error - it just says "loading ..." for ages!

I've tried it both wired and wireless and the problems are the same.  However, I have a suspicion that it may be to do with the fact Jaunty has ipv6 enabled by default (with no way to turn it off ...).  If i do:

```

dig AAAA www.metoffice.gov.uk

```

I get the reponse:

```

;; Warning: Message parser reports malformed message packet.
...

```

Whereas:

```

dig A www.metoffice.gov.uk

```

gives the correct response (I think!).

I have tried disabling ipv6 in firefox using about:config

```

network.dns.disableIPv6; true

```

which seems to occasionally work (weirdly) - but not consistently.  I have no idea why.

Any more advice welcome!

Cheers,

ashen

---

### Post by blueridgedog on 2009-07-03
Try:

```
sudo echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```

Then, restart networking:

```
sudo /etc/init.d/networking restart
```

The suggestion is from this thread:

[http://ubuntuforums.org/archive/index.php/t-1065469.html](http://ubuntuforums.org/archive/index.php/t-1065469.html)

But, reading further down, some people reported problems with the fix.

---

### Post by ashen on 2009-07-03
Thanks for your help.  Unfortunately this didn't work for me, and when I restarted the computer "disable_ipv6" was set back to zero. :(

It appears my only option at the moment is to use the other computer for the met office website!

Doh!

Cheers,

ashen

---

### Post by unutbu on 2009-07-03
Is /etc/resolv.conf on the laptop and desktop identical?

---

### Post by blueridgedog on 2009-07-03
Can you disable ipv6 on your router?

---

### Post by ashen on 2009-07-03
> **unutbu said:**
> Is /etc/resolv.conf on the laptop and desktop identical?

They're not identical - on the desktop there are two name servers listed that are not on the laptop.  How are the name servers set?

> 
Can you disable ipv6 on your router? 


I don't think so - I'm not sure my router actually does ipv6.  It's a Asus WL500g.

Thanks,

ashen

---

### Post by unutbu on 2009-07-03
On the laptop, type
```

gksu gedit /etc/resolv.conf
```

This will open gedit (the text editor) with root privileges.
Type in the two lines listed in the desktop's resolv.conf that are missing on the laptop's resolv.conf.

Save and exit. I think the changes take effect immediately.

Then try the dig commands again.

---

### Post by ashen on 2009-07-03
> **unutbu said:**
> On the laptop, type
```

gksu gedit /etc/resolv.conf
```

This will open gedit (the text editor) with root privileges.
Type in the two lines listed in the desktop's resolv.conf that are missing on the laptop's resolv.conf.

Save and exit. I think the changes take effect immediately.

Then try the dig commands again.

Weirdly everything now seems to work.  I haven't actually changed anything, but Opera and firefox now both load the webpage ok.

I'm still confused as to why it wasn't working and I'll post here if it goes wrong again.

Thanks for all the help!

ashen

---

