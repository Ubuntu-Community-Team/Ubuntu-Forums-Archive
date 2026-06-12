---
title: "lost taskbar in 10.04"
date: 2010-05-01
forum: General Help
---

### Post by Disident on 2010-05-01
Hello everyone!
Yesterday I upgrade my Kubuntu to 10.04 LTS (Lucid Lynx) and I lost taskbar. Besides, I can't right-click on desktop. In fact I can, but nothing happens. Is that some Plasma problem? I red that Kicker is replaced by some Plasma feature. Could it be because of Conky (some desktop layouts)? I tried to prevent it, but I can't. I killed all Conky instances, and removed it from .kde/Autostart, but it still runs on every start-up.
Please someone help.

---

### Post by Disident on 2010-05-01
It seems, something's wrong with Plasma.
I have installed:
> *$aptitude search plasma|grep ^i*
i   kdebase-plasma                  - Transitional package for plasma-widget-fol
i A libplasma-applet-system-monitor - Library for the plasma system monitor     
i A libplasma-geolocation-interface - Library for the plasma geolocation        
i   libplasma3                      - library for the KDE 4 Plasma desktop      
i A libplasmaclock4                 - Library for the plasma clock              
i A libplasmagenericshell4          - shared elements for all the plasma shells 
i   plasma-dataengines-addons       - addons for KDE 4 Plasma - data engines    
i   plasma-dataengines-workspace    - KDE 4 base workspace Plasma data engines  
i A plasma-scriptengine-javascript  - javascript script engine for Plasma       
i   plasma-scriptengine-python      - Python script engine for Plasma           
i   plasma-widget-facebook          - Plasma Widget for Facebook Updates        
i   plasma-widget-folderview        - Folder View Plasma widget                 
i   plasma-widget-googlecalendar    - Plasma Widget for Google calendar         
i   plasma-widget-kimpanel          - addons for KDE 4 Plasma - universal input 
i A plasma-widget-kimpanel-backend- - addons for KDE 4 Plasma - universal input 
i   plasma-widget-lancelot          - addons for KDE 4 Plasma - lancelot widget 
i A plasma-widget-message-indicator - A Plasma applet to display message indicat
i   plasma-widget-networkmanagement - Network Management widget for KDE4 Plasma 
i   plasma-widget-quickaccess       - An alternate folder display plasma widget 
i   plasma-widgets-addons           - addons for KDE 4 Plasma - widgets         
i   plasma-widgets-workspace        - KDE 4 base workspace Plasma widgets and co

and when I Alt+F2 tzpe Plasma, some window opens, I can't choose anything, and when I click OK, nothing happens.
*$kquitapp plasma* gives: <unknown program name>(3972)/: "Application plasma could not be found using service org.kde.plasma and path /MainApplication."

---

### Post by Disident on 2010-05-01
Ok I didn't have installed plasma-desktop.

---

### Post by coldbluesteel on 2010-05-07
Gnome is doing the same thing. I just got an update notification this morning, ran it, rebooted and now my panel is there, but taskbar does not function. Just a blank bar and when I minimize a program it just goes away.

How can I fix this?

---

### Post by xscd on 2010-05-12
Just right-click on the taskbar, click "Add to Panel ..." and add "Window List" :)

---

