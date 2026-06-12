---
title: "Turn Off Touchpad Scrolling for Changing Between Desktops"
date: 2011-04-24
forum: General Help
---

### Post by leegold on 2011-04-24
Hi,

Using Lubuntu 10.10 on a laptop with a Synaptics touchpad. Moving the finger along the right edge of the touchpad acts as a scroll wheel. If the cursor is not in any app window but is in open desktop area - then this scrolling action will transport one to a different desktop. I have two desktops enabled so by moving the the finger along the side up/down I go from Desktop1 to Desktop2 and back.

This deadly for me and causing much hair pulling. I am in the middle of doing something and desktop will change. No matter how careful I am this eventually happens. So for the sake of sanity I have only one desktop.

I'd like multiple desktops but I need to turn-off this scrolling feature. I've seen some hacks in config files but they either don't work or have side effects. I want to keep the scrolling in windows were the touchpad scrolling really helps. I just want to turn-off the scrolling between desktops only. 

I can't fing a GUI in Lubuntu to do this. Is there a way that work that anyone knows?

---

### Post by cavalier911 on 2011-04-26
Tested Lubuntu 10.04 Lucid on Dell Laptop.
File Manager/View/Show hidden files
Go to ~/.config/openbox
Make backup:
RightClick Copy lubuntu-rc.xml 
Paste/Rename Filename:lubuntu-rc.xml~ 
Edit/Save:
RightClick lubuntu-rc.xml Open With Leafpad
Options/Check Line Numbers
Scroll to line 642:
Change
<mousebind button="Up" action="Click">
To
<**!--**mousebind button="Up" action="Click">
Scroll to line 659:
Change
</mousebind>
To
</mousebind**--**>
File/Save
Logout/in to this user
Scrolling with touchpad or mouse wheel with cursor on the desktop does nothing.
Scrolling with the cursor in app window with vertical scroll bar scrolls.

In case the line numbers are different your commenting out this block of xml:
<!--mousebind button="Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
      <mousebind button="A-Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="A-Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
      <mousebind button="C-A-Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="C-A-Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind-->

---

