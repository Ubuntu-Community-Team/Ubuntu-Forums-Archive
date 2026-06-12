---
title: "Deleted volume icon, top right"
date: 2011-03-02
forum: General Help
---

### Post by jezzyjez on 2011-03-02
I accidently deleted my speaker(volume) icon on the top right of the screen, around the date. I cant seem to get it back ive tried right clicking on the menu or using ubuntu tweak but cant seem to get it back.

Any help would be great

Thanks
Jez

---

### Post by DanneStrat on 2011-03-02
> **jezzyjez said:**
> I accidently deleted my speaker(volume) icon on the top right of the screen, around the date. I cant seem to get it back ive tried right clicking on the menu or using ubuntu tweak but cant seem to get it back.

Any help would be great

Thanks
Jez

Right-click the panel and select "add to panel".

Then select the "indicator applet".

That should bring it back.

---

### Post by jezzyjez on 2011-03-02
that's put in the battery and email, but not the volume.

---

### Post by prshah on 2011-03-02
> **jezzyjez said:**
> that's put in the battery and email, but not the volume.

Press Alt-F2, then give the command ```
gnome-volume-control-applet
``` (Note the "-applet"; without that, it will launch some other program).

---

### Post by jezzyjez on 2011-03-02
Ok this gave the following error.

Could not open location 'file:///home/jez/gnome-volume-manager-applet'

Error stating file '/home/jez/gnome-volume-manager-applet': No such file or directory

---

### Post by AgentY on 2011-03-02
Press Alt-F2, then give the command ```
gnome-volume-control-applet
``` (Note the "-applet"; without that, it will launch some other program).[/QUOTE]

Cheers, this resolved my issue! Ensure you run it by using alt+f2 as terminal will enable it but only until the the terminal session is closed.

---

### Post by Frogs Hair on 2011-03-02
Try to restore panels to default.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by DanneStrat on 2011-03-02
> **jezzyjez said:**
> that's put in the battery and email, but not the volume.

I had a closer look at it and

I think it should be the "notification area"

applet. Try to add it to the panel.

---

### Post by temman on 2011-03-02
[SIZE=2]In terminal type "gnome-volume-control-applet" without the quotes!
This will make the volume icon reappear.
To keep it there leave terminal open for the time being.
Go to System / Preferences / Startup Application hit the "add" tab the add startup  program window shows up.
In the 'Name" window type Audio
In the " Command" window copy and paste the code you still have in Terminal 
In the " Comment" window type Icon Hit Add and reboot your pc.

[/SIZE]

---

### Post by amitpokhrel on 2011-03-02
Try this link. It helped when i did the same mistake....

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

