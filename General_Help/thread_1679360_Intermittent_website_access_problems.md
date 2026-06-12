---
title: "Intermittent website access problems"
date: 2011-01-31
forum: General Help
---

### Post by atari_gods on 2011-01-31
My issue pertains to accessing websites through Firefox (or Chrome) on an Ubuntu-running laptop. Specifically when I try to access a website I have seen these symptoms: Connection Timed-Out messages, "Connecting to {address}..." freezes in the Status bar, loading of a webpage takes a few minutes and only results in the page's text being displayed and not in the webpage's format; it's just a page of text and links from the webpage. Some of these problems resolve themselves with a reload (i.e. webpage of text-only sometimes solves with this), or, after a period of time (30min to several hours) a webpage with load without issue when earlier it would time-out or freeze during connection. These issues have not been specific to any few websites, but to a random website at any time during my online access and surfing. There have been a few repeat offenders I can mention: Facebook (specifically when "Connecting to static.ak.fbcdn.net") and [www.pricewatch.com](www.pricewatch.com) (Connection Timed-Out message). I am fairly certain that these issues are local because I have tested access through a Windows machine using IE and FFx during the access problem and have loaded the webpages without problem. I have had problems with my ISP's DNS servers in the past so I currently use the public DNS's through Google. Figured this out through searching the forums about a year ago. I have asked my ISP for assistance or suggestions to solve my problem, but they are unwilling to help users of non-Windows or non-Mac OS's ("Oh, your using Linux. It must be your system that's causing the problem. Our servers are working fine.")

Machine specifics:
Ubuntu 10.04 (updated regularly)
Firefox 3.6.13 w/NoScript extension (and I do use it, but allow sites when a problem site occurs, I have also tried disabling NoScript and accessing pages to no change in access problems)

This is my first post to Ubuntu Forums, so please be nice. Any other information just ask. Additionally this problem has been going on for at least a year, but lately it has gotten worse and is restricting my web access more each time.

---

### Post by atari_gods on 2011-03-05
*bump*

I found [a post]("http://ubuntuforums.org/showthread.php?t=1488765") related to my problem. I hope it can shed some light on my issue and perhaps lead to some answers.

---

### Post by Habitual on 2011-03-05
I've had to restart my network several times recently just to get to some sites also.

Strange.
Firefox 3.6.13 (NOT from REPOs) and a few add-ons. NoScript isn't one of them.
LinuxMint 10
2.6.35-22-generic-pae

Suggestion:
When your ISP says "Oh, your using Linux. It must be your system that's causing the problem. Our servers are working fine."
**Ask for the next level of support and remind them that the S is for SERVICE**

That is a Level 1 (entry level) answer. 
Unacceptable since about > 65% of the computers on the 'net run Unix or a variation of it.

---

### Post by MIJ-VI on 2011-03-05
Re finding the fastest DNS servers: I've used [namebench]("http://www.talkbass.com/forum/f34/malware-http-results-google-analytics-com-malware-677892/index2.html#post9592754") under Ubuntu 10.04.x and 10.10.

Other causes of Internet slowdowns can include:

[load-balancing]("http://ubuntuforums.org/showpost.php?p=9768039&postcount=8") schemes used by server farm-operating, web hosting companies like Akamai technologies and amazonaws.com (Amazon Web Services).

Denial of Service (DoS) or Distributed Denial of Service (DDoS) attacks against the server or network of servers which one is attempting to connect to. The hacktivist group Anonymous and a lone hacktivist named th3j35t3r (The Jester) are currently using these types of attacks as part of the [wide-ranging cyber war]("http://www.talkbass.com/forum/f34/anonymous-hacktivists-become-web-vigilantes-743419/") they're involved in.

---

### Post by atari_gods on 2011-03-07
Thank you for the responses folks.

It would seem that today after a few new updates (Firefox, Avahi?, and a few others) that previously inaccessible websites or ones with timed-out connections are now loading as normal. So things work for now, but how long will it last? I'll have to watch for a pattern in future problems.

Thanks again.

---

### Post by randumnumber on 2011-03-09
I am having this problem also. My laptop decided it didnt like its boot partition anymore and i had to reinstall. After the reinstall I am having problems with both firefox and chrome. The statusbar says "waiting for 'insert name of website here'" and it takes forever to load. It has been google analytics and when loading facebook it takes forever to load the profile pictures. 

I had this problem before on a 64bit system. None of the regular fixes worked (disable IPV6 in grub and firefox, change DNS server). I found a very obscure fix that involved editing a file somewhere. This was 6 months ago, and i unfortunately don't remember what it was. 

This is a very common problem and the fix that i found didn't involve ipv6 or dns servers.

My bandwidth is fine, i can download files no problem. All the other computers on my network are running fine on the internet. My x box runs fine. 

If you find a good fix for this please let me know. TNX

---

### Post by bob6 on 2011-09-12
Turning off timestamps should work. ```
echo 0 > /proc/sys/net/ipv4/tcp_timestamps
``` You need to make sure this setting holds on reboot.  Maybe /etc/sysctl.conf file add net.ipv4.tcp_timestamps = 0 If you use firestarter as a firewall there is a bug in firestarter that stalls or timesout on webpages intermittently.     [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

