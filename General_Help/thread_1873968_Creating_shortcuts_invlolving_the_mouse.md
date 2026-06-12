---
title: "Creating shortcuts invlolving the mouse"
date: 2011-11-02
forum: General Help
---

### Post by samjad51 on 2011-11-02
Hi,

I was just wondering if there is anyway I can create a shortcut to change my volume by: Holding Left Click on the mouse + mouse wheel down/up to turn volume up or down.

I have become accustomed to using Volumouse on the windows platform, which offers this feature, and its become like a habit now. So was wondering if there is any way to do the above.


THanks in advance :)

---

### Post by notgary on 2011-11-10
Unfortunately there's no easy way to remap mouse buttons under any variant of Linux, and it's even harder to do ti for non-standard functinoality such as volume control. 

Xorg, the part of the display stack responsible for controlling mouse. keyboard, etc iterction with the system, expacted the mouse to have certain functionality attached to each button. For example, it expects the first button on the mouse to be used for selecting things on the screen, the second one (a click of the scroll wheel in many cases) to be for pasting, and the third one (the right button) to be a context menu. You can, without an inordinate amount of hassle, remap these particular features to different buttons, and there are ways to get mice up and running that have more than three buttons.

Attaching mouse input to non-standard features such as volume may be wuite problematic, but unfortunately I don;t know any more than that. There are some  links on the subject of mouse remapping that you may find useful. Sorry I couldn't give you an actual solution.

[https://lists.ubuntu.com/archives/kubuntu-users/2006-November/011080.html](https://lists.ubuntu.com/archives/kubuntu-users/2006-November/011080.html)
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)
[http://www.alanbriolat.co.uk/2010/04/remapping-mouse-buttons-on-ubuntu-lucid/](http://www.alanbriolat.co.uk/2010/04/remapping-mouse-buttons-on-ubuntu-lucid/)
[http://www.alanbriolat.co.uk/2009/06/mouse-button-remapping-with-hal/](http://www.alanbriolat.co.uk/2009/06/mouse-button-remapping-with-hal/)
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

