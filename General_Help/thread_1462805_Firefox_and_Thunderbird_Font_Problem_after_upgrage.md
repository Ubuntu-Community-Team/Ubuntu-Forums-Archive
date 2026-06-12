---
title: "Firefox and Thunderbird Font Problem after upgrage"
date: 2010-04-26
forum: General Help
---

### Post by selimaky on 2010-04-26
I am using Karmic Koala and when i upgrade my firefox to 3.6 series or my thunderbird to 3 , their fonts do not work properly. I installed as shown in this link; [http://ubuntuforums.org/showthread.php?t=1379961](http://ubuntuforums.org/showthread.php?t=1379961).
The fonts are not clear as before. What should i do to use new ones with better fonts?

---

### Post by selimaky on 2010-04-26
This isn't going to work, i have tried already. Last time i upgraged my firefox, i didn't know how to use previous firefox and i reinstalled ubuntu because i couldn't stand using firefox with bad fonts.

---

### Post by lovinglinux on 2010-04-27
[See this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-display-weird-fonts,-with-greenish-blue-shadows,-after-update--2)

---

### Post by montuos on 2010-05-02
I had the same (or similar) font problem after finally upgrading to Karmic last week, even after upping my system font settings, but my ~/.fonts.conf was exactly the same as the one lovinglinux linked to.  The way I fixed it was creating a [userChrome.css]("http://kb.mozillazine.org/UserChrome.css") to add a [Global UI font]("http://kb.mozillazine.org/Pane_and_menu_fonts#Global_UI_font").   (Or maybe I mean "recreating"; I had *thought* I already that file!)

---

