---
title: "Synaptics tweaking Synclient/HAL"
date: 2009-07-15
forum: General Help
---

### Post by gueshew on 2009-07-15
I have played around with synclient to find some ideal settings for my synaptics touchpad that I would like to apply permanently to my system.

I would like fingerlow=30 and fingerhigh=40.

Therefore I have created a new file entitled 11-x11-synaptics.fdi and placed it in the folder  /etc/hal/fdi/policy

the file reads:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.FingerLow" type="string">30</merge>
    <merge key="input.x11_options.FingerHigh" type="string">40</merge>
    </match>
  </device>
</deviceinfo>


after restarting HAL and computer these wanted settings don't seem to stick in my system, synclient -l proving it....

does anyone know what I did wrong?

thank you

---

### Post by gueshew on 2009-07-15
bump

---

### Post by aharown07 on 2009-08-26
I'd also love some help with this. Need to get double tap & drag working w/my touchpad.

Apparently it has something to do w/the info here: [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)
But it appears to me that there would be dozens of ways to mess up here. It's a far-from-ideal approach!

---

### Post by aharown07 on 2009-08-26
Here's the file I created.... that also doesn't work.
(synclient  -l reveals no change in parameters)

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">false</merge>
        <merge key="input.x11_options.MaxTapMove" type="integer">110</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="integer">1</merge>
    <merge key="input.x11_options.SingleTapTimeout" type="integer">3</merge>
        <merge key="input.x11_options.LockedDrags" type="string">true</merge>
    <merge key="input.x11_options.LockedDragTimeout" type="integer">1200</merge>
    </match>
  </device>
</deviceinfo>
```

---

