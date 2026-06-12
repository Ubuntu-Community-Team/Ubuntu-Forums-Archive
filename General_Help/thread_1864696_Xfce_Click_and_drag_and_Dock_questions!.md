---
title: "Xfce Click and drag and Dock questions!"
date: 2011-10-19
forum: General Help
---

### Post by Rytron on 2011-10-19
Hi.

I am trying out Xubuntu 11.10 in VirtualBox. It looks pretty decent. Generally I dislike docks but the one in Xubuntu 11.10 is alright. Attached is a screenshot I took. How can I move the icons back to the middle?

I prefer the click and drag in GNOME2 to Xfce. In Xfce a click and drag acts like a copy & paste. In GNOME2 it acts like cut and paste. I prefer the latter. Can drag and drop settings be changed in Xfce? I know that you can click and drag + hold down Shift key to drag and drop but that is awkward.

---

### Post by hwttdz on 2011-10-19
Is that just a transparent panel?

You should be able to right click a panel->panel->panel preferences->then drag and drop the panel.  

Or you could set the width to 100% and add a spacer to both sides of the launchers you want on it.

---

### Post by Toz on 2011-10-19
I've never been able to drag/drop xfce panel layouts. 

Xubuntu uses "separators". You either need to add a new expanding separator at the beginning of the bar or if one already exists there, change it to an expanding separator.

Right-click the bar (panel) and choose Panel->Panel Preferences. This will display the "Panel" dialog box. Click on the "Items" tab. This will show the layout of all of the items on the panel. 

If the first one listed is a separator, click on it then select the "Edit" button (5th one down) on the right. Check the "Expand" box.

If you need to add a separator, click the "Add" button (3rd one down), select "Separator" and click on "Add" then "Close". The separator will have been added to the bottom of the list. Scroll down, select the new separator item, click on the "Up" button until the item moves to the top. Then follow the previous step to change it to an expanding separator.

---

### Post by Rytron on 2011-10-19
Just to clarify. When I mentioned drag and drop in the first post, I meant drag and drop from one folder to another or from a pen drive to a folder on the desktop. The dock is a separate issue.

---

### Post by Rytron on 2011-10-20
I sorted the icons stuck to the left problem [image attached].

How would I center icons with 100% dock length though?

---

### Post by Toz on 2011-10-20
Right-click Panel, choose Panel->Panel Preferences and change length to 100%.

---

### Post by gsmanners on 2011-10-20
> **Rytron said:**
> How would I center icons with 100% dock length though?

I like using the corners (you just flick the mouse in that direction and you're suddenly at that applet), but I suppose you could just have an expanding separator on each side. I don't know if it works, but you could try it. :D

---

### Post by Rytron on 2011-10-21
> **Toz said:**
> Right-click Panel, choose Panel->Panel Preferences and change length to 100%.

But then the icons are lobbed to the left hand side!

---

### Post by Rytron on 2011-10-21
> **gsmanners said:**
> I like using the corners (you just flick the mouse in that direction and you're suddenly at that applet), but I suppose you could just have an expanding separator on each side. I don't know if it works, but you could try it. :D

Depending on where i put the seperators, the icons either get pushed to the far left or far right. Is there a dot folder in the home directory that I can delete to get the dock back to default?

---

### Post by Elfy on 2011-10-21
Not sure if I'm reading you right here - but I have my dock set to Automatically increase in length with Length % at 1

Moved it to the middle and it stays there - guess it expands from the middle then

Might be barking up the wrong tree - not had enough tea yet.

---

### Post by gsmanners on 2011-10-21
> **Rytron said:**
> Depending on where i put the seperators, the icons either get pushed to the far left or far right. Is there a dot folder in the home directory that I can delete to get the dock back to default?

This looks like a job for: right-click on the panel, then select Panel / Panel Preferences... Then select the Items tab. That'll let you sort, add, delete, configure the items whatever way you want.

---

### Post by Toz on 2011-10-21
> **Rytron said:**
> Depending on where i put the seperators, the icons either get pushed to the far left or far right. Is there a dot folder in the home directory that I can delete to get the dock back to default?

If you put one expanding separator to the left of the launchers and one expanding separator to the right of the launchers, with the launcher size set to 100%, then the panel will be full screen wide and the launchers will be centered. Something like this:

- separator (expanding)
- launcher
- launcher
- launcher
- launcher
- launcher
- separator (expanding)

You can also place other non-expanding launchers inbetween launchers to insert a small gap between them (you can also further specify if this gap is transparent, separator, handle, dots, new line)

To reset all of the xfce panels to default, have a look at: [http://bevanscanterburylife.blogspot.com/2011/02/reset-xfce-panel.html]("http://bevanscanterburylife.blogspot.com/2011/02/reset-xfce-panel.html")

---

### Post by Rytron on 2011-10-21
> **forestpiskie said:**
> Not sure if I'm reading you right here - but I have my dock set to Automatically increase in length with Length % at 1

Moved it to the middle and it stays there - guess it expands from the middle then

Might be barking up the wrong tree - not had enough tea yet.

Yes, that works fine. But to have a 100% length dock, the icons wont stay centered. Not a big problem but it'd be nice to solve.

---

### Post by Rytron on 2011-10-23
> **Toz said:**
> If you put one expanding separator to the left of the launchers and one expanding separator to the right of the launchers, with the launcher size set to 100%, then the panel will be full screen wide and the launchers will be centered. Something like this:

- separator (expanding)
- launcher
- launcher
- launcher
- launcher
- launcher
- separator (expanding)

You can also place other non-expanding launchers inbetween launchers to insert a small gap between them (you can also further specify if this gap is transparent, separator, handle, dots, new line)

To reset all of the xfce panels to default, have a look at: [http://bevanscanterburylife.blogspot.com/2011/02/reset-xfce-panel.html]("http://bevanscanterburylife.blogspot.com/2011/02/reset-xfce-panel.html")

Ah yes. Like this. Sorted. ^_^

---

### Post by Rytron on 2011-10-23
> **gsmanners said:**
> I like using the corners (you just flick the mouse in that direction and you're suddenly at that applet), but I suppose you could just have an expanding separator on each side. I don't know if it works, but you could try it. :D

You were spot on! :)

At first I did not understand what an 'expanding' separator was.

Thank you gsmanners.

---

### Post by Rytron on 2011-10-23
> **forestpiskie said:**
> Not sure if I'm reading you right here - but I have my dock set to Automatically increase in length with Length % at 1

Moved it to the middle and it stays there - guess it expands from the middle then

Might be barking up the wrong tree - not had enough tea yet.

Thanks. That would also be an decent option.

---

### Post by Elfy on 2011-10-23
See - I was barking up the wrong tree, it was too early for me to realize you wanted a full size panel :)

---

### Post by Rytron on 2011-10-23
> **forestpiskie said:**
> See - I was barking up the wrong tree, it was too early for me to realize you wanted a full size panel :)

Not to worry. ;)

---

