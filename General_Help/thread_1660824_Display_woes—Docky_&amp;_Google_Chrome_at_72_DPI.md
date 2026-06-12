---
title: "Display woes—Docky &amp; Google Chrome at 72 DPI"
date: 2011-01-05
forum: General Help
---

### Post by ajblue98 on 2011-01-05
Hey all,

I'm running Maverick Meerkat (x64), and my screen is set to 72 logical DPI (which I prefer for working with graphics).  As a result, the dock item label font size in Docky, and the tab and address bar suggestion drop-down text in Google Chrome, both have shrunken to almost unusable sizes.

What I'd like to know is how to fix this issue?  Preferably, I'd like to change the point size of this text.  As secondary and tertiary options, redefining the text sizes in terms of pixels instead of points, or changing the DPI of just the individual programs would work, also.

I haven't found a solution to either of these online, but I'm still hoping that a simple preferences fix in gconf-editor will work.  Any thoughts?

Your help will be appreciated greatly!

&#8212;AJBlue98

[COLOR="Red"]**_Edit/Update_**[/COLOR]

Incidentally, it occurs to me that this could be fixed by changing the source code so that font sizes for interface elements are calculated to adjust automatically for the screen DPI using a proportion.  Specifically, since the default screen DPI for Ubuntu is 96, and if we use the string variables **$runtimeDPI** to represent the screen DPI used when the program is running and **$defaultTextSize** to represent the correct font size used to display the text in question on a system with the logical DPI set to the default of 96, then the following formula should suffice.

(96 * **$defaultTextSize**)/**$runtimeDPI**

What do you think?

Thanks in advance for the help!

&#8212;AJBlue98

---

