---
title: "change keyboard  from UK to US using system &gt; preferences &gt; keyboard &gt; layouts"
date: 2009-11-25
forum: General Help
---

### Post by rutiezer on 2009-11-25
Changing keyboard layout from UK to USA on Ubuntu 8.04.

Did system > preferences > keyboard > layouts 
and saw only United Kingdom listed.

Clicked   Add > Layouts 
and selected "+Add" and from "choose a layout" under layouts drop down list. In list of countries found "USA" then selected "+Add" and USA is added to the list below United Kingdom. 

Clicked on USA and over on right-hand side under Default the circle is highlighted. Sometimes circle does not get highlighted. If I click on "Separate layout for each window" the un-highlighted circle get highlighted, and click again and it stays that way.
 

When I type in the box labeled "Type to test settings" the keyboard is still United Kingdom since for the numbers above the letters the upcase for 1, 2, 3 is still !, ", £, respectively.

Believe I followed this method before and got layout to change.

Ideas about what I am doing wrong?

---

### Post by blazemore on 2009-11-25
Can you not remove the UK layout, preventing it from being reselected?

---

### Post by t0p on 2009-11-25
I once had a similar problem to yours, but the other way round: trying to switch from US to UK layout.  I thought it wasn't changing.  Then I logged out (for another reason), logged in again, and the keyboard setting had changed.

Well, that's my memory of it anyway.  I'm not definitely sure it was the logout/login that sorted it, but that's how it seemed to me at the time.  Worth a try?

---

### Post by audiomick on 2009-11-25
> **t0p said:**
> I once had a similar problem to yours, but the other way round: trying to switch from US to UK layout.  I thought it wasn't changing.  Then I logged out (for another reason), logged in again, and the keyboard setting had changed.

Could be something in that; the keyboard setup is part of the gconf file ( config file for the GUI ), which gets read in when you log on. Log out doesn't mean restart, just log off and back on again. Funny, though, that the keyboard test brings the wrong result....

---

### Post by rutiezer on 2009-11-26
Tried logging out, even rebooting with no change to the keyboard characteristics.

When I click between United Kingdom and USA don't see any Layout selected, that is, the circle highlighted. When USA is highlighted type in box "Type to test settings" and see United Kingdom layout for upper 1, 2, 3 as previously described.

Am concerned that if I remove United Kingdom layout then I won't be able to type at all. Is this a valid concern or not a problem?

Maybe I should look at the gconf file to see what it looks like?
When I run gconf-editor there are lots of items there.
Does one of them specify keyboard layout?
Using post
[http://ubuntuforums.org/archive/index.php/t-704554.htm](http://ubuntuforums.org/archive/index.php/t-704554.htm)
and this line in the post
gconftool-2 --type string --set /desktop/gnome/peripherals/keyboard/kbd/layout "layout name"
I click on each item in order: desktop, gnome, peripheral, keyboard, kbd, and see in layouts the value [gb,us], in options the value 
[grp grp:alts_toggle] and in overrideSetting a check mark for the value.

Then what?

---

### Post by rutiezer on 2009-11-26
Problem solved.

The suggestion to delete the Great Britain keyboard layout after adding the USA keyboard succeeded in changing the keyboard layout from Great Britain to USA. 

This Ubuntu was just installed and did not notice installation procedure asking what sort of keyboard layout was wanted.

Thanks for the responses and thanks blazemore.

---

