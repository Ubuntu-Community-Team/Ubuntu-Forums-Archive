---
title: "Strange middle click in Firefox 1,5"
date: 2006-05-22
forum: General Help
---

### Post by VK2XCI on 2006-05-22
Hello all,

I finally found a script to install Firefox 1,5 which worked perfectly. BUT...

When I middle click on an open tab, instead of closing the tab it opens a Google Search page with...

cd Desktopchmod  x installnewfirefox.sh./installnewfirefox.sh

...as the search term. Now, this is  what I cut and pasted into a Kate window , to prompt me as  I ran the scrip in a terminal window.:confused: 

I can still close the tab with right click > Close Tab

Any clues?

Norm

Edit: Now this is really wierd.

When I middle click on the tab to close this tab... I was taken here 
[http://www.nasa.gov/centers/glenn/research/warp/warp.html](http://www.nasa.gov/centers/glenn/research/warp/warp.html)

Which is somewhere I have never been before! If it was windows I'd say it was a browser hijack!!!


Norm

---

### Post by glotz on 2006-05-22
Welcome to using Linux. Middle click usually pastes on Linux. You can disable this in Firefox. Type about:config to location bar and hit enter. Find middlemouse.contentLoadURL and double click it's value to false. That's it.

EDIT: What happened when you middle clicked is, you submitted whatever you had in your clip board to Firefox as an URL. When Firefox is given an inproper URL, Firefox makes a google "I'm feeling lucky" search using the input as keyword. This is why you get different results with different clip board contents. (And maybe even for consecutive clicks with same content, what ever google decides...)

---

### Post by aysiu on 2006-05-22
If you install an extension like Tab Mix Plus or Tabbrowser Preferences, you can configure the middle-click behavior as you want it to be.

---

### Post by VK2XCI on 2006-05-22
[QUOTE=glotz]Welcome to using Linux. Middle click usually pastes on Linux. You can disable this in Firefox. Type about:config to location bar and hit enter. Find middlemouse.contentLoadURL and double click it's value to false. That's it.

EDIT: What happened when you middle clicked is, you submitted whatever you had in your clip board to Firefox as an URL. When Firefox is given an inproper URL, Firefox makes a google "I'm feeling lucky" search using the input as keyword. This is why you get different results with different clip board contents. (And maybe even for consecutive clicks with same content, what ever google decides...)[/QUOTE]

Thank you for a consice explanation. I did figure it eventually!](*,)

---

