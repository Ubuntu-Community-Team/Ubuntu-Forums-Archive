---
title: "How to forbid hald to start 'hald-addon-hid-ups' process?"
date: 2009-08-30
forum: General Help
---

### Post by ilna on 2009-08-30
Last one conflicts with 'nut' (upsd) service.

---

### Post by kerry_s on 2009-08-30
did you install "nut-hal-drivers"?

---

### Post by ilna on 2009-08-30
> **kerry_s said:**
> did you install "nut-hal-drivers"?
There was a moment when they were installed, but currently the package is removed.

It seems like I need to add something like 

```
$ cat /usr/share/hal/fdi/policy/10osvendor/10-ignore-power-mgmt.fdi
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">

  <device>
    <match key="hiddev.application_pages" contains="Power Device Page">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>

</deviceinfo>

```

Can not test just at the moment...

---

### Post by ilna on 2009-08-30
No, it doesn't work...

---

### Post by ilna on 2009-08-30
Ok, this does work

```
$ cat /etc/hal/fdi/preprobe/10osvendor/10-ignore-power-mgmt.fdi
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">

  <device>
    <match key="usb_device.vendor_id" int="1892">
      <match key="usb_device.product_id" int="1281">
        <merge key="info.ignore" type="bool">true</merge>
      </match>
    </match>
  </device>

</deviceinfo>
```

where usb_device.xxx_id were found with 'hal-device'.

---

