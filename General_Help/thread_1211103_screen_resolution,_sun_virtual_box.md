---
title: "screen resolution, sun virtual box"
date: 2009-07-12
forum: General Help
---

### Post by jhurrel on 2009-07-12
I can only get 800x600 resolution (very small screen) using sun virtual box. any help? using windows vista as host.

---

### Post by Legace on 2009-07-12
What's your guest?
You should install the Guest additions, but the procedure varies from system to system..

---

### Post by tasyhari on 2009-07-12
> **jhurrel said:**
> I can only get 800x600 resolution (very small screen) using sun virtual box. any help? using windows vista as host.

I presume you are using ubuntu as Guest OS. I managed to have the screen resolution (auto resize) worked when working with ubuntu version up to intrepid (8.10). 

Firstly, you should install guest addition. Just log in to ubuntu and from the virtual box menu (press host key to access it) go to Devices --> Install Guest Additions

Open your CDrom Drive in the Guest OS.. Open the drive folder and drag VBoxLinuxAdditions-x86.run to your desktop.

Open your terminal and direct it to the desktop and invoke the following command.

sudo ./VBoxLinuxAdditions-x86.run 

Enter your root pasword and you will be done.

Final step just requires you to restart the virtual machine and the screen size will be adjusted accordingly. You now can use the seamless mode which is great in my opinion. 

NB: I tried Jaunty and follow this step still did not work until now. However, when working in MAC-OS host, it runs perfectly.

---

