---
title: "My first Linux BSOD"
date: 2011-03-16
forum: General Help
---

### Post by Rebelli0us on 2011-03-16
PC just freezes coming out of suspend S3, happens intermittently. Any ideas how to fix it?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186259&stc=1&d=1300284041[/IMG]

---

### Post by An Sanct on 2011-03-16
BlueTooth (**bt**usb) is complaining ... do you use it?

---

### Post by Rebelli0us on 2011-03-16
> **An Sanct said:**
> BlueTooth (**bt**usb) is complaining ... do you use it?

Thank you. Yes a Cirago BTA-3210 USB Bluetooth Dongle.

We have two **identical** machines, one with Lucid 10.04, one with Maverick 10.10... Lucid resumes fine, Maverick crashes.

---

### Post by Rebelli0us on 2011-03-16
In Windows I'd uninstall the device and let the system reconfigure. What can I do with Linux "Device Manager"?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186298&stc=1&d=1300304744[/IMG]

---

### Post by Rebelli0us on 2011-03-25
Lucid 10.04 started crashing as well, after a recent update.

Both machines have a Wii remote mouse via Bluetooth. Bluetooth is suddenly "disabled" during resume from s3 and system crashes. Removing and re-inserting the BT dongle temporarily fixes the problem.

Adding/removing this line made some difference but hasn't stopped the crashes

```
echo USB0 >> /proc/acpi/wakeup
```

I'd wanted to enable wakeup from keyboard but somehow this line enables USB0 to USB6 which includes the Bluetooth USB dongle.

Crashing is intermittent, system will suspend-resume successfully for several cycles, then on resume the screen shows black and white bands with CAPS LOCK and SCROLL LOCK LEDs flashing..

---

### Post by Rebelli0us on 2011-04-03
I've narrowed this down:

**It is the Bluetooth pairing with Wii mouse that causes the OS to freeze.** It always happens right after resume form S3 when I press Wii buttons 1 & 2 to make device discoverable.

I've also googled and this problem goes back a few **years** with people reporting that Bluetooth pairing with various devices causes OS to freeze.

---

### Post by Rebelli0us on 2011-10-22
Still happening -- Wii remote driver (wminput) in daemon mode wipes out Ubuntu when it attempts to reconnect on resume from S3. Will they ever fix this? Here's what's left on the screen as the system goes down.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=205145&stc=1&d=1319293992[/IMG]

---

