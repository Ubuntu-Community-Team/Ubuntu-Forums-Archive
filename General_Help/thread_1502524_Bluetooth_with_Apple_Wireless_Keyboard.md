---
title: "Bluetooth with Apple Wireless Keyboard"
date: 2010-06-05
forum: General Help
---

### Post by Maletor on 2010-06-05
Every time I start up Ubuntu my keybaord does not already connect to Bluetooth.

So far my fix is to go to the Bluetooth notifications bar => Apple wireless keyboard => dissconnect. Then I hit reconnect and it works as expected.

A real fix to this would be much appreciated. Thank you!

---

### Post by keithy on 2010-06-11
I am having exactly the same problem.  

Actually, the keyboard connects fine, just dont get any input through to the PC until a disconnect/reconnect is done :(

It was working fine with 9.10 karmic.

any ideas anyone??

---

### Post by keithy on 2010-06-16
Bump!

Any clues, if not a solution then a troubleshooting procedure would be most welcome - this is driving me insane

thanks

---

### Post by keithy on 2010-06-20
Finally!

adding hid_apple as first entry in /etc/modules has fixed it :)

---

### Post by Maletor on 2010-06-20
Yay baby!

---

### Post by sriram.venkataramani on 2010-08-02
Hi,

Can you elaborate on the fix? I am having the same issue.

- Sri

---

### Post by keithy on 2010-08-03
Hi,

open a terminal

type sudo gedit /etc/modules

add hid_apple as first uncommented entry

enjoy!

---

### Post by sriram.venkataramani on 2010-08-04
> **keithy said:**
> Hi,

open a terminal

type sudo gedit /etc/modules

add hid_apple as first uncommented entry

enjoy!


no love - still having the same issue.

---

### Post by keithy on 2010-08-06
Sri,

Sorry I'm not an expert and cannot even remember where I got the original tip from.

However, it has worked flawlessly for me.

---

