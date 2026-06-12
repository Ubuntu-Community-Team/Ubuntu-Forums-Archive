---
title: "Upstart - &quot;net-device-added&quot; Event"
date: 2010-01-11
forum: General Help
---

### Post by maddog2050 on 2010-01-11
Hi,

Can anyone tell me what fires off the upstart event "net-device-added" ? I think it's udev but I can't find the rule.

Thanks in advance

Adam

---

### Post by maddog2050 on 2010-01-20
Any ideas?

---

### Post by akheron on 2010-03-19
I think it's the upstart-udev-bridge daemon.

---

### Post by mkalen on 2012-06-15
> **maddog2050 said:**
> Can anyone tell me what fires off the upstart event "net-device-added"? I think it's udev but I can't find the rule.

(I know this is an old thread, but since it took me some time to search for the answer and this thread ranked high on Google, I am adding an answer for completeness and to help others.)

You're right - udev is the source and the upstart-udev-bridge forwards the event to Upstart.

Using "[FONT="Courier New"]man upstart-events[/FONT]" (see also [manpages.ubuntu.com]("http://manpages.ubuntu.com/manpages/natty/man7/upstart-events.7.html")) you get a summary of well-known Upstart events. Relevant excerpts for "net-device-added" (from the 11.10 Oneiric version of the manpage, upstart 1.3-0ubuntu12): ```

&#9474;Ref &#9474;       Event      &#9474; Type &#9474; Emit &#9474;  Time   &#9474; Note &#9474;
&#9474; 3  &#9474; net-device-added &#9474;  S   &#9474;  U   &#9474; > (5)   &#9474;  C   &#9474;

```
> 
Event type S = Signal (Non-blocking)

Event emitter U = upstart-udev-bridge

Event note C = upstart-udev-bridge will emit events which match the pattern, "S-device-A" where 'S' is the udev subsystem and 'A' is the udev action. See udev(7) and for further details.


However, checking the udev log in [FONT="Courier New"]/var/log/udev[/FONT] you will see that the udev action is actually "add". Example udev event for my eth0 interface: ```

UDEV  [4.225817] add      /devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0 (net)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0
SUBSYSTEM=net
INTERFACE=eth0
IFINDEX=2

```

There is a translation table in the [upstart-udev-bridge source]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/oneiric/upstart/oneiric/view/head:/extra/upstart-udev-bridge.c") (lines 202-214) that reveals what will get translated in the bridge (I could not find this info in the manpage): > 
add -> added
change -> changed
remove -> removed
 Given those translations, the "S-device-A" pattern from the manpage makes sense (SUBSYSTEM=net, ACTION=add, translated to added gives "net-device-added").

---

