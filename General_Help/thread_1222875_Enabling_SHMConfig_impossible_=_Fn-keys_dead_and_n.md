---
title: "Enabling SHMConfig impossible = Fn-keys dead and non-configurable touchpad"
date: 2009-07-25
forum: General Help
---

### Post by linduxed on 2009-07-25
I've got an Asus Eee 1005HA and a large part of the Fn-keys do not work with a standard install of Jaunty. Among other things this includes the WiFi on/off Fn-combination and the touchpad on/off.
Some googling has hinted that the first step to fixing these issues is enabling SHMConfig, but this has turned out to be harder than expected.

First of all, the xorg.conf method is out of the question since hotplugging is present in Jaunty. This leaves me with tweaking the hal-policies, which has not worked so far.
The guide provided [here]("http://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig") has not worked, whenever I try running applications like gsynaptics (which requires SHMConfig to be on) it tells me that SHMConfig is not enabled.

I'm aware of the fact that Karmic has dropped hal, and that this therefore will potentially be auto-solved in Karmic, but I'm neither in for using non-final releases, nor am I keen on waiting until the end of october to have my Fn-keys and touchpad working.

---

