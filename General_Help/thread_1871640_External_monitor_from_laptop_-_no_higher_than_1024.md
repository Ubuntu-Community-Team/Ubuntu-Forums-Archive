---
title: "External monitor from laptop - no higher than 1024x768"
date: 2011-10-29
forum: General Help
---

### Post by etienne@Rofti on 2011-10-29
Dear all

I have an HP-Compaq 615 laptop that I connect up with an external monitor so that I can work with two screens. So, when I did a fresh install of Ubuntu Oneiric 64-bit, I expected no problems when connecting up my second monitor...

However, no matter what I do, I cannot set the resolution any higher than 1024x768, even though the monitor's max resolution is 1440x900.

Google searches have only been taking me to posts telling me to use the now-defuct xorg.conf which is useless, or to use various xrandr commands, which only give me error messages.

Does anyone know how to get Ubuntu to recognize and use the monitor's real resolution? I am not using the proprietary fglrx driver because the laptop is much faster on the open-source driver.

---

### Post by etienne@Rofti on 2011-11-01
No-one?

---

### Post by alco75 on 2011-11-01
Did it used to work for you in Natty?

Because it *never* has for me. I have only ever been able to get my 1440x900 monitor to display at the same resolution as my 1366x768 laptop, unless I actually switch the laptop's display off entirely, in which case I *can* get the monitor to display 1440x900.

---

### Post by etienne@Rofti on 2011-11-01
Dear alco75

Thank you for the reply. I have not yet tried to disable to laptop's screen so as to work solely with the external monitor. I will definitely try it. I will let you know how it went.

And no, it did not work in Natty. It worked perfectly in Maverick, however.

---

### Post by WasMeHere on 2011-11-01
Hi Etienne,

Maybe you have already tried this, but just in case you haven't...

You can choose to display the same desktop on both screens, the internal and the external. In this case, the lowest resolution will limit the display. But if you choose the option to have different desktops, you can select the resolution independently for the two screens.

If there is a limitation on one of the screens below that of the monitor, I think that the graphics driver does not recognize that monitor. Maybe another driver would work better, for example a proprietary driver for the graphics card/chip. But maybe this would cost speed in your case.

Have fun finding out :-)
Olle

---

