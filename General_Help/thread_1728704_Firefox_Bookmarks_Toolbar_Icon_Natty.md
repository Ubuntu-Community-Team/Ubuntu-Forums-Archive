---
title: "Firefox Bookmarks Toolbar Icon Natty"
date: 2011-04-14
forum: General Help
---

### Post by aaaaalex on 2011-04-14
For some reason the bookmark menu tool bar icon is missing form Firefox in Natty. It is visible when i select customize on the too bar - as soon as the customize menu is closed it disappears again.

I found somebody stating that this is caused by the ubufox (xul-ext-ubufox) package. Sadly the problem persists after removing that. 

I tried looking into about:config but could not really find anything there.

---

### Post by lovinglinux on 2011-04-14
Right-click on any toolbar and tick the option to display the Bookmarks menu. If that is already ticked, then click "Customize" and then "Restore Default Set". this will reset all your toolbars and icon positions.

---

### Post by aaaaalex on 2011-04-14
Nope :-D

I already tried that. Maybe i have not been explicit enough...

The first screen shot shows the tool bar before and after the customize was opened. The second one while the customize menu is open.

---

### Post by lovinglinux on 2011-04-14
> **aaaaalex said:**
> Nope :-D

I already tried that. Maybe i have not been explicit enough...

The first screen shot shows the tool bar before and after the customize was opened. The second one while the customize menu is open.

I know. That happened to me also with the Navigation Toolbar. It shows in the customize dialog, but not after closing it. Did you click the "Restore Default Set"?

If that doesn't help, close Firefox, open the profile folder (*~/.mozilla/firefox*) and delete the file *localstore.rdf*. You should get your toolbar back.

---

### Post by aaaaalex on 2011-04-14
I have the bookmarks tool bar no problem there but i dont want it. After installing FF 4 in Maverick i noticed the drop down bookmarks menu that lives in the navigation tool bar and found it quite handy.

I am suspecting that this is a Ubuntu modification to FF not to show it. If i drag the bookmarks icon into the navigation tool bar its there, but its not the drop down menu you can see in my second screen shot - instead it opens the bookmarks side bar. :-(

---

### Post by lovinglinux on 2011-04-14
> **aaaaalex said:**
> I have the bookmarks tool bar no problem there but i dont want it. After installing FF 4 in Maverick i noticed the drop down bookmarks menu that lives in the navigation tool bar and found it quite handy.

I am suspecting that this is a Ubuntu modification to FF not to show it. If i drag the bookmarks icon into the navigation tool bar its there, but its not the drop down menu you can see in my second screen shot - instead it opens the bookmarks side bar. :-(

I just tested on a clean profile and indeed it disappears when placed in the navigation toolbar. Drag it to the tabs toolbar, the bookmarks toolbar or the add-ons toolbar and it will persist.

Alternatively, hide the Menu Bar and it will be displayed, along with the Firefox menu.

---

### Post by aaaaalex on 2011-04-15
Thanks. I had not tried that. I guess i can live with the Icon living in the bookmarks tool bar. ;-)

P.S. Can't hide the menu bar in natty

---

### Post by lithopsian on 2011-04-15
It is worth noting that there are two identical bookmarks toolbar buttons (OK, one has text and one doesn't, but you might not have text turned on).  One has the bookmarks menu dropdown, the other opens the bookmarks sidebar.

I see both on every toolbar I've tried but I don't have Natty.  Are you testing with the repository version of Firefox?  With or without Ubuntu extensions?

---

### Post by lovinglinux on 2011-04-15
> **aaaaalex said:**
> Thanks. I had not tried that. I guess i can live with the Icon living in the bookmarks tool bar. ;-)

P.S. Can't hide the menu bar in natty

I am using Kubuntu Natty and I can hide it. Is it because the global menu available to Ubuntu users?

---

### Post by aaaaalex on 2011-04-18
> **lovinglinux said:**
> I am using Kubuntu Natty and I can hide it. Is it because the global menu available to Ubuntu users?

I should think so... But i am happy now :-D

---

