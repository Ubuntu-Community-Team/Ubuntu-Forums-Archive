---
title: "Web proxy (privoxy) connection fails daily"
date: 2010-10-07
forum: General Help
---

### Post by Emmental on 2010-10-07
I have been running privoxy on Ubuntu 10.04 64bit for the last few months as a web proxy for Firefox with no real problems until now. For about the last week, the proxy connection seems to fail at around the same time (almost) every day. Here are the symptoms:

- Firefox is no longer able to connect to the proxy server (the timeout message is from the browser, not the proxy server). I've also tested with Chromium with the same result.
- Web browsing works again if the browser's proxy settings are changed to direct connection.
- The Privoxy process appears to be still running.
- Restarting Privoxy does not fix the problem. The log file indicates that the proxy is running and listening on the correct port.
- Restarting the browser does not fix the problem.
- The only way I've found so far to fix the problem is to reboot.

This happens at around 8am pretty much every day (5 days out of 7 this week) and appears to correspond with Ubuntu's update manager checking for updates. This seems to me to be an unlikely cause but I have noticed two occurences where:

- I have installed an update then the proxy connection failed.
- Update manager has checked for updates (with no actual update done) then the proxy connection failed.

Again, I'm not convinced that update manager is the cause so this may just be a coincidence. I'm also not sure that it's actually Privoxy itself failing.

I don't really know where else to check, but I do plan to do the following when I get back home tonight:

- Turn on all logging options in Privoxy and try restarting and connecting.
- Disable update manager for a few days to see if this is the cause.
- Set up privoxy to serve other machines on the network and see if they can still connect when the failure happens.

Any other suggestions would be welcome as I'm running out of ideas as to what the cause is.

---

### Post by fredbird67 on 2010-10-11
I found this elsewhere on the web, so I thought I'd see if this helps:  Edit Privoxy's configuration file at /etc/privoxy/config, and look for the lines that say:

> # Set the listen address to 127.0.0.1:8118
listen-address 127.0.0.1:8118

Setting it to "listen-address localhost:8118" will NOT work!  It specifically needs to have the loopback IP address in there.

Once you've done that, then type

> sudo service privoxy restart

and all should be well.

Please let me know if this works for you or not.
Fred in St. Louis

---

### Post by Barriehie on 2010-10-11
> **fredbird67 said:**
> I found this elsewhere on the web, so I thought I'd see if this helps:  Edit Privoxy's configuration file at /etc/privoxy/config, and look for the lines that say:



Setting it to "listen-address localhost:8118" will NOT work!  It specifically needs to have the loopback IP address in there.

Once you've done that, then type



and all should be well.

Please let me know if this works for you or not.
Fred in St. Louis

Found about the same thing when I installed privoxy.  Sometimes 'localhost' gets resolved to an address other than 127.0.0.1.  I've got a chain going like browser >> squid >> privoxy >> tor and it took a bit to get it going.

---

### Post by Emmental on 2010-10-12
While poking around looking for information about this previously, I'd come across a few posts mentioning the localhost/127.0.0.1 change. I did give this a try (changing to 127.0.0.1 and restarting Privoxy) but it didn't fix the problem (no reboot at this stage).

I continued to test as per my first post:

- After turning all logging and restarting Privoxy, there was nothing appearing in the log to suggest anything was even trying to connect.
- Enabling the proxy for other machines and restarting it also had no effect and other machines were not able to connect (the listen address is now 192.168.0.2).
- I've disabled the update manager and rebooted.

So far, after the reboot to get things working again, the proxy has not failed for 4 days (now usable by everything on the network), but since I've changed 2 things (update manager and the listen address) I'll need to re-enable update manager again at some point and see if the localhost was the problem.

It may be that something does happen when update manager runs that confuses things when set to localhost, although changing it and restarting Privoxy didn't fix it - I still had to reboot. I also couldn't reproduce the problem by manually running update manager.

I agree though that it does seem like Privoxy is listening, but not on the right address when set to localhost. Why this would change suddenly and refuse to work again without a reboot is a bit strange. It's also odd that this has only just started happening after months of running fine as localhost with update manager enabled.

Anyway, I'll see how it goes for the next few days and enable update manager again. I'll post again when I get any information either way.

Thanks for the replies.

---

### Post by ffjjkk on 2010-10-15
Same problem with me!
Proxy connection with ubuntu is a nightmare.
Edit bash file can resolve some but not complete and not secure

[http://wwww.ubuntuforums.org/showthread.php?t=1590385](http://wwww.ubuntuforums.org/showthread.php?t=1590385)

---

### Post by Emmental on 2010-10-29
After enabling update manager last week, things have been fine until today. This morning, again, I am unable to make any connections to the proxy server, which appears to be running fine. Restarting the proxy server has no effect.

I'm now at a complete loss as to what could be causing this.

---

### Post by ffjjkk on 2010-10-30
Yup!

Edit apt.conf can make ubuntu update and install software but we must re-edit apt.conf after LinuxKernel updated.

Read more:

[https://help.ubuntu.com/community/AptGet/Howto#Setting](https://help.ubuntu.com/community/AptGet/Howto#Setting) up apt-get to use a http-proxy

---

### Post by Emmental on 2010-10-30
I think you've misunderstood the problem. I'm not trying to get apt to use a proxy. The problem is that the proxy connection regularly fails for browsers.

The reason I mentioned update manager was because it seems to happen around the time the auto-update happens.

---

