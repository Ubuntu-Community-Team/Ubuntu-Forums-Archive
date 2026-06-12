---
title: "Trouble with Emerald"
date: 2010-05-04
forum: General Help
---

### Post by jjb5909 on 2010-05-04
So, I'm pretty much brand new to the entire Linux deal, so pardon my lack of proper terms and whatnot. 

I have the 64bit edition of Ubuntu, 10.04 or whatever the latest is. 

Basically, I got this theme, and it installed fine when I dragged it to the Appearance application. However, it also came with a corresponding theme for Emerald. 

So I installed Emerald and imported the theme just fine, I see it as a choice to pick in the theme selection area. When I click it though, Emerald just disappears, and nothing happens. I guess it crashes. So, I was researching around and read about a terminal command that was: 

emerald --replace 

When I run that, I get the following error: 
"(emerald:7750): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks","
Then, terminal hangs, and if I exit, all my borders disappear, I can't drag around windows, and stuff like that. 

I need to fix this, because my desktop is really lacking usability without buttons and such. So any advice would be appreciated, and I'll do whatever I can to help you guys help me if needed. 

Thanks!

---

### Post by WorMzy on 2010-05-04
Unfortunately there's a bug in the Emerald theme manager right now. If you want to get your windows borders and controls back press Alt+F2 and run 'metacity --replace'.

---

