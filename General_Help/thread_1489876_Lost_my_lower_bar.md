---
title: "Lost my lower bar"
date: 2010-05-21
forum: General Help
---

### Post by phase constant on 2010-05-21
Not sure what happened but I lost the lower task bar.  So when I minimize windows they disappear and I have to use alt-tab to navigate to them.

Someone help please?

---

### Post by cain071546 on 2010-05-21
right click on the existing panel and make new panel

---

### Post by Elfy on 2010-05-21
You'll need to add windows list to the panel and show desktop if you want it back to the default.

Right click the new panel then Add to Panel

---

### Post by phase constant on 2010-05-21
Ok that worked except when I added show desktop and windows list...

The show desktop is center aligned on the bar, like right in the center.

And the windows start to the right of that.  So I'm getting like 1/2 use out of it.

Thanks for the help!!!!

EDIT- ok sorry I figured out how to move. THANKS!

---

### Post by phase constant on 2010-05-21
Is the only way to burn a DVD from an .avi through terminal and all those commands.  

There is no easy program to use... like on windows I used convertxtodvd and it wasy easy peasy.

---

### Post by phase constant on 2010-05-21
Now I've got a new problem.

Seems I created 3 of them...?

---

### Post by SlidingHorn on 2010-05-21
> **phase constant said:**
> Is the only way to burn a DVD from an .avi through terminal and all those commands.  

There is no easy program to use... like on windows I used convertxtodvd and it wasy easy peasy.

Try taking a look @ DeVeDe.  That will convert it to MPEG2 and allow you to burn to DVD.  You can then use Brasero (or your burning program of choice) to burn the disk.

```
sudo apt-get install devede
```

---

### Post by SlidingHorn on 2010-05-21
> **phase constant said:**
> Now I've got a new problem.

Seems I created 3 of them...?

Just right click on the two you don't want and select "Remove from panel"

---

### Post by Chesamo on 2010-05-21
Right-click on two of them; remove from panel.

[img]http://imgur.com/uN6b2.png[/img]

---

### Post by SlidingHorn on 2010-05-21
> **Chesamo said:**
> Right-click on two of them; remove from panel.

Had to show me up with your fancy screen shots....jerk!!  ;) kidding..

---

### Post by phase constant on 2010-05-21
Thanks guys I got rid of the extras.

Checking out DeVeDe now.

---

### Post by AlanR8 on 2010-05-21
One of the first things I do on a clean install is get rid of the bottom bar. I then install Cairo Dock!

That's one of the great things about Ubuntu, flexibility and freedom of choice. I was working today on a colleague's Acer net book running XP. 

SLOW compared to this Compaq Mini running Lucid.

---

### Post by Chesamo on 2010-05-21
> **SlidingHorn said:**
> Had to show me up with your fancy screen shots....jerk!!  ;) kidding..
<3 I just happen to have the screencap tool bound to a hotkey, and since I'm at work I didn't have much time to explain in words ;-)

---

### Post by dustinmarlowe56 on 2010-05-21
there is a custom script  that i have which will reset your panels to how they were after the install. its handy for me because i have messed up and been frustrated by the panels before.


do the following:

$ vi resetpanel

edit that file to read:

gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

save the file, then run:

chmod +x resetpanel

sudo mv resetpanel /usr/bin/

resetpanel



now whenever you have an issue with your panel and want to get back to the original just open up a terminal and run the resetpanel command.

---

