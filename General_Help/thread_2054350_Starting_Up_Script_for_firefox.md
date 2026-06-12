---
title: "Starting Up Script for firefox"
date: 2012-09-07
forum: General Help
---

### Post by MrC11 on 2012-09-07
Hello,

I got Ubuntu 12.04 on my PC but, I need a start-up script for firefox. I got the script for **Chromium** but, we decided to get **Firefox**.

Here is my old **Chromium** Script:

```
#!/bin/bash
xscreensaver -nosplash &
Onboard &
cat ~/.config/chromium/Local\ State | perl -pe "s/\"bottom.*/\"bottom\": $(xrandr | grep \* | cut -d' ' -f4 | cut -d'x' -f2),/" > ~/.config/chromium/Local\ State
cat ~/.config/chromium/Local\ State | perl -pe "s/\"right.*/\"right\": $(xrandr | grep \* | cut -d' ' -f4 | cut -d'x' -f1),/" > ~/.config/chromium/Local\ State
while true; do chromium-browser %u --kiosk --start-maximized; sleep 5s; done
```

But, I need this code for **Firefox**. Well I was giving It A try and maked the best off it.

```
#!/bin/bash
xscreensaver -nosplash &
Onboard &
cat ~/.config/firefox/Local\ State | perl -pe "s/\"bottom.*/\"bottom\": $(xrandr | grep \* | cut -d' ' -f4 | cut -d'x' -f2),/" > ~/.config/firefox/Local\ State
cat ~/.config/firefox/Local\ State | perl -pe "s/\"right.*/\"right\": $(xrandr | grep \* | cut -d' ' -f4 | cut -d'x' -f1),/" > ~/.config/firefox/Local\ State
while true; do firefox %u; sleep 5s; done
```

But. this doesn't work.
Does anyone know how the code should be?

Greetz,
MrC11

[SIZE="1"]PS. Sorry for my bad english I am Dutch.[/SIZE]

---

### Post by dcstar on 2012-09-07
> **MrC11 said:**
> Hello,

I got Ubuntu 12.04 on my PC but, I need a start-up script for firefox.


No you don't, you just put Firefox into the Startup Applications.

---

### Post by MrC11 on 2012-09-07
Forgot to say this.

It needs to start in kiosk-mode with a virtual-keyboard On top off it.

But, I will try this Thank you

Greetz,
MrC11

---

