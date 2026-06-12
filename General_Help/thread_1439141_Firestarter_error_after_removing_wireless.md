---
title: "Firestarter error after removing wireless"
date: 2010-03-25
forum: General Help
---

### Post by NertSkull on 2010-03-25
So I had my desktop connecting via wireless to my home network.  And I had firestarter helping with the firewall, and it was running using the wlan0

But now I have connected that machine by ethernet to the internet and I have taken out the wireless card.  So there is no more wlan0 connection.

But now firestarter doesn't recognize my eth0 connection.  How do I fix this.  Should I just uninstall and reinstall firestarter?  I feel that there should be a way to configure it to realize the firewall should be on eth0 now instead of wlan0. 

What am I doing wrong?  Thanks all.

---

### Post by NertSkull on 2010-05-06
Anyone? I tried uninstalling and reinstalling firestarter, but I get the same.  I don't think it removed the config files.

I'm sure this has to be a simple fix

---

### Post by NertSkull on 2010-05-15
one more time, cause I really don't want to re-install the entire system.....

---

### Post by byStanderone on 2010-05-15
...have you also reconfigured your network connection so as to update your hardware changes? just wondering.

---

### Post by NertSkull on 2010-06-16
I'm not sure I know exactly what you mean by updated it.

The wireless card is totally removed, not even in the same room :)  And it doesn't show up in scans.

I've removed EVERY file containing the word firestarter in the name.  I've then reinstalled firestarter and configured it to work on eth0

But when it starts, it still gives me the error that it can't start the firewall because wlan0 is not found.

My iptables (which I don't fully understand) also appears to be empty.

Thanks for the help all.  I'm totally lost with network stuff.

---

### Post by byStanderone on 2010-06-18
...am i missing something? are you saying that you have configured firestarter by going thru its gui >status>program preferences>network settings > internet connected network devices ...and that your ethernet is not included in the dropdown choices? normally you'd find your ethernet device listed on the dropdown choices.

---

### Post by NertSkull on 2010-06-23
No my eth0 IS there.  But when I go through and select it.  It pops up a message saying it could not be started.  And that the reason is because it can't find wlan0.  And then it turns off the firewall (or keeps it off I should say).

Its like it won't let me change to eth0.

Is my best hope just to figure out iptables?  I've always avoided that, but perhaps its time I bite the bullet and do it manually.

---

### Post by bodhi.zazen on 2010-06-23
> **NertSkull said:**
> No my eth0 IS there.  But when I go through and select it.  It pops up a message saying it could not be started.  And that the reason is because it can't find wlan0.  And then it turns off the firewall (or keeps it off I should say).

Its like it won't let me change to eth0.

Is my best hope just to figure out iptables?  I've always avoided that, but perhaps its time I bite the bullet and do it manually.

If you *must* stay with firestarter, purge it and reinstall:

```
sudo apt-get purge firestarter
sudo apt-get install firestarter
```

If you would like an alternate, try gufw

With all that in mind, ufw is likely sufficient.

Learning iptables never hurts either.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by NertSkull on 2010-06-25
So I tried that all (again) and still to no avail.  I can purge firestarter.  Re-install it, and it still won't start, saying that the wlan0 can't be found.  And all ports stay open.

I can install gufw, there's no NEED to stick with firestarter.  I guess its more I want to figure out what is going on.

There HAS to be some sort of configuration file left over somewhere that I can delete.  Its just really weird to me that I can't completely remove firestarter.

I guess I'm happy going with gufw, but I'd like to really remove all of firestarter first.  And as it is, there must be something left behind.

---

### Post by bodhi.zazen on 2010-06-25
> **NertSkull said:**
> So I tried that all (again) and still to no avail.  I can purge firestarter.  Re-install it, and it still won't start, saying that the wlan0 can't be found.  And all ports stay open.

I can install gufw, there's no NEED to stick with firestarter.  I guess its more I want to figure out what is going on.

There HAS to be some sort of configuration file left over somewhere that I can delete.  Its just really weird to me that I can't completely remove firestarter.

I guess I'm happy going with gufw, but I'd like to really remove all of firestarter first.  And as it is, there must be something left behind.

```
dpkg --listfiles firestarter

locate firestarter
```

manually delete the files.

The sourec code for firestarter is no longer maintained. So while it is packaged and available in the repositories, there is no way to fix any potential bugs such as you are experiencing short of programing firestarter yourself.

So as painful as it may be, time to consider learning gufw, wireshark, ufw, iptables, shorewall, snort, psad, or any of the numerous alternates to firestarter depending on your needs.

---

### Post by NertSkull on 2010-06-26
well, thanks for all the help.  still none of the above works.

its really not a huge deal, I've installed gufw already.  And read through some tutorials on iptables and I have my firewall back up and working fine.

just really weird that if I re-install firestarter, it still finds wlan0 as the only connection.

but oh well, I knew the code wasn't really being worked on anymore, so I'm happy to chalk it up to a mystery I'll never solve. 

no biggie, thanks again everyone for the help.  in the end it was a good thing, because iptables is much more flexible and specific than what I had.  I like it.

---

