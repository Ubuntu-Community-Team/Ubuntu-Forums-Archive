---
title: "Extra network showing!"
date: 2012-08-02
forum: General Help
---

### Post by johnnypict on 2012-08-02
A bizzare thing is happening.

Had some issues with Talk Talk broadband.
Thought my wi-fi or pc had been hacked and someone was draining my broadband.

Long story short they sorted it by raising the line to 15db.
All working well until this evening when it is on a go slow non connecting mode again and I also spot a Netgear option showing in my list of available wireless networks!!! Ubuntu 12.04

Is this common. I know my ipad shows available wi-fi networks when it is near then but I wasn't aware that it would show in ubuntu desktop. Seen this once before.

Anyone share any thoughts.

---

### Post by audiomick on 2012-08-02
> **johnnypict said:**
>  I know my ipad shows available wi-fi networks when it is near then but I wasn't aware that it would show in ubuntu desktop.

Yep, it does. The network jigger will show you any networks available. I can see six at the moment. 

You also mentioned a "go slow" phase. If there are a lot of access points and or machines with active wireless around, then it is possible that this will slow down your connection. It is a little like too much traffic on a road.

---

### Post by SeijiSensei on 2012-08-02
Try changing your router to use a different radio channel.  If you run the command "sudo iwlist wlan0 scanning" you'll see a list of neighboring access points and the channels they use.  Most routers are factory-configured to run on channels 3, 6 or 11.  I'm the only one in my neighborhood on channel five.

---

### Post by johnnypict on 2012-08-03
Thanks guys.
Can't change the router settings at the moment as one of my issues is that when I type in 192.168.1.1 the browser doesn't find he router.

If I type in other addresses i.e the printer on .4 it finds it easily as well as the server address on .2 but wont find .3

Since posting I'm waiting on talk talk coming back on that point with then I'll try it.

Thanks.

J

---

### Post by plucky on 2012-08-03
> **johnnypict said:**
> Thanks guys.
Can't change the router settings at the moment as one of my issues is that when I type in 192.168.1.1 the browser doesn't find he router.

If I type in other addresses i.e the printer on .4 it finds it easily as well as the server address on .2 but wont find .3

Since posting I'm waiting on talk talk coming back on that point with then I'll try it.

Thanks.

J

Are you sure that address is right?

Mine is 192.168.0.1

What is the Make and Model of your router?

---

### Post by johnnypict on 2012-08-03
Its 192.168.1.1 Plucky.
Been logged in recently.
We'll see what talk talk come back with.

---

