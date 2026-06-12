---
title: "How do I kill a rogue shell script?"
date: 2011-07-04
forum: General Help
---

### Post by Jforsyth on 2011-07-04
I was trying to write an innocuous shell script, but I messed up and, upon executing the script, it began to spawn a million copies of Nautilus. 

I tried logging out and restarting, but the script appears to be executing at start-up. Each time I log in, I have about 2-3 good minutes before the interface locks up and the computer becomes unusable. 

Does anyone have any suggestions?

---

### Post by Habitual on 2011-07-04
Logout to Login prompt/GUI/screen
Login to console with Ctrl+Alt+F1 
rename rogue script.
exit console.
Ctrl+Alt+F7 to login graphically.

---

### Post by 3Miro on 2011-07-04
With 2 - 3 minutes you can open System Monitor (System -> Admin), find the process and kill it. Also, look into startup (session) programs to see why it gets executed.

---

