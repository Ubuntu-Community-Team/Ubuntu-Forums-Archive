---
title: "Lubuntu system font very very small"
date: 2012-01-02
forum: General Help
---

### Post by finny388 on 2012-01-02
I just fresh installed Lubuntu 11.10 and seems fine but when I hook it up to my Samsung LCD TV by VGA the fonts become impossibly small while the icons are just fine.

I don't know how to take a screen shot in Lubuntu to post a pic.

This is very frustrating to trouble shoot when you can't read the screen.

Lubuntu installed nVidia drivers during installation. I set it to Separate X /Resolution Auto and disabled the laptop display.

It is an Asus 1015PN

Any ideas?

---

### Post by Dennis N on 2012-01-02
Screen Shot - just press the Print Screen Key and it will be done in the background and placed in your home folder with a time stamp.

System Fonts - if you mean that which is used in the file manager, main menu and window menus, that is set in Preferences > Customized Look and Feel > Widget Tab. Look on the lower right - called default font. Desktop Icon font can be set by right-clicking on the desktop and choosing Desktop Preferences.

---

### Post by finny388 on 2012-01-02
Thanks for the tips. Still something is wrong:

Note how panel and window fonts are so small (and it seems 24 pt size is overkill to achieve what looks like 11pt)

[[IMG]http://img838.imageshack.us/img838/8103/201201021158281360x768s.png](http://imageshack.us/photo/my-images/838/201201021158281360x768s.png/)

---

### Post by Dennis N on 2012-01-02
> **finny388 said:**
> 
Note how panel and window fonts are so small (and it seems 24 pt size is overkill to achieve what looks like 11pt)



Window Title Font: You can set that one here:

Preferences > Customized Look and Feel >  Window Border Tab

Below that are tabs for Theme, Title Bar, Misc.

Title Bar has settings for the Window Title.

As to the Buttons on the Task Bar at the bottom, I have not seen any good way to change the font size there. It has been brought up in some posts in the past, but no good solution has been offered, as far as I know. One method is to increase the width of the panel, and when you do, the font size will increase at some point, but this is not a good solution in my opinion. A way to change this font is needed when using large HD screens.

To increase panel width, right click on panel, select "panel settings".

---

### Post by finny388 on 2012-01-02
I'll give that a try 
were you able to see my screenshot?
my resolution is only 1366x768

i'm able to use 11pt fonts in ubuntu and they are normal (about 6-8 times bigger than what i have in Lubuntu)

---

### Post by Dennis N on 2012-01-02
Yes, I looked at the screen shot and spotted the tiny window title font and tiny task bar button font. 

If you increase the panel size, you need to change to a solid color panel background - I think the panel image supplied is a fixed size.

With the window title font adjusted, you might be able to get by.

---

### Post by Rodney9 on 2012-01-02
This will help and give you clues on how to make the panel how you want - [http://goo.gl/oiBwS](http://goo.gl/oiBwS)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by finny388 on 2012-01-02
This seems to be a fundamental incompatibility issue with my tv.

Leafpad with 11pt font is microscopic as well.

That and no sound and when I right click the sound icon settings are greyed out.

I shouldn't have to set fonts to 24pt all over the place just to make things readable.

I'm going to try xubuntu.

Thanks for the replies and good tips.

---

### Post by Worp8d on 2012-01-10
I have exactly this problem too. It's very frustrating, you can't change all of the font sizes. It's annoying, Lubuntu is by far the best Ubuntu distribution atm.

---

### Post by marinara on 2012-01-10
i assure you, you can change all the font sizes.  Any specific font you can' change?

---

### Post by Cheesemill on 2012-01-10
I've had this problem with several distros, the problem is with the Nvidia driver not correctly recognising the screens DPI.

If I recall the answer is to edit /etc/X11/xorg.conf and in the Nvidia Device section add
```
Option   "DPI"   "96 x 96"
```
and reboot.

If this works you'll then have to change the system font sizes back to the defaults because you've probably made the huge to compensate.

PS - I don't have this problem on my current system so this is all from memory, if it doesn't work just google for 'nvidia small fonts ubuntu' and you should be able to find the correct solution.

---

### Post by Dennis N on 2012-01-10
> **marinara said:**
> i assure you, you can change all the font sizes.  Any specific font you can' change?

The setting which eludes us is the size of the font on the task bar buttons and the possibility of setting it to boldface.

---

### Post by marinara on 2012-01-10
right click on task bar, select 'panel preferences'

i have my icon height to 36, and my size-height at 27.
works perfect, i don't mind that the icons are cut off at the bottom

---

### Post by Dennis N on 2012-01-11
> **marinara said:**
> 
i have my icon height to 36, and my size-height at 27.
works perfect, i don't mind that the icons are cut off at the bottom

Thanks for the suggestion, but I've tried these same size adjustments in the past. I personally didn't care for the undesirable appearance side effects you get. I'll stick with the what we have.

If nothing else, bold face setting alone would be helpful for readability, as possible with the clock font.

---

