---
title: "some apps don't like wide display?"
date: 2010-04-29
forum: General Help
---

### Post by _Duhhh on 2010-04-29
I'm running 9.10 with a Radeon X300 video. Two displays, one is 1920x1200, the other is 1600x1200. I'm finding that some apps don't like to be too far to the right (anything past about 2600 x-resolution). If I move a window that far to the right, some of the controls are blank. A good example is OpenOffice. If I move an OO app too far to the right, the text in the main menu items will all be blank. All I see are the icons and the underscores for the keyboard shortcuts. There are other apps that do it, but OpenOffice is the most popular.

I tried re-configuring my displays, and it is always the one on the right. If I stack them top-to-bottom, I don't see the problem. If I reduce resolution, the problem diminishes, until I reduce the total x-resolution to below about 2600.

Suggestions would be appreciated.

---

### Post by RTrev on 2010-04-29
If I'm reading this correctly, the problem is only with "some apps" and not all?

Sounds like it would have to be an issue with those specific apps, and not with your setup.

If you can zero in on what the problem apps have in common, and what the ones without problems have in common, maybe a bug report can result.

I've never had two displays that wide, but with two 1680x1050 I never ran into it. <g>

---

### Post by _Duhhh on 2010-04-30
Yes, it is only with "some" apps. OpenOffice has problems with the menu, but not with the text in a document. SlickEdit has a problem with menus AND main window text. Firefox doesn't have a problem at all. Gimp is good. I have a Windows app I compiled with MONO and it has a problem.

So, there is definitely a problem with some graphics API that these apps share. What that is, I don't know. How many people have at least 2600 pels of x-resolution? Apparently not enough to see this problem.

---

### Post by _Duhhh on 2010-06-11
Upgrading from Karmic to Lucid made the problem go away. :p

---

### Post by RTrev on 2010-06-11
> **_Duhhh said:**
> Upgrading from Karmic to Lucid made the problem go away. :p

Ah, good!  Maybe it was some library that the problem apps were calling which just got updated.  As long as it's fixed. <g>

---

