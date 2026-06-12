---
title: "Shift + home keys not working"
date: 2010-06-20
forum: General Help
---

### Post by =CrAzYG33K= on 2010-06-20
Allright, I think it has been covered before, I'm not able to dig up or find anything on these.

I have a Lenovo G550 Notebook, with a US keyboard layout (dedicated Numpad on the right). Now the quirk is.. the 'Home', 'End', 'PageUp' & 'PageDn' keys on the numpad do work in Ubuntu (They double up as 7, 1, 9 & 3 respectively, when Numlock is turned on), but what doesn't is Shift + 'Home', 'End', 'PageUp' or 'PageDn'.. Is there a setting to do this? I just have gotten used to it in Windows (for say, easily removing the typed in URL on a web-browser, using the keyboard), it seems like alls' lost without it :(

---

### Post by megamandos on 2010-06-20
well, I am pretty sure in linux those are browser dependent, if you cant find it in System>Preferences>Keyboard Shortcuts then I would say try looking in the browsers preferences. If not there, then I guess you are stuck scrolling like the rest of the world.

---

### Post by technocp on 2010-06-20
> **=CrAzYG33K= said:**
> Allright, I think it has been covered before, I'm not able to dig up or find anything on these.

I have a Lenovo G550 Notebook, with a US keyboard layout (dedicated Numpad on the right). Now the quirk is.. the 'Home', 'End', 'PageUp' & 'PageDn' keys on the numpad do work in Ubuntu (They double up as 7, 1, 9 & 3 respectively, when Numlock is turned on), but what doesn't is Shift + 'Home', 'End', 'PageUp' or 'PageDn'.. Is there a setting to do this? I just have gotten used to it in Windows (for say, easily removing the typed in URL on a web-browser, using the keyboard), it seems like alls' lost without it :(
try setxkbmap command on the terminal and see if every thing goes right

---

### Post by =CrAzYG33K= on 2010-06-20
> **technocp said:**
> try setxkbmap command on the terminal and see if every thing goes right

No go :(

No other Ubuntu user faces this problem ???

**EDIT:**
It looks like it works when Numlock is on, for some weird reason :(
Is my keyboard all barfed up?

---

### Post by =CrAzYG33K= on 2010-07-01
Finally found out the solution :

System -> Assistive Technologies
-> Keyboard Accesibility -> Layouts
-> Layout Options -> Miscellaneous compatibility options
-> Shift with numeric keypad keys works as in MS Windows

Reference : [http://ubuntuforums.org/showthread.php?t=60336](http://ubuntuforums.org/showthread.php?t=60336)

This community just rocks!

---

### Post by JohannesJo on 2011-10-25
This is great. Worked also with my Easy Note TJ65 and Ubuntu 11.10. =)

Edit: I would suggest to rename the Topic to "shift + numpad keys (home, end, ...)" instead of home (as it aint the only key affected).

---

