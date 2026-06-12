---
title: "internet sporadically stops working"
date: 2012-04-24
forum: General Help
---

### Post by gibxam on 2012-04-24
Hello citizens of the world,

Hope you are all doing well. For the past several months my computer laptop will sporadically disconnect from the internet when i am home. It still says that it's connected but none of the applications will be able to perform (example: internet browser or bittorrent clients). I say sporadically because this will only happen at random times during the day or night. Also if I am streaming music my computer may stay connected for one to two hours and then lose connection. When this happens if I disable my wireless card and then re-enable it the internet will work fine for maybe another 5 to 10 minutes and then I have to do the same thing again. The weird thing is this only happens on my home internet connection, never on the campus provided wifi, nor if I tether to my phones wifi. To make matters more confusing none of my other room mates have this problem, who all use mac osx.

At first I thought it was our router, but it can't be since no one else has this problem in my house. Then I thought it was my wireless card, but its only at my house that I have this problem. The last hypothesis I have is that it has something to do with the way Ubuntu connects me to the router? I'm not sure though, I'd really appreciate anyone's input, let me know if I should post any network diagnostics stuff.   

thanks for your time

max

---

### Post by Spaceman Spiff on 2012-04-24
Next time it happens, ping your router, see if it's a routing problem or a connection problem.

---

### Post by jadtech on 2012-04-24
it could be your router never say never but more likely is that  even if your  ISP says your internet bandwidth is unlimited there is truly no such thing and most providers today are throttling your connection based on what  you are doing less important things can and are automatically throttled to a crawl making it as if you are almost not connected..

things like at IP addresses of that share illegal music and video files torrent servers know porn site steaming servers things that suck up tons of bandwidth slowing down the rest of the system for others using there system and business  clients ..
if nothing has changed on you computer you have a good router your modem has been fine you can bet it ISP related ..

---

### Post by jadtech on 2012-04-24
if you use gobs of bandwidth and find you always have problems connected at hom not others chances are 99.99% its provider related most specially cable broad band today even if they claim to be unlimited box all user into  roughtly 40 gigs of bandwidth a month  and they will throttle you when you start uploading and down loading streaming ton of music and videos or have a torrent program or server running..

they can and slow any user on there system down slower then any dailup connection  who is using bandwidth above normal home use at certian times of the day , here where I am cable  is $30 a month allowed 40 gig of useage for that over that its $2 a gig up to $150 worth then your cut off unless you call to pay your bill and buy more paid for in advance ..

and yes  today some of the problem people are having with flash foryou tube and such are related to this because  there is a minimum internet speed required for flash to work correctly ..

---

### Post by wildmanne39 on 2012-04-24
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by techsupport on 2012-04-24
> **gibxam said:**
> Hello citizens of the world,

Hope you are all doing well. For the past several months my computer laptop will sporadically disconnect from the internet when i am home. It still says that it's connected but none of the applications will be able to perform (example: internet browser or bittorrent clients). I say sporadically because this will only happen at random times during the day or night. Also if I am streaming music my computer may stay connected for one to two hours and then lose connection. When this happens if I disable my wireless card and then re-enable it the internet will work fine for maybe another 5 to 10 minutes and then I have to do the same thing again. The weird thing is this only happens on my home internet connection, never on the campus provided wifi, nor if I tether to my phones wifi. To make matters more confusing none of my other room mates have this problem, who all use mac osx.

At first I thought it was our router, but it can't be since no one else has this problem in my house. Then I thought it was my wireless card, but its only at my house that I have this problem. The last hypothesis I have is that it has something to do with the way Ubuntu connects me to the router? I'm not sure though, I'd really appreciate anyone's input, let me know if I should post any network diagnostics stuff.   

thanks for your time

max

[gibxam]("http://ubuntuforums.org/member.php?u=786090")

I bet it is your leased DSL connection on the router losing the leases periodically. On campus you probably have a dedicated Ethernet "Static IP" configuration going on. They never change.   I've seen this before. Update your Ubuntu network configuration from Dynamic IP to a Static IP configuration and call tech support for your router to have them walk you through the process of getting the router configured so you will have the settings you need to configure your Ubuntu network manager to connect to your router with a Static IP address.  It would take forever on this forum to show you how to do that. So I am not going to bother with that. Tech support is free through your router manufacture (usually?) and they can help you configure a static IP on ubuntu from that make/model router. 

Bottom line is, you are using a dynamic IP address at Home. The router updates the leases periodically from whatever ISP you are using to connect to the internet.. It periodically changes the WAN IP. And assigns you the same LAN IP.  Sometimes that can take a few minutes depending on your ISP and when they perform nightly updates. You need to configure a static IP on Ubuntu.  And you probably would want to configure port forwarding on the router manually if you are torrenting too while you in the process of updating from a dynamic IP to a static ip connection in network manager. Port Forwarding is set up in the router itself, and again, tech support from your router company can walk you thorugh that process for your make/model router.  Worse comes to worse, forward this message to your ISP and have them tell if this might be going on or not.  It happens in windows too, but it is less noticeable for some reason I'm not sure why.

:guitar:

---

