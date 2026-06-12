---
title: "WLAN Light Blinks and other Terminal ????"
date: 2011-03-07
forum: General Help
---

### Post by kingbah on 2011-03-07
Hi, I am very new to Ubuntu and I need some help. My HP Pavillion WLAN light constantly blinks as it recieves data on the internet and I learned that I have to create and save a file: "sudo nano /etc/modprobe.d/wlan.conf" and then paste the following at the end: "#1 means do not blink options iwlcore led_mode=1" but when I try to save it asks me for my sudo password which I don't have and it does not even register any key I press. It just blinks but does not acccept any key. Also how do you save the file in terminal?

---

### Post by Quackers on 2011-03-07
Welcome to UF.
I don't think you can paste into a file using nano. You will have to type in the line that you want in there. To save the changes press ctrl+o (not zero) then press enter, then press ctrl+X
The password used for sudo is your user password.

---

### Post by kingbah on 2011-03-07
Appreciate your quick reply but it is not accepting any key I press when I try to enter my password after the cusor.

---

### Post by Agent Smith on 2011-03-08
This is correct. You will never see your password as you type it. I know its strange to get used to. Hope this helps.

---

