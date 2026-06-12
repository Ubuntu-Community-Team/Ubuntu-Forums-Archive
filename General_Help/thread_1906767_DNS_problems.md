---
title: "DNS problems"
date: 2012-01-09
forum: General Help
---

### Post by MrKitty871 on 2012-01-09
so i got a new router today and under the dynamic dns tab there's only an option to select "www.dyndns.org" which you need to pay for. but my other router had a "www.no-ip.org" option. any ideas? i'm running Ubuntu server 11.10

---

### Post by topsites on 2012-01-09
Just run it default, and if it works, don't fix it.

---

### Post by duke.tim on 2012-01-09
Well you could always manually update your domains dns record as your ip changes. I have a dynamic ip and it seems to only change well it hasn't yet :D

You could consider installing new firmware on your router like tomato. It would be wise to be 100% sure that your router is supported and print out the instructions if you have never done it. (I have never done this myself)

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)
[http://en.wikipedia.org/wiki/Tomato_(firmware](http://en.wikipedia.org/wiki/Tomato_(firmware))

Tomato seems to support noip.com
[IMG]http://www.polarcloud.com/img/ssddns108.png[/IMG]

---

### Post by cmileto on 2012-01-10
just install and use ddclient to update your dynamic dns if your router doesnt support the one u need

---

### Post by MrKitty871 on 2012-01-10
i have a netgear cg3000d. idk if its supported

---

### Post by duke.tim on 2012-01-11
It doesn't looks like tomato doesn't supports your router

[http://en.wikibooks.org/wiki/Tomato_Firmware/Supported_Devices#Netgear](http://en.wikibooks.org/wiki/Tomato_Firmware/Supported_Devices#Netgear)

If the other suggestions didn't work then maybe try looking up if
these firmware support your router.

I did a quick search and didn't see any that actually supported your router, but maybe you will see something I didn't.


[LIST]
[*][DD-WRT]("http://api.viglink.com/api/click?format=go&key=9398b809c67d99979cb2b75250526730&loc=http%3A%2F%2Fwww.polarcloud.com%2Ftomato&v=1&libid=1326270560819&out=http%3A%2F%2Fwww.dd-wrt.com%2F&ref=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1906767&title=Tomato%20Firmware%20%7C%20polarcloud.com&txt=DD-WRT&jsonp=vglnk_jsonp_13262705818901")
[*][FreeWRT]("http://api.viglink.com/api/click?format=go&key=9398b809c67d99979cb2b75250526730&loc=http%3A%2F%2Fwww.polarcloud.com%2Ftomato&v=1&libid=1326270560819&out=http%3A%2F%2Fwww.freewrt.org%2F&ref=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1906767&title=Tomato%20Firmware%20%7C%20polarcloud.com&txt=FreeWRT&jsonp=vglnk_jsonp_13262706199102")
[*][HyperWRT Thibor]("http://api.viglink.com/api/click?format=go&key=9398b809c67d99979cb2b75250526730&loc=http%3A%2F%2Fwww.polarcloud.com%2Ftomato&v=1&libid=1326270560819&out=http%3A%2F%2Fwww.google.com%2Fsearch%3Fq%3Dthibor%2Bfirmware&ref=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1906767&title=Tomato%20Firmware%20%7C%20polarcloud.com&txt=HyperWRT%20Thibor&jsonp=vglnk_jsonp_13262706378013")
[*][OpenWRT]("http://api.viglink.com/api/click?format=go&key=9398b809c67d99979cb2b75250526730&loc=http%3A%2F%2Fwww.polarcloud.com%2Ftomato&v=1&libid=1326270560819&out=http%3A%2F%2Fwww.openwrt.org%2F&ref=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1906767&title=Tomato%20Firmware%20%7C%20polarcloud.com&txt=OpenWRT&jsonp=vglnk_jsonp_13262706487844")
[*][Tarifa]("http://api.viglink.com/api/click?format=go&key=9398b809c67d99979cb2b75250526730&loc=http%3A%2F%2Fwww.polarcloud.com%2Ftomato&v=1&libid=1326270560819&out=http%3A%2F%2Ftarifa.sourceforge.net%2F&ref=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1906767&title=Tomato%20Firmware%20%7C%20polarcloud.com&txt=Tarifa&jsonp=vglnk_jsonp_13262706691315")
[*][X-Wrt]("http://api.viglink.com/api/click?format=go&key=9398b809c67d99979cb2b75250526730&loc=http%3A%2F%2Fwww.polarcloud.com%2Ftomato&v=1&libid=1326270560819&out=http%3A%2F%2Fx-wrt.org%2F&ref=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1906767&title=Tomato%20Firmware%20%7C%20polarcloud.com&txt=X-Wrt&jsonp=vglnk_jsonp_13262706823606")
[/LIST]

---

