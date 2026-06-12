---
title: "Remote desktop"
date: 2010-05-07
forum: General Help
---

### Post by pr3zident on 2010-05-07
Can someone please tell me how to connect my ubuntu 10.04 lts netbook to my ubuntu desktop with remote desktop im a noob i need help please?

---

### Post by lisati on 2010-05-07
Moved to "General help"

---

### Post by 3rdalbum on 2010-05-07
Remote Desktop is for controlling one computer from the other computer.

If that's what you want, then remote desktop is a doddle to set up. On the computer whose desktop you want to control, go to System > Preferences > Remote Desktop and click "Allow other users to view your desktop" and "Allow other users to control your desktop". Set up some sort of security (such as confirming access, or requiring a password). If the netbook and desktop are not on the same network, then you must also check "Configure network automatically".

On the computer that you want to use to do the controlling, go to Applications > Remote Desktop. If your computers are on the same network, the target computer will appear in the left pane and you can just double-click it. If they're not on the same network, you'll need to click the Connect button and type the external IP address of the target computer. The method should be VNC.

That's all there is to it.

---

