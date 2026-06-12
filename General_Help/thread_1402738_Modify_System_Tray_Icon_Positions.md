---
title: "Modify System Tray Icon Positions"
date: 2010-02-09
forum: General Help
---

### Post by A&#11375;A on 2010-02-09
Hello All,

Is there any way to modify the location of System Tray Icons (such as audio and WiFi) or possibly remove them?

On a somewhat related note, does anyone know how to disable the DropBox SystemTray icon?

tia

---

### Post by akand074 on 2010-02-09
right click on the notification area and uncheck "Lock to Panel", it is now free to move within the panel. You can also remove it by right clicking and selecting "Remove from panel". If you need to add it after removing it just right click and select "Add to panel" and find the notification area launcher.

I don't believe there is a way to move single icons because they are part of the notification area, nor can they be removed unless you close them/remove them from starting in the notification area.

---

### Post by A&#11375;A on 2010-02-09
> **akand074 said:**
> right click on the notification area and uncheck "Lock to Panel", it is now free to move within the panel. You can also remove it by right clicking and selecting "Remove from panel". If you need to add it after removing it just right click and select "Add to panel" and find the notification area launcher.

I don't believe there is a way to move single icons because they are part of the notification area, nor can they be removed unless you close them/remove them from starting in the notification area.

Thanks i don't know how i missed that.

Is there any way to rearrange the icons in the notification area?

edit:

that is to say can i change the order of them. Sometimes WiFi is to the left of Sound, sometimes it's to the right.

---

### Post by person9 on 2010-02-09
Actually the sound icon is not attached to the "Notification Area" itself (which contains wifi, battery meter, etc). The sound icon can be right clicked and you can choose "move" and move it freely. However the wifi, battery meter, and some other icons are all part of the Notification Area which moves as one unit. :)

---

### Post by A&#11375;A on 2010-02-09
> **person9 said:**
> Actually the sound icon is not attached to the "Notification Area" itself (which contains wifi, battery meter, etc). The sound icon can be right clicked and you can choose "move" and move it freely. However the wifi, battery meter, and some other icons are all part of the Notification Area which moves as one unit. :)

thats strange because it's moving as one unit

---

### Post by person9 on 2010-02-13
Sorry that didn't work for you! That's how it is on my computer. Maybe it's because I have Jaunty and you have Karmic, I noticed that afterwards. I have no idea, maybe it changed!

On my computer, the sound/volume icon can move by itself, and I can put it wherever I want on that panel.

The wifi icon, the firewall icon, and the battery meter all move together.

Good luck figuring this out!
:cool:

---

### Post by Esau on 2010-04-17
Hello.

I'm not a Linux expert or anything, but I think this solution might work for you, as it did for me with another notification icon issue I was having. 

If you go to System>Preferences>Start up Applications you'll notice that each Notification Area icon has it's own entry. Click on each one(wifi, bluetoooth, power-manager) that you want to change and edit the Command section to include a script to change the amount of time needed for each one to start up using this script: bash -c "sleep 20; /usr/bin/checkgmail" (obviously that's for my checkgmail icon). Changing the number after sleep to a lower number starts the notification faster/earlier/more to the right on the panel. 

Again, I haven't actually tried it with wifi,power manager. bluetooth, but I don't see why it won't work.

Hope this helps.

---

### Post by smoosh on 2010-06-13
Worked for me, thanks!

---

