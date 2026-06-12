---
title: "Ettercap arp:remote not working only shows https pages in firefox"
date: 2011-01-27
forum: General Help
---

### Post by jaspen on 2011-01-27
I am using unbuntu as root.  I've made all the edits to my etter.conf file as follows:

[privs]
ec_uid = 0
ec_gid = 0

and:
remote-browser = "firefox -remote openurl (http://%host%url)"

I also turn on ipTables.  I then start my attack as follows:

ettercap -T -Q -M arp:remote -i eth1 /client-ip/ // -P remote_browser
[COLOR=#0000FF]
echo 1 > /proc/sys/net/ipv4/ip_forward[/COLOR]

[COLOR=#0000FF]ettercap -T -Q -M arp:remote -i eth0 /target_ip/ /gateway_ip/ -P remote_browser[/COLOR]

My problem is Firefox only shows https:// pages and not regular pages like google.  I'm stumped.  I have no clue why.  I've tried other versions of linux.  Different computers and still the same result.  I'd really love some suggestions.  If I turn quiet off I see in my terminal all the traffic.

---

### Post by jaspen on 2011-01-31
I turn -Q off and see all the activity however FireFox only shows https secure pages. I'm using this on my own network watching the activity of my children as a concerned parent. Would also like to educate our community. Thanks.

---

### Post by bsinger74 on 2011-03-10
I'm confused on this one as well.  It would seem to me that the syntax for 'firefox -remote' no longer works correctly.  I have tried various configs:
  

[LIST]
[*]remote_browser = "firefox -remote= openurl http://%host%url"
[*]remote_browser = "firefox -remote openurl(http://%host%url)"
[*]remote_browser = "firefox http://%host%url"
[/LIST]
And others, in addition I did set the uid to 0 above and am launching firefox in the same uid as when running ettercap.

Is there a log file for firefox or ettercap that could point out what the error is?  Anyone know the correct syntax to get Ettercap's remote_browser plugin working for firefox?

Many Thanks!

---

