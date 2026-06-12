---
title: "Ubuntu 10.04 Wireless Connection Goes Out"
date: 2010-05-06
forum: General Help
---

### Post by jschille on 2010-05-06
After upgrading to 10.04 my wireless connection constantly goes out while in Ubuntu and not sure if it is related or not, but it takes an abnormally long time to load webpages (even after changing those true and false's in firebox's about:config) now as opposed to pre 10.04.

---

### Post by jschille on 2010-05-07
/bumping for love

---

### Post by jschille on 2010-05-07
No one else is having this problem with their wireless internet?

---

### Post by duble08 on 2010-05-08
i also have this problem - i have a compaq presario laptop, model CQ60-215dx - i was originally running 9.10, which worked awesome until an update that was released on 4/29/2010, which for some reason completely halted the functionality of my wireless.  I couldn't figure out how to undo the update, so i figured since 10.04 had just came out, i might as well give it a try.  10.04 seems to run pretty good, and my wireless works again, but it seems really shady.  i'm also kind of confused about my wireless light on my laptop, which is also a button to turn on and off the wireless.  in version 9.10, the light was always orange - it has two lights, orange for off, blue for on - even though it always showed orange, it worked (prior to update).  my guess is a driver.  however, now with 10.04, it flickers back and forth between orange and blue (kind of looks like maybe it's blinking with network activity?)  

But back onto topic, since 10.04 has been installed, it seems like my ability to do multiple things on the net have been shot.  I used to be able to run torrents and browse the web, and play video games at the same time, with no latency, no issues.  now i have to pause my torrents (i've even tried limiting connections to save on bandwidth) in order to browse the web properly, and sometimes that's not even enough.  sometimes web pages are real snappy, and pop up immediately, and other times i'll click a link, and be sent to page that says it can't be found - if i keep refreshing, or click the link multiple times threw out the waiting time, it'll eventually open. it shouldn't be an issue with my provider, as my roommate runs winblows 7 and has no issues, and my isp is a 20mb/sec cable line. i don't know what's causing the issue, but like the above poster, if there's a fix, i'd love to know about it... please let us know if you guys know a way to correct it, or if you need more info about my machine or whatnot.

Thank you!

---

### Post by duble08 on 2010-05-11
so I've noticed the problem isn't necessarily the wireless turning on and off, but web browsing seems to do so (if that makes sense? maybe a protocol freezing up for some reason?).  I'm only coming to this conclusion by observing certain behaviors, such as:

- I play WOW - even though web pages will stall, and fail to load, i stay connected to the game server.  however, i do experience latency spikes when this happens.

- on pidgin, whenever i have a web page stall or fail to load, my Facebook account disconnects... the other services (aim, msn, yahoo, google talk) all stay connected. i cannot reconnect to facebook until the web pages begin to function again.

- my torrents in deluge will continue to go when the web pages fail.  my original thought was that the torrents were hogging to much bandwidth, thus causing stalls and failures, but the issues happen even if i'm not running any torrents, and if deluge is completely shut down.  however, the issue seems to occur more frequently if i have downloads going, but does not seem significant.

ideas?

---

### Post by atulkakrana on 2010-08-07
Same **** here..no relief...my expertise in linux fetch no purpose...bumped by problem..No solution till date

---

### Post by dphaynes on 2010-08-21
Same thing here, desktop system running 10.04 server that ran very reliably under 9.10 and Windows XP.  There doesn't seem to be any rhyme or reason to when it dies, it simply stops working. 

sudo /etc/init.d/networking restart 

...always gets it working again, however it's a pain in the *** to get to the console. I normally manage it through Webmin.

It's possible that it only happens if I don't access the computer for more than 3-4 days.

I definitely don't have any power saving modes configured in the BIOS but I don't know what places to check on Ubuntu to see if the wifi adapter is somehow configured to power down after a few days. 

FWIW it's a Gigabyte ES3 motherboard and a USB wifi adapter (Trendnet TEW424ub) and the hardware LAN adapter is disabled. 

If I access the server every day it seems like it works okay (not positive) Seems like if I don't access it for several days it will be dead until I restart networking.

---

### Post by ngrieb on 2010-08-21
I have never had this problem and am no expert at these types of problems, but I have heard that the wireless backports help the sketchiness of the wireless sometimes. But you probably have already tried this...

---

### Post by dphaynes on 2010-08-21
> **ngrieb said:**
> I have never had this problem and am no expert at these types of problems, but I have heard that the wireless backports help the sketchiness of the wireless sometimes. But you probably have already tried this...

Hopefully I did the right thing - I updated my sources and then did

sudo aptitude install linux-backports-modules-wireless-2.6.32-23-server

I rebooted it just to make sure everything is fresh.

I'll be accessing it frequently over the weekend but will try to leave it sit the first few days next week and see what happens.

Thanks for the info!

   Dan

---

### Post by dphaynes on 2010-09-01
Update: it's still working for me so far.  It has only been one week but so far so good. Keeping my fingers crossed.

---

### Post by dphaynes on 2010-09-13
> **dphaynes said:**
> Update: it's still working for me so far.  It has only been one week but so far so good. Keeping my fingers crossed.

Sigh. It crapped out yesterday. 

I had an ssh session open to it, it got closed with "Connection reset by peer" and it's not responding on any port (http:, svn:, webmin on 10000 etc.)

So it didn't fix the problem. 

If anyone has any other ideas I'd sure like to hear them. This is pretty unacceptable since I run the thing headless. The only way to get it going again is the power switch :(

---

### Post by glepore70 on 2010-09-13
I have regular trouble with my wireless card and one workaround I've used is to restart networking every 15 minutes via a cron job.  Not ideal, but it avoids having to hit the big button to get it going again.

---

### Post by dphaynes on 2010-09-13
> **glepore70 said:**
> I have regular trouble with my wireless card and one workaround I've used is to restart networking every 15 minutes via a cron job.  Not ideal, but it avoids having to hit the big button to get it going again.

Thanks, seems a bit like overkill but I may have to resort to it. Based on what I've found I may put a cron job in that greps for "**Withdrawing address record for 192.168.1.8 on wlan0." **and if grep returns 0 then go ahead and restart the networking.

The issue seems to be this:

Sep 11 18:50:07 fringe kernel: [561838.540040] No probe response from AP 00:11:95:9e:dd:62 after 500ms, disconnecting.

According to the threads I found by googling for that message it may be a long standing bug with both Linux and Ubuntu going back at least to 2006.

Apparently it affects quite a lot of people but since it has been attributed to various wifi adapters, various releases and various hardware configurations no one has actually addressed the root cause of the problem. They've got a whole bunch of different bugs/threads reporting it and none of them seem to be satisfactorily resolved. Since no one is marking them as duplicates of the same problem, I don't think anyone at Ubuntu realizes how frequent or widespread the problem is.

Since I have 4 other computers running various versions of Windows (7 x64, 7 x32, and XP Pro) that all get DHCP allocations from there and they've never hiccuped in 3 or 4 years running 24x7 it seems like it must be a Linux problem. 


In case it helps anyone, here is the relevant bit of /var/log/syslog for the day it quit with the problem bits highlighted:

Sep 11 18:38:18 fringe dhclient: DHCPACK of 192.168.1.8 from 192.168.1.1
Sep 11 18:38:18 fringe dhclient: bound to 192.168.1.8 -- renewal in 1482 seconds.
Sep 11 18:39:01 fringe CRON[27348]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 11 18:42:00 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 18:42:00 fringe dhclient: DHCPACK of 192.168.1.8 from 192.168.1.1
Sep 11 18:42:00 fringe dhclient: bound to 192.168.1.8 -- renewal in 1500 seconds.
[B]Sep 11 18:50:07 fringe kernel: [561838.540040] No probe response from AP 00:11:95:9e:dd:62 after 500ms, disconnecting.
Sep 11 19:03:00 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
[/B]Sep 11 19:04:07 fringe dhclient: last message repeated 6 times
Sep 11 19:05:15 fringe dhclient: last message repeated 4 times
Sep 11 19:06:16 fringe dhclient: last message repeated 6 times
Sep 11 19:07:17 fringe dhclient: last message repeated 7 times
Sep 11 19:08:18 fringe dhclient: last message repeated 7 times
Sep 11 19:09:01 fringe dhclient: last message repeated 6 times
Sep 11 19:09:01 fringe CRON[27500]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep 11 19:09:02 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:10:05 fringe dhclient: last message repeated 10 times
Sep 11 19:11:07 fringe dhclient: last message repeated 10 times
Sep 11 19:12:11 fringe dhclient: last message repeated 10 times
Sep 11 19:13:15 fringe dhclient: last message repeated 11 times
Sep 11 19:14:19 fringe dhclient: last message repeated 8 times
Sep 11 19:15:19 fringe dhclient: last message repeated 8 times
Sep 11 19:16:19 fringe dhclient: last message repeated 8 times
Sep 11 19:17:01 fringe dhclient: last message repeated 6 times
Sep 11 19:17:01 fringe CRON[27546]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 19:17:10 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:18:12 fringe dhclient: last message repeated 10 times
Sep 11 19:19:18 fringe dhclient: last message repeated 8 times
Sep 11 19:20:19 fringe dhclient: last message repeated 7 times
Sep 11 19:21:19 fringe dhclient: last message repeated 10 times
Sep 11 19:22:19 fringe dhclient: last message repeated 7 times
Sep 11 19:23:19 fringe dhclient: last message repeated 9 times
Sep 11 19:24:19 fringe dhclient: last message repeated 11 times
Sep 11 19:25:19 fringe dhclient: last message repeated 9 times
Sep 11 19:26:19 fringe dhclient: last message repeated 8 times
Sep 11 19:27:19 fringe dhclient: last message repeated 9 times
Sep 11 19:28:19 fringe dhclient: last message repeated 10 times
Sep 11 19:29:19 fringe dhclient: last message repeated 9 times
Sep 11 19:30:19 fringe dhclient: last message repeated 10 times
Sep 11 19:30:55 fringe dhclient: last message repeated 6 times
Sep 11 19:30:55 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:30:59 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:31:08 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:31:19 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:31:22 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:31:33 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:31:36 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:31:40 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:31:48 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:31:54 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:32:01 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:32:01 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:32:08 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:32:15 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:32:21 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:32:29 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:32:32 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:32:39 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:32:45 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:32:54 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:32:58 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:33:11 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:33:13 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:33:27 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:33:29 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:33:40 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:33:45 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:33:54 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:33:58 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:34:03 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:34:12 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:34:18 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:34:26 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 192.168.1.1 port 67
Sep 11 19:34:31 fringe dhclient: DHCPREQUEST of 192.168.1.8 on wlan0 to 255.255.255.255 port 67
Sep 11 19:35:36 fringe dhclient: last message repeated 8 times
Sep 11 19:36:39 fringe dhclient: last message repeated 8 times
Sep 11 19:37:47 fringe dhclient: last message repeated 8 times
Sep 11 19:38:19 fringe dhclient: last message repeated 4 times
[B]Sep 11 19:38:19 fringe avahi-daemon[748]: Withdrawing address record for 192.168.1.8 on wlan0.
Sep 11 19:38:19 fringe avahi-daemon[748]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.8.
Sep 11 19:38:19 fringe avahi-daemon[748]: Interface wlan0.IPv4 no longer relevant for mDNS.[/B]

---

### Post by dphaynes on 2011-01-11
In case it helps anyone, I never was able to resolve the problem but I did find a workaround. I moved it from a WEP network to a WPA2 network and it no longer seems to suffer disconnection issues. 

I had avoided WPA2 because there was no working documentation on how to configure it on Ubuntu. Lots of web pages/forum posts that claimed to make it work, but nothing that actually worked. Then I stumbled across this page:

[http://www.pantz.org/software/wpa_supplicant/wirelesswpa2andlinux.html](http://www.pantz.org/software/wpa_supplicant/wirelesswpa2andlinux.html)

There is only one flaw I've found in the instructions - that is the "-Bw" option to wpa_supplicant is invalid, it should be "-B" instead.

---

