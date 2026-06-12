---
title: "wired key mapping problem"
date: 2010-03-09
forum: General Help
---

### Post by 3piglets on 2010-03-09
Dear experts,

I have a wired key mapping problem. When I'm in xterm, my "i" key somehow maps to "paste" key. And I do not know how to correct it.

For example, if I have done copy and paste with mouse, say "ubuntu" in another program, say firefox, then I switch to a xterm, typing "ifconfig". Whenever I type "i", it will show "ubuntu" instead. The temporary fix is I do another copy and paste of "i". But after a while the mapping is invalid that my "i" key is mapping to nothing. I have checked that any other keys are still good.

Basic info:

I have a ubuntu 9.10 guest running in a virtualbox 3.1.2. It worked fine for several months until this morning with this wired problem. Recently, I have installed AWN.

Any solution or fix is welcome.

Jun

---

### Post by 3piglets on 2010-03-09
This is really wired. If I open up another xterm from the problem xterm, everything is ok in the new xterm. It is only the one opened from application/accessory/terminal that has no "i" key. I have reinstalled terminal program, the problem does not go away. The upper case "I" works fine on that key. The same problem persists with different key board. bummer!

---

### Post by 3piglets on 2010-03-11
> **3piglets said:**
> This is really wired. If I open up another xterm from the problem xterm, everything is ok in the new xterm. It is only the one opened from application/accessory/terminal that has no "i" key. I have reinstalled terminal program, the problem does not go away. The upper case "I" works fine on that key. The same problem persists with different key board. bummer!
This is what I found out:

I use the terminal from Application/Accessory/Terminal. In this terminal, when I click on Edit from menu bar, I see paste is mapping to "i". Now I know why.

---

