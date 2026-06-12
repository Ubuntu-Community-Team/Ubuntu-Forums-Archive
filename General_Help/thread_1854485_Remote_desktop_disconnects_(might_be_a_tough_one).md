---
title: "Remote desktop disconnects (might be a tough one)"
date: 2011-10-04
forum: General Help
---

### Post by Tylerofl on 2011-10-04
I have Ubuntu installed on a desktop computer, which only has one goal - to automatically connect to a Windows 2003 terminal server with RDP via tsclient. It connects up just fine, you can use it with no issue. The computer shares a screen with a dialysis machine, and after a minute or so the dialysis machine takes over the screen to deliver patient stats, machine stats, etc. When you switch back to the Ubuntu machine, you see the remote desktop session on the screen, but as soon as you move the mouse, it cuts back to the GNOME desktop, where you have to open the RDP shortcut again. The session resumes, and everything you had open is still there.

Basically, I would like to have it keep the RDP session alive, and not close tsclient. The dialysis machine does not send any sleep or suspend commands to the computer when it switches over - the devices do not communicate at all, they only share a screen. I have already gone into power management in Ubuntu and turned off automatic sleep mode/screen dim. Any ideas?

---

### Post by dcstar on 2011-10-07
> **Tylerofl said:**
> I have Ubuntu installed on a desktop computer, which only has one goal - to automatically connect to a Windows 2003 terminal server with RDP via tsclient. It connects up just fine, you can use it with no issue. The computer shares a screen with a dialysis machine, and after a minute or so the dialysis machine takes over the screen to deliver patient stats, machine stats, etc. When you switch back to the Ubuntu machine, you see the remote desktop session on the screen, but as soon as you move the mouse, it cuts back to the GNOME desktop, where you have to open the RDP shortcut again. The session resumes, and everything you had open is still there.

Basically, I would like to have it keep the RDP session alive, and not close tsclient. The dialysis machine does not send any sleep or suspend commands to the computer when it switches over - the devices do not communicate at all, they only share a screen. I have already gone into power management in Ubuntu and turned off automatic sleep mode/screen dim. Any ideas?

Try the **remmina** package instead of tsclient.

---

