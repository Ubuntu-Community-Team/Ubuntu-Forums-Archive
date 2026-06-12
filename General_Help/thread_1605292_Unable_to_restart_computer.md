---
title: "Unable to restart computer"
date: 2010-10-25
forum: General Help
---

### Post by blairm on 2010-10-25
Hi.

Have installed Ubuntu Lucid and I'm unable to restart the computer. Doesn't work using the power icon in the top right or using sudo reboot from the termial - I have to hit the reset button to get the computer going again.
The problem is only related to restart - shutdown works as it should.
When I try to reboot, the screen goes black aside from a narrow band of crimson on the far left of the screen; it freezes at that point.
I've had a look through the var/log/messages and saw nothing that was an obvious problem, but then again it's not something I've ever had to look at before.
Tried adding acpi=off as an option but that seemed to make no difference.

Not sure whether it's relevant, but specs are 3ghz Core 2 Duo; ATI 4850;4gb ram; Gigabyte motherboard with Intel p31 express chipset.

Any advice would be much appreciated,

Blair

---

### Post by dcstar on 2010-10-25
> **blairm said:**
> Hi.

Have installed Ubuntu Lucid and I'm unable to restart the computer. Doesn't work using the power icon in the top right or using sudo reboot from the termial - I have to hit the reset button to get the computer going again.
The problem is only related to restart - shutdown works as it should.
When I try to reboot, the screen goes black aside from a narrow band of crimson on the far left of the screen; it freezes at that point.
I've had a look through the var/log/messages and saw nothing that was an obvious problem, but then again it's not something I've ever had to look at before.
Tried adding acpi=off as an option but that seemed to make no difference.

Not sure whether it's relevant, but specs are 3ghz Core 2 Duo; ATI 4850;4gb ram; Gigabyte motherboard with Intel p31 express chipset.

Any advice would be much appreciated,

Blair

Check the BIOS settings - maybe a reset to default will help - for any memory mapping options etc.

Also try an "sudo init 6" and see if it behaves differently.

---

