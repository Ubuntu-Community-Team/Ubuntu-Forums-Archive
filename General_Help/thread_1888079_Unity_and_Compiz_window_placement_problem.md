---
title: "Unity and Compiz window placement problem"
date: 2011-11-28
forum: General Help
---

### Post by startling on 2011-11-28
Running Compiz under 11.10, I get a problem when launching applications. They are launched in the very top left corner of the screen, which means they are partially hidden under the launcher and the bar at the top. Therefore the Close, Minimize and Maximize buttons in an application's title bar are hidden underneath Unity's bar at the top and I cannot click them.

Is there any way I can change this so that newly launched programs' windows are launched at, say, 50 pixels from the top and left corners of the screen?

---

### Post by roger_1960 on 2011-11-28
Hi

I solved this problem by setting the "reveal mode" for the unity plugin in ccsm to 'bottom left"  Launcher only appears when mouse goes to bottom left. Normally I use the widows key to get the dash and launcher.

---

### Post by kherring7383 on 2011-11-28
If you're looking for a way to launch your apps window in the center of the screen, checkout this Compiz setting at this wiki link. [http://wiki.compiz.org/Plugins/Place](http://wiki.compiz.org/Plugins/Place)

---

### Post by startling on 2011-11-29
Thanks for the replies. roger_1960, the launcher isn't really the problem - it's the panel bar at the top that's the problem. The title bars of programs are hidden under it.

kherring7383 - thanks for the link. I can't seem to make Window placement work. I've tried following the instructions but I suspect I'm too stupid to get it right! As for centering all windows this would be almost as bad as the current behaviour as then I'd have to manually move each window every time I launch a program. 

Is there any way to save program and window sessions in Ubuntu Unity? This would be a major productivity boost if it were possible.

---

### Post by roger_1960 on 2011-11-29
Hi again

Yes, I misunderstood a bit through not reading carefully enough!

In compiz - window management - place windows do you have "placement mode" set to "smart"?  In unity 3D I don't have the problems you are describing.  The window title and buttons appear in the top panel rather than under it.  Does this happen with all applications?

---

### Post by startling on 2011-11-30
Thanks Roger. Yes I do have "placement mode" set to "smart".

I think I *am* too stupid to use the Compiz Place Windows plugin! In the Fixed Window Placement tab, after setting class=nautilus to new x and y positions, I wondered why it wasn't working. Then I saw that I hadn't checked the "Enable Place Windows" box in the left hand pane...  I stupidly assumed that by adding a new setting it would automatically enable the feature.

New Nautilus windows now appear in the visible part of the desktop. However, the Place Windows plugin does not seem to work for Filezilla, which always launches maximised for some strange reason. 

Is there any way to make Unity remember window placement and size settings?

---

### Post by Maximus_ARNP on 2012-05-03
I had the same problem on Xubuntu 12.04 with Compiz. It is solved with your instructions. Thank you so much.

For anyone's help, **_here is [B]how to fix the problems in Xubuntu:**_[/B]
[COLOR="DarkRed"]**Settings --- Compiz Setting Manager --- Windows Management --- Place Windows --- Enable --- Placement mode --- Smart.**[/COLOR]

With SMART mode, Compiz will place a new application windows on screen space with an attempt to avoid overlaping as much as possible.

Very helpful.

Again, thank you so much.

Keywords: left top upper corner window placement problem xubuntu 12.04 compiz

---

