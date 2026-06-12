---
title: "Internet help."
date: 2010-09-29
forum: General Help
---

### Post by Ninja_ on 2010-09-29
Okay, so here's the sitch. My internet hasn't been paid... So  until I get my check Friday I am using my phone to tether. Problem being that said phone creates an Ad-Hoc network. I need to make it an infrastructure network so I  can connect my ps3. I can't do an ethernet bridge because I only have  one router, and I am not putting any software onto it. I am running K/Ubuntu Linux 10.04. 



So I have  my laptop wirelessly connected to my phone, then I have it wired to my  router. I can not set my laptop up to be an Ad-Hoc connection(which is  where I believe my problem lies, because therefore no internet is getting to  the router, right?) if you know how you can help me out here, it would be  GREATLY appreciated.

---

### Post by spcwingo on 2010-09-30
When you wired from your laptop to your router did you tell Ubuntu what you wanted it to do with it.  To do just that, right-click on your network manager applet in your system tray and select "edit connections".  On the "Wired" tab select your interface then select "edit".  Under the "IPv4 Settings" tab in the dropdown beside "Method" select "Shared to other computers".  After that open a terminal and issue this command:

```
sudo /etc/init.d/networking restart
```

If that doesn't work just reboot.

BTW, be sure that the ethernet cable you use from your laptop to the "in" port of the router is a crossover ethernet cable.  :)

---

