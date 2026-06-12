---
title: "Connected HP Pav laptop to Vizio TV, displays computer on tv but not on laptop?"
date: 2010-06-23
forum: General Help
---

### Post by RonB123123 on 2010-06-23
Hi. I connected my HP Pavillion laptop to a 1360x768 Vizio TV. On the TV it displays my laptop but on my laptop it has a black screen. How do I fix it so I can see my laptop screen on my laptop and on my TV at the same time?

I used to be able to do this with this TV as well as my friend's Samsung. I'm using a VGA connector. What should I do to have my laptop screen on my laptop and on my TV at the same time?

Thank you,
R

---

### Post by Praetor77 on 2010-06-23
You can try installing and running lxrandr (or use xrandr if comfortable with command line) and using it to turn on your default display. Nevertheless, the default should not be to turn it off when connecting another display!

When running xrandr on the command line, you will see what displays are enabled/disabled. For example, I have LVDS1 connected and VGA1 disconnected. To turn on VGA1, I would do xrandr --output VGA1 --auto.

---

