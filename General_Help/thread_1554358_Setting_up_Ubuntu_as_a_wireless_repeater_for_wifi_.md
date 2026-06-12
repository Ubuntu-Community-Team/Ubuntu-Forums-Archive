---
title: "Setting up Ubuntu as a wireless repeater for wifi RC helicopter."
date: 2010-08-16
forum: General Help
---

### Post by Agarax on 2010-08-16
Hi,

This is a little off beat, but I recently preordered a [remote control wifi helicopter]("http://ardrone.parrot.com/parrot-ar-drone/usa/") that is controlled by an iphone.

I'm thinking to myself, "the only thing that is cooler than a helicopter controlled over wifi with a phone is doing it long distance using a directional antenna."

I currently have a netbook, some usb 802.11 adapters, and a [cantenna]("http://www.cantenna.com/").

Now, the toy is only controllable by an iphone or a ipod touch.  I would like to have Ubuntu act as a wireless repeater, like below.

iphone --> ~802.11~ --> wlan0 usb --> Ubuntu forwards packets at Layer 1 --> wlan1 usb connected to Cantenna --> ~802.11~ --> helicopter.

---

