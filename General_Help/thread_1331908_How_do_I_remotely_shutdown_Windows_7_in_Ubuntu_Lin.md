---
title: "How do I remotely shutdown Windows 7 in Ubuntu Linux"
date: 2009-11-19
forum: General Help
---

### Post by robofighter on 2009-11-19
Preferably without using remote desktop, and Ubuntu is using verison 9.10.

Both computers are already set-up in a workgroup.

---

### Post by robofighter on 2009-11-24
bump

---

### Post by fluffman86 on 2009-11-24
telnet into it and issue the shutdown command.

---

### Post by karthik120 on 2009-11-24
You can login to the windows 7 using *Terminal server client* and shutdown.



Regards,
Karthik

---

### Post by tgalati4 on 2009-11-24
Turn off Windows firewall.  Remotely open several ports on the router for that machine.  Wait for BSOD.

Check your BIOS for shutdown options.  Your network card may have a sleep-on-lan setting.

---

### Post by fluffman86 on 2009-11-24
Just realized that Win7 doesn't have telnet turned on by default.  From [http://www.leateds.com/2009/telnet-for-windows-vista-windows-7/](http://www.leateds.com/2009/telnet-for-windows-vista-windows-7/) :
    * open control panel
    * Then go into programs
    * Then in programs and features there should be a part that says &#8216;turn windows features on or off &#8216;
    * Click &#8216;turn windows features on or off &#8216;  then on the list that appears simply choose: Telnet Client

Now you can open applications > accessories > terminal and type:

telnet 192.168.1.12

Where the IP is the IP of your Windows box.

Once you're in, type:

shutdown /f /t 0

To force a shutdown immediately.  Add /r to reboot.

More:
[http://www.computerperformance.co.uk/w2k3/shutdown.htm](http://www.computerperformance.co.uk/w2k3/shutdown.htm)

---

