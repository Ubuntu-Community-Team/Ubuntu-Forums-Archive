---
title: "Bluetooth mouse frustration"
date: 2010-03-12
forum: General Help
---

### Post by RutRow on 2010-03-12
I have a Dell Mini 10 running Ubuntu 8.04. I ordered the Mini with built-in bluetooth. I bought a Logitech mouse and powered it up. The dell saw it just fine the first time and it worked great. After I shutdown and restarted the mouse does not work. If I go to the bluetooth device wizard it sees the "Bluetooth Laser Travel Mouse" as installed. I can press the connect button on the bottom of the mouse but it never does connect.
 
In the bluetooth manager if I select the mouse and hit the forward button I get the error: Input already exists. There is no option to remove the mouse input. How can I delete that device paring and start again. 
 
I have searched but I did not find a solution.

---

### Post by RutRow on 2010-03-15
I found the partial solution. I have to go to terminal and type in: 

sudo hidd --search

Now I just need to figure out how to make that happen automatically. 

Is there an easier way?

---

### Post by agkq62 on 2010-03-22
I have the same problem with a Bluetooth keyboard, every time I restart the computer I have to reinstall the keyboard before it works.

Anyone got an idea?

Tried the above but got "command not found"

Thanks.

---

