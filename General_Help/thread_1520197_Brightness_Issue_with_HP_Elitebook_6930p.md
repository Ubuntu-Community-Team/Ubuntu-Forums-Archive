---
title: "Brightness Issue with HP Elitebook 6930p"
date: 2010-06-29
forum: General Help
---

### Post by vel. on 2010-06-29
Hey been having an issue with adjusting the brightness on my laptop
- HP Elitebook 6930p - the issue is as follows:
1. the function buttons do nothing for the brightness, not even the brightness bar is shown after pressing them [fn + f9/f10]

2. when i try to adjust is manually it still doesn't do anything

3. they only time my brightness flickers is when I plug in the power cable and then I need to relog into ubuntu to get it to max brightness.

Currently running Ubuntu 10.04 Lucid Lynx 64bit desktop version.
Does anyone have an issue like this or perhaps even a fix for it? :)
Opinions are welcome.

thanks in advice!
-vel.

---

### Post by ossipetz on 2010-08-08
hallo

exact same problem here. the brightness does what it wants. the light sensor (fn/f11) does work but not the brightness. if booting with a power plug the brightness is higher that when booting from battery.

There is some report in the bugtracker:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284319](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284319)

it suggests adding a few entries in: 
/usr/share/hal/fdi/information/20thirdparty/30-keymap-private.fdi
(i had to create the file)
 
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="@input.originating_device:info.linux.driver" string="atkbd">
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix="Hewlett-Packard">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains="6930p">
          <!-- HP Compaq 6930p -->
          <append key="input.keymap.data" type="strlist">e012:brightnessdown</append> <!-- FnF9 (brightness down) -->
          <append key="input.keymap.data" type="strlist">e017:brightnessup</append> <!-- FnF10 (brightness up) -->
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

```this makes the brightness popup appear once but it still is not the solution.

the same issue was reported in [http://ubuntuaddict.com/ubuntu-brightness-issue-with-hp-elitebook-6930p/](http://ubuntuaddict.com/ubuntu-brightness-issue-with-hp-elitebook-6930p/) too but no answer there yet neither.

hopefully someone with a better knowledge of keymap internals stumbles uppon this thread ;)

---

### Post by vel. on 2010-09-24
> **ossipetz said:**
> hallo

exact same problem here. the brightness does what it wants. the light sensor (fn/f11) does work but not the brightness. if booting with a power plug the brightness is higher that when booting from battery.

There is some report in the bugtracker:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284319](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284319)

it suggests adding a few entries in: 
/usr/share/hal/fdi/information/20thirdparty/30-keymap-private.fdi
(i had to create the file)
 
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="@input.originating_device:info.linux.driver" string="atkbd">
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" prefix="Hewlett-Packard">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains="6930p">
          <!-- HP Compaq 6930p -->
          <append key="input.keymap.data" type="strlist">e012:brightnessdown</append> <!-- FnF9 (brightness down) -->
          <append key="input.keymap.data" type="strlist">e017:brightnessup</append> <!-- FnF10 (brightness up) -->
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

```this makes the brightness popup appear once but it still is not the solution.

the same issue was reported in [http://ubuntuaddict.com/ubuntu-brightness-issue-with-hp-elitebook-6930p/](http://ubuntuaddict.com/ubuntu-brightness-issue-with-hp-elitebook-6930p/) too but no answer there yet neither.

hopefully someone with a better knowledge of keymap internals stumbles uppon this thread ;)

Yes, I saw this bug report unfortunately I don't have an issue with the brightness notifier( It always shows the notifier when pressing FN + F9 or F10 ) and I applied the solution from the bug report but it doesn't seem to do anything for me.
I'm still looking for a solution. If anyone can help please do :)

---

