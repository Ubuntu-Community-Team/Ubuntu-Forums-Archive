---
title: "DBUS Broken"
date: 2009-09-25
forum: General Help
---

### Post by BillRebey on 2009-09-25
[COLOR="Silver"](I'm not using Karmic, but I'm posting here because it seemed the most relevant forum in which to discuss DBUS getting broken from one version to the next.  Please let me know if there is a more appropriate place to post.)[/COLOR]

The DBUS appears to have broken in the migration from 8.10/Intrepid to 9.04/Jaunty, and is presumably still broken in Karmic.  

It worked great in 8.10, but in 9.04, it doesn't release all the hardware that's removed, and it thinks removed hardware is still plugged in and accumulates an ever-growing list as devices are repeatedly plugged and unplugged.

Specifically, I'm using Future Technologies-based RS232-USB dongles.  When I plug them in, they're added correctly, but when I unplug them, they aren't completely removed, but rather remain in the list of attached devices.  

After some time of plugging/unplugging 7 devices, 		```
dbus_g_proxy_call(proxy, "FindDeviceByCapability", &error,G_TYPE_STRING, "serial"....)
``` returns a list of 169 devices that it thinks are still attached, when in fact 0 devices are attached.  The list is attached below.  

It might be worthy to note that -INSERTING- a dongle generates *THREE* device insertion callbacks, such as (... is shorthand for prefix "/org/freedesktop/Hal/devices"):
```
Device Inserted generates callbacks for:
'.../usb_device_403_6001_FTE2V2NK'
'.../usb_device_403_6001_FTE2V2NK_if0'
'.../usb_device_403_6001_FTE2V2NK_if0_serial_usb_0_23
```
but -REMOVING- a dongle only generates *TWO* device removal callbacks, in reverse order:

```
Device Removed generates callbacks for:
'.../usb_device_403_6001_FTE2V2NK_if0'
'.../usb_device_403_6001_FTE2V2NK'
```

Not surprisingly, the '.../usb_device_403_6001_FTE2V2NK_if0_serial_usb_0_??' entries are the ones that are "stuck" in the list (see below)


[COLOR="SeaGreen"]Any thoughts?[/COLOR]

(The following is the list of "stuck" devices - i.e., devices that DBus thinks are still attached but aren't.  All device names start with "/org/freedesktop/Hal/devices";  I've used ellipsis for brevity)

```
'.../usb_device_403_6001_FTE2V3IA_if0_serial_usb_0_22'
'.../usb_device_403_6001_FTE2V3HR_if0_serial_usb_0_21'
'.../usb_device_403_6001_FTDEHL44_if0_serial_usb_0_22'
'.../usb_device_403_6001_FTE2V2PF_if0_serial_usb_0_21'
'.../usb_device_403_6001_FTE2V0I7_if0_serial_usb_0_22'
'.../usb_device_403_6001_FTE2V2PF_if0_serial_usb_0_20'
...
... (lots of lines removed, but the pattern continues
... similar to the above with decreasing values in the 
... final two digits)
...
'.../usb_device_403_6001_FTE2V3EC_if0_serial_usb_0_0'
'.../usb_device_403_6001_FTE2V3EC_if0_serial_usb_0'
'.../usb_device_403_6001_FTE2V2PF_if0_serial_usb_0'
'.../usb_device_403_6001_FTE2V0I7_if0_serial_usb_0'
'.../usb_device_403_6001_FTE2V3HR_if0_serial_usb_0'
'.../usb_device_403_6001_FTE2V2NK_if0_serial_usb_0'
'.../usb_device_403_6001_FTE2V2TU_if0_serial_usb_0'
'.../usb_device_403_6001_FTE2V3IA_if0_serial_usb_0'
'.../usb_device_403_6001_FTDEHL44_if0_serial_usb_0'

```

---

### Post by BillRebey on 2009-10-02
I recently posted a problem with the DBUS _[COLOR="Blue"]([http://ubuntuforums.org/showthread.php?t=1275174]("http://ubuntuforums.org/showthread.php?t=1275174"))[/COLOR]_, but I've gotten no replies.

Is there a better place to get help with this issue?  It's a serious problem for me and I'd really like to get it fixed, but I'm not sure where to turn.

Thanks for any help!

---

### Post by cariboo on 2009-10-02
You may have better luck in General Help, as this issue is not specific to Karmic.

Edit: Please don't double post on the same subject, If you don't get an answer to your question, I'd advise you to bump your thread after 24 hours has elapsed.

---

