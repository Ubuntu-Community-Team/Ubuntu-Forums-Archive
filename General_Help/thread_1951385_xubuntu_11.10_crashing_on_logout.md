---
title: "xubuntu 11.10 crashing on logout"
date: 2012-04-02
forum: General Help
---

### Post by lukeone on 2012-04-02
Now I have this problem:  The computer crashes when I log out.  It's almost like a blue screen of death but it's black and white.  I will supply more info as needed. At this time I don't know what to tell you.

---

### Post by CynicRus on 2012-04-02
Cashes only in LXDE?

---

### Post by lukeone on 2012-04-02
Not sure.  Not even sure what that is.  I bring down the menu from the top, not right click, and click "logout" disaster.

---

### Post by 2F4U on 2012-04-02
@CynicRus: He is talking about Xubuntu (XFCE) and not LXDE.

@lukeone: What are your hardware specs, what graphics driver do you use? Is this happening on every logout?

---

### Post by CynicRus on 2012-04-02
@2F4U Yes, exactly. I have them from time to time, confuse)
May try open terminal, and run : [B]xfce4-session-logout --logout 
If system freeze\crash - paste terminal output to here.

[/B]

---

### Post by lukeone on 2012-04-02
Seems to happen on every logout.  Getting the specs now.  Can you tell me a fast way to find them?

---

### Post by CynicRus on 2012-04-02
Well, I'm not telepathic, to predict that your system is not the case with this procedure. Give some more information and maybe someone will be able to solve this problem

---

### Post by lukeone on 2012-04-02
```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]

```

---

### Post by CynicRus on 2012-04-02
Give your session log. Usually is it: /home/user/.xsession-errors

---

### Post by lukeone on 2012-04-02
command not found

---

### Post by CynicRus on 2012-04-02
/home/user/.xsession-errors:
instead of the user - substitute your username that you use. well, before the above way - put cat.

---

### Post by lukeone on 2012-04-02
No dice.  Or I'm not really understanding what you're asking me to do.

---

### Post by lukeone on 2012-04-02
Looks like a lot of folks are having this problem and no solution.

---

