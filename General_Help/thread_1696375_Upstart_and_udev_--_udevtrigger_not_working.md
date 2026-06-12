---
title: "Upstart and udev -- udevtrigger not working"
date: 2011-02-27
forum: General Help
---

### Post by wd5gnr on 2011-02-27
Recently virtualbox started not letting me use any USB devices unless they were hot plugged. That is, no devices that were plugged in at boot were visible unless they were unplugged and replugged. In addition, my uvc camera was not being set up right.

A little investigating showed me that it should have (and apparently used to) work like this:

1) The kernel loads init (which is really upstart now)
2) Init loads udev this appears to work)
3) When udev finishes loading, udev runs udevadm trigger --action=add to pick up any events that happened before udev started.
4. Events for USB hot plugs cause VirtualBox's udev rules to execute a script to create a VirtualBox USB node for the device.
5) My camera also has a udev rule to load its custom setup.

I instrumented the udevtrigger.conf file and I can see that it is running, completing and not giving an error. But it is clear that no events are happening. HOWEVER, running sudo udevadm trigger --action=add manually lets everything work.

So I'm not sure where to go from here. The kernel is clearly able to produce the "late" events because running trigger manually works. But I am getting logging from my instrumentation telling me that the udevtrigger job is working. It just doesn't seem to do anything.

Any ideas?

Also, /var/log/udev (which upstart sets up and collects via udevmonitor and udev-finish) never shows any RUN events. But it does show all the devices. So it is as if the devices are found but either the rules are not being matched or the RUN parts of the rules are being inhibited somehow. Well, nevermind about that -- I manually triggered it and turns out you never see the RUN events even when they clearly work. So the log just doesn't show them. Interesting, too, that you have to run the trigger sudo or nothing happens (no error, but nothing happens). Surely upstart is running stuff as root....

---

