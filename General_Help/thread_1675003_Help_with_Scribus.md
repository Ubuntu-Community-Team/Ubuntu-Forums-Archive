---
title: "Help with Scribus"
date: 2011-01-24
forum: General Help
---

### Post by SteveHillier on 2011-01-24
Hey guys, not strictly an Ubuntu problem but who knows who I might reach.  However Scribus 1.3.3.13 is in the Ubuntu repositories.

I am an experienced DTP user having started in the mid-late 80s with a GST offering on DOS.  I have used Pagemaker, Publisher, Serif PagePlus all in various releases.
However I simply cannot get started with this product.  I have looked at the 'getting started' documentation but the interface is so different to the one I have got.  Menu options not present, options in different menus.
But the biggest problem is that I cannot enter any text in the story editor - well not strictly true, I can enter all digits from main keyboard and number keypad, I can enter all the special printing characters but can I enter alpha characters - NO.  Upper or lower case makes no difference, and by the way it is this keyboard I am trying to use and you can see I can enter alpha characters in this forum!
I just googled 'giving up on scribus' and found thread on this forum on a similar track, so I thought I would chance my arm.
If any one can point me in the right direction I would be grateful.
ps, the Sribus wiki doesn't offer much help either.
Many thanks
Steve

---

### Post by notbitmonk on 2011-02-12
I have used Scribus to do business cards, some flyers and a doctoral dissertation (a friend's). So far I have not encountered the problem you are referring. I have used the stable version (the one you are using) and currently use the development version from Ubuntu Software Source (different from latest development version on Scribus website) on 10.04. What I think that is happening is that the font that you are using might contain only numbers. Try using a font like DejaVu or Liberation (pre-installed on Ubuntu) to see if there is a change. To do that:
[LIST=1]
[*]Select the text frame
[*]If the properties tab is not open, click F2
[*]Select the Text "tab"
[*]Change the font
[/LIST]
This is a "dirty" way to do it because Scribus is very much about using paragraph styles to manage the "view" of the document. You can click F3 to open the Style window and create several paragraph styles to see how text changes. Scribus can add sample text. You can do that by right clicking the text frame and selecting "Sample text".

---

### Post by SteveHillier on 2011-02-24
Many thanks to notbitmonk.
It seems that the default font for this program is lohit gujarati.  The hint about the property frame showed this.
I have now used preferences to avoid this font and start in a much more suitable font for an English language user.

---

