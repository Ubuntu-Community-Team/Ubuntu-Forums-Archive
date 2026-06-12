---
title: "IRSEND not blasting signal"
date: 2011-03-26
forum: General Help
---

### Post by YfoMp5QBh2 on 2011-03-26
Hi Everyone,

I want to use IRSEND to send an IR pulse to my TV (to switch it on, off) on receipt of a IR pulse from my MCE remote. The MCE remote is correctly configured and the USB IR receiver recognises the pulses (confirmed using irw).

This is what I know

[LIST]
[*]I have downloaded the correct lirc codes for the TV's remote
[*]I know I have to add the codes to one of the lirc.conf files but not sure which
[*]Finally I should configure the lircrc file so irexec can send the TV's IR pulse on receipt of the IR pulse from the MCE remote
[/LIST]
When I try ```
irsend SEND_ONCE Samsung_BN59-00603A power
``` the terminal returns ```
irsend: command failed: SEND_ONCE samsung_BN59-00603A power
``` and ```
irsend: unknown remote: "samsung_BN59-00603A"
```Can anyone tell me where I am going wrong? TBH lirc's official website talks as if you seem to know exactly what your doing and hasn't been much help unfortunately.

---

### Post by YfoMp5QBh2 on 2011-03-28
bump?

---

### Post by YfoMp5QBh2 on 2011-03-29
BUUUUUUUUMP. please? can anyone help?

---

