---
title: "Gaia Online on Ubuntu [how to]"
date: 2010-01-10
forum: General Help
---

### Post by spiritofelric on 2010-01-10
Gaia on Ubuntu
I couldn't find any post on how to solve this, so I'm writing how i got it to work.

HERE IS A GUIDE TO GET IT WORKING IN UBUNTU

[http://gaiatech.sorrowind.net/wiki/index.php/How_to_make_zOMG_work_on_Ubuntu](http://gaiatech.sorrowind.net/wiki/index.php/How_to_make_zOMG_work_on_Ubuntu)

BELOW IS THE WINE SOLUTION.

1) Install Wine:
It can't run through native linux yet (not sure why flash behaves differently on OS!?)

[LIST]
[*]applications -> Ubuntu Software Center -> Search on Wine
[*]Or go here:  [http://www.winehq.org/](http://www.winehq.org/)
[/LIST]

2) Install Opera/Firefox through Wine
[i recommend opera because IE and other browsers seem to have issues like wineserver taking all processor power - opera runs really fast]

[LIST]
[*]You could use playonlinux ([http://www.playonlinux.com/](http://www.playonlinux.com/)) to install
[*]Or download the opera windows exe and right click, then select open with Wine ([http://www.opera.com/download/?os=windows&list=all](http://www.opera.com/download/?os=windows&list=all))  Recommend 9.64
[/LIST]

3) Enable Key holds (for rage powers in zOMG)

[LIST]
[*]System -> Preferences -> Keyboard
[*]Deselect "key presses repeat when key is pressed"
[/LIST]
or
[LIST]
[*]xset r off
[*]xset r on
[/LIST]

4) Install Flash on Wine
When you first visit Gaia, it will prompt you to download flash.  Click run install, then close opera while install prompt is up (or it won't integrate it) or download flash install and right click then run in Wine.

** I'll add more as i test out the features, but so far it runs well and runs fast.

---

### Post by ell02 on 2010-04-04
thanks

---

