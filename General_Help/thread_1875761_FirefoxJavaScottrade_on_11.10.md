---
title: "Firefox/Java/Scottrade on 11.10"
date: 2011-11-05
forum: General Help
---

### Post by i8bugs on 2011-11-05
SOLVED:
Here's an easy way to run Scottrade Streaming Quotes in Firefox and Ubuntu without opening terminal, coding, or building any treacherous symlinks :
Go to Ubuntu Software Center/ Search "Java"
Install:
OpenJDK Java 6 Runtime
Icedtea Java Plugin
Tcedtea Java 6 Webstart

Open Firefox
Go to Scottrade
Click on Streaming Quotes Application
At this point, download manager will show file Scottrader-1.jnlp (or some version of that but it will be a *.jnlp file)
Right click on that file and select "open containing folder"
Find that same file and right click on it again.  Select "Properties"
Select tab "Open With"
Select "Icedtea Java 6 Webstart" and click "save as default'
Close everything up. You should not need to restart anything, but I do anyway to ensure it's not a factor.
Your Scottrade application should run.  If it does not, than you are like a JEEP- a lot further from help than I can give you :)
If this was any help, please let me know.

---

### Post by YumaJim on 2011-12-30
I8bugs - Thanks for the solution - worked for me - great write up.

---

### Post by i8bugs on 2011-12-31
Glad to help.  After I had to do a reinstall, I needed these instructions for myself again!

---

