---
title: "Stop running services 11.04"
date: 2011-04-30
forum: General Help
---

### Post by Sinopa on 2011-04-30
When I shut down ubuntu I see a lot of programs/services that are being stopped/shutdown. Is there an app that I can use to see what's running and shutdown/disable those I don't need?

---

### Post by 3Miro on 2011-04-30
Most of the "services" are vital for your system.

Lookup "Startup Applications" in the search menu and then disable some of those (if you are sure that you don't need them).

---

### Post by Sinopa on 2011-04-30
> **3Miro said:**
> Most of the "services" are vital for your system.

Lookup "Startup Applications" in the search menu and then disable some of those (if you are sure that you don't need them).

I know most are vital, but some aren't. And Startup Applications don't snow them.

---

### Post by 3Miro on 2011-04-30
Try to read on the individual ones. There is no sure way for me to know what you need or use.

Do you use Bluetooth, if not, you can remove that one.

You can probably disable the "check for new hardware drivers", you will have to do it manually if you change the video card or the wireless card (people rarely do that).

Do you have a printer? If not, then disable that one.

Do you use the Alarm Notifier and/or Visual Assistance? Do you use Remote Desktop.

The rest should probably stay, but then again, my system is not your system.

---

### Post by Sinopa on 2011-04-30
> **3Miro said:**
> Try to read on the individual ones. There is no sure way for me to know what you need or use.
Do you use Bluetooth, if not, you can remove that one.
You can probably disable the "check for new hardware drivers", you will have to do it manually if you change the video card or the wireless card (people rarely do that).
Do you have a printer? If not, then disable that one.
Do you use the Alarm Notifier and/or Visual Assistance? Do you use Remote Desktop.
The rest should probably stay, but then again, my system is not your system.

As I wrote before I'm not after the startup application preferences. I have already disabled the things I don't need there.

I'm looking for an app that shows me the services running and were I can disable/turn them off.

Is there anyone out there that know of an app like i described above? I tried System Jobs, but that wasn't exactly it.

---

### Post by 3Miro on 2011-04-30
Use rcconf. Open a terminal then to install:

```
sudo apt-get install rcconf
```

to start:

```
sudo rcconf
```

Google each service first to make sure you don't disable anything important. Other than Bluetooth and CUPS (printing), you probably don't want to mess with the rest.

---

### Post by 5149.5 on 2011-04-30
> **3Miro said:**
> Google each service first to make sure you don't disable anything important. Other than Bluetooth and CUPS (printing), you probably don't want to mess with the rest.

The SANE daemon, pppd-dns, dns-clean, rsync, and pcmciautils are other possibilities.

---

### Post by Sinopa on 2011-04-30
> **3Miro said:**
> Use rcconf. Open a terminal then to install:

```
sudo apt-get install rcconf
```to start:

```
sudo rcconf
```Google each service first to make sure you don't disable anything important. Other than Bluetooth and CUPS (printing), you probably don't want to mess with the rest.

Thank you 3miro. That was exactly what I was after :)

---

