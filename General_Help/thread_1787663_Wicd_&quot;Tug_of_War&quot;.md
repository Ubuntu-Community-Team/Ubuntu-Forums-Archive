---
title: "Wicd &quot;Tug of War&quot;"
date: 2011-06-21
forum: General Help
---

### Post by jlacroix on 2011-06-21
Hello everyone, I am having a strange problem with Wicd, which I prefer to use for my wireless client. I'm coming to Kubuntu after a long hiatus (been using Arch) and I'm using the KDE version of the wicd client.

I have a wireless-N network in my home, but I also have an ethernet cable at my desk that I plug in when I'm stationary. In fact, I almost always use the ethernet cable unless I am away from my desk for whatever reason. I have wicd setup to always show the ethernet connection, and always switch to a wired connection when available. My wireless connection is set to automatically connect.

Now here's the problem. When I boot up my laptop while the ethernet cable is plugged in, the wireless connection and ethernet connection plays a strange "tug of war" match where one will connect, and the other will cancel it out and try to connect. Basically, wicd sees the network cable is plugged in and it tries to enable my wired connection, but then my wireless connection tries to connect cancelling out the wired connect, and then the wired connection cancels out the wireless connection, it creates an infinite loop and neither will connect. If I click "abort" and connect to one of them manually, it always works. But both can't be automatic.

The strange thing is that this worked fine in Arch, also using the KDE version of wicd, set up the same way. If I plugged in my wire, it would disconnect wireless and connect via the cable. If I unplugged my cable it would switch to wireless.

Anyone else have this problem? I hope my explanation isn't too long it was kind of hard to explain.

---

