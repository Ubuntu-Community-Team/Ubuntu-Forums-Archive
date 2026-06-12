---
title: "rename ID associated with /dev/input/js0"
date: 2012-03-03
forum: General Help
---

### Post by brneuro on 2012-03-03
Hi folks,

hopefully General Help is the right forum for this.

I'm having a problem where a gamepad is not being detected by some software. The gamepad is hooked up and running in a few games, and is listed as /dev/input/js0. I think the problem with one specific piece of software (MATLAB PsychToolbox) not finding the gamepad is because when I run

```
ls /dev/input/by-id
```the device shows up as

```
usb-&#1033;_PPM___________-event-joystick
usb-&#1033;_PPM___________-joystick
```which, as you can see, contains UNICODE characters.

Is it possible to rename the device's ID so that it contains only regular ASCII charaters, and then hopefully shows up as an available device in my software?

Thanks,
Brian

EDIT:
I just tried
```
sudo mv /dev/input/by-id/usb-&#1033;_PPM___________-event-joystick /dev/input/by-id/usb-mygamepad-event-joystick
...and...
sudo mv /dev/input/by-id/usb-&#1033;_PPM___________-joystick /dev/input/by-id/usb-mygamepad-joystick
```
and while it appeard to change the ID when running ls, it did not change the actual ID, as evidenced by running jstest and still seeing UNICODE in the ID.

---

