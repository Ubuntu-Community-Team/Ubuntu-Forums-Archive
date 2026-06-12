---
title: "udev run command is and isn't working"
date: 2011-09-28
forum: General Help
---

### Post by oiper on 2011-09-28
I've got the following udev rule (71-touchpad.rules):
```
# disable PS/2 touchpad on DISPLAY :0 if a mouse is added to the system
ACTION=="add", SUBSYSTEM=="input", ENV{ID_INPUT_MOUSE}=="1", RUN+="/bin/sh -c 'DISPLAY=:0 /usr/bin/xinput --set-prop ImPS/2\ ALPS\ GlidePoint Device\ Enabled 0'"

# enable PS/2 touchpad on DISPLAY :0 if a mouse is removed from the system
ACTION=="remove", SUBSYSTEM=="input", ENV{ID_INPUT_MOUSE}=="1", RUN+="/bin/sh -c 'DISPLAY=:0 /usr/bin/xinput --set-prop ImPS/2\ ALPS\ GlidePoint Device\ Enabled 1'"

```

Testing the rule, it appears to run as expected:
```

sudo udevadm test --action=remove /sys/devices/platform/i8042/serio1/input/input8/mouse1 2>&1 | grep "run:"
udevadm_test: run: '/bin/sh -c 'DISPLAY=:0 /usr/bin/xinput --set-prop ImPS/2\ ALPS\ GlidePoint Device\ Enabled 1''
sudo udevadm test --action=add /sys/devices/platform/i8042/serio1/input/input8/mouse1 2>&1 | grep "run:"
udevadm_test: run: '/bin/sh -c 'DISPLAY=:0 /usr/bin/xinput --set-prop ImPS/2\ ALPS\ GlidePoint Device\ Enabled 0''

```

However, the command doesn't do anything. If I run the command manually, it works as expected (turns the touchpad on and off):
```
/bin/sh -c 'DISPLAY=:0 /usr/bin/xinput --set-prop ImPS/2\ ALPS\ GlidePoint Device\ Enabled 1'
/bin/sh -c 'DISPLAY=:0 /usr/bin/xinput --set-prop ImPS/2\ ALPS\ GlidePoint Device\ Enabled 0'

```

Also, I can run the command from a terminal outside of my X11 session and it runs without error. (Testing with DISPLAY=:1 I get an error about not being able to connect to the X server.)

Why isn't the udev run command working?

---

### Post by siersmak on 2012-03-20
Hello Oiper,

I am experiencing the exact same problem you describe here. My udev rule looks very similar to yours, udevadm test appears to work correctly, but my touchpad doesn't get disabled when I plug my usb mouse into the usb port.  Did you get this to work?

---

### Post by karre on 2012-04-20
Hi ,

I wrote customized udev rule to auto mount and umount when we insert the usb drive and remove case.

My mount rule is working but umount is not working.

How can i debug this issue.

Thanks,

---

