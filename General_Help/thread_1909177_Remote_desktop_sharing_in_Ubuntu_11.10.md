---
title: "Remote desktop sharing in Ubuntu 11.10"
date: 2012-01-14
forum: General Help
---

### Post by stefangr1 on 2012-01-14
Hello,

I just installed Ubuntu 11.10, so I'm currently exploring a completely redesigned Ubuntu.

However, remote desktop sharing isn't yet working (because the screen doesn't refresh). In previous versions, this problem occured when visual effects were enabled in the appropriate panel.

Does anyone know how to fix it in Ubuntu 11.10?

---

### Post by bluexrider on 2012-01-14
I use 11.04 and have no issues with Remmina

Can VNC or RPD whichever

---

### Post by stefangr1 on 2012-01-15
> **bluexrider said:**
> I use 11.04 and have no issues with Remmina

Can VNC or RPD whichever

I use 11.10 and I *have* issues. If I connect with either VNC4 client or the build in remote desktop client of OSX Lion, I can start a session but the screen doesn't get refreshed. When I press a key or click something, it does actually do something when I look at the system itself, but I can't see that on the remote desktop client until I reconnect.

As said, that immediately reminded me of the fact that I had the exact same issue in Ubuntu 8.10, *once I turned on visual effects*. In previous versions, there used to be a configuration dialog where you could specify 3 levels of visual effects. I can't find it in 11.10.

So my question is basically twofold: (1) does anyone know how to fix the problem itself, or (2) does anyone know how visual effects can be turned off in Ubuntu 11.10.

---

### Post by overwheat on 2012-02-15
Hate to bump this thread, but i'm having this exact issue. I can connect with tightVNC just fine, but the screen doesn't refresh at all. I know i'm connected because on the my ubuntu machine it shows the notification that I am connected, and I can see the mouse move and everything, but on my windows machine I have no visual response to the actions i'm doing.

---

### Post by AlanR8 on 2012-02-15
Had this issue trying to connect to my 11.10 "server" from my 12.04 laptop. Workaround was to start the 11.10 machine in Unity 2D or Gnome. Screens then refresh and the application works fine now.

---

### Post by overwheat on 2012-02-15
That totally worked! Thank you!

---

### Post by AlanR8 on 2012-02-16
You're welcome

---

### Post by digitaltruth on 2012-02-29
I have noticed this is an issue while using the fglrx (ATI proprietary drivers). To get around this if you run the ATI Catalyst admin control program and enable the "tear free" option it resolved the issue for me immediately. :P

---

### Post by DonJuan4076 on 2012-03-28
ok so i am having the same issue here. Connecting from 11.10 to 10.10 (I know that it is time to upgrade waiting for 12.04) but anyway. I need to reconnect to see any changes. My 10.10 system has no extra effects... have yet to try the 2D login will do that tomorrow, in my 11.10 I have tried Gnome efects, no effects, Unity regular and 2D still unable to connect. 

I am just wondering if there truly is honestly no way to use the 3d or effects versions with remote desktop as stated before.

also my 11.10 is an acer aspire one... don't know it the netbook thing has anything to do with my problems

---

### Post by DonJuan4076 on 2012-03-28
I couldn't wait until morning. Ok so using 'no effects' on my host computer (not the viewing one) solved my problems.

BUT isn't there a way to set up a remote desktop on a computer that is currently using effects... there has to be a way

---

