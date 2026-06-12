---
title: "Using Transmission, Empathy, etc. With Internet Connection Through Android (Proxoid)"
date: 2010-08-22
forum: General Help
---

### Post by Forgotten Path on 2010-08-22
I use my HTC DROID Eris (firmware 2.1) to establish an internet connection using the Android SDK package and the phone app Proxoid (Details/Methods [here]("http://code.google.com/p/proxoid/wiki/installationLinux").), so that I can browse the internet using Verizon Wireless's 3G network.  The Android Debug Bridge (from the SDK) is used to forward requests to a certain port to the phone, and then Proxoid forwards them to the network.  You set your proxy settings for the selected port you are forwarding.  I am currently forwarding port 8080, so my proxy setting is localhost:8080.

I have everything working fine, but I still have one major issue that I would like to resolve, if possible.  Even when I apply the proxy settings system wide in the Gnome Network Proxy, I am still unable to use Transmission, Empathy, (G)Wget or any other program besides FireFox to connect to the internet.  I have even tried giving each program its own proxy setting (localhost:8080), with no luck. [Edit] When proxy settings are applied system wide, Update Manager as well as Synaptic work just fine. [Edit]

I have searched and searched Google and have not found any existing solutions, and I have read some on port forwarding, etc, but been unable to find any kind of solution.

Is it even possible?  Does anyone have any clue on how to begin?
Thanks for any replies!

---

### Post by Forgotten Path on 2010-08-22
I was hoping that maybe someone could at least point me in the right direction...  Surely someone else must be using Proxoid, or have an inkling as to whats going on!

:confused:

---

