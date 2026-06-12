---
title: "Original Dust Theme"
date: 2010-05-14
forum: General Help
---

### Post by Exüberance on 2010-05-14
After upgrading to Lucid Lynx, I found that the Dust theme has been changed to have rather ugly bars on the sides of windows and the loading bars aren't as fany anymore (now they're just a solid colour).

Is there any way to get back the original dust theme?

---

### Post by fragos on 2010-05-14
The Appearances will allow you customize any theme and save it. You may be able to come close with that. Perhaps the Dust Sand theme is closer to what you remember. It would appear that you can find the files for the 10.04 Dust theme in /usr/share/themes/Dust. You could modify some of these png's as well. Lastly you could try taking this set of files from a 9.10 install but be sure to make backups just in case.

---

### Post by Exüberance on 2010-05-17
Thanks for the reply. I got the old awesome loading bar back, and I think I could probably change the window side borders back to hairline thickness, but I'm kind of liking the look of Ambiance so I might stick with that for window borders and use Dust for the other GUI elements. Thanks!

For anyone else wanting the cool moving diagonal stripes effect for the loading bar, open /usr/share/themes/Dust/gtk-2.0/gtkrc and change the line "progressbarstyle = 0" to "progressbarstyle = 1"

Looks like you can do this with any theme too. Just change 'Dust' in the path to the name of your theme and find that line and change it. Woo!

---

### Post by Andy06 on 2010-05-29
Any idea why it was changed. I know beauty is subjective but this was like a horrible horrible regression. The old loading bar was light years better than the new one and those bars on the sides look positively fugly. What was the design reasoning for them?

Does anyone know how to contact the devs for this? I will beg and plead them to revert the changes! :)

---

### Post by Andy06 on 2010-05-29
Oh and if there are any recommendation for how to get the old theme back, please do let me know

---

### Post by fragos on 2010-05-29
Appearance-> Theme tab-> Customize button-> Control tabs. There are a number of these to choose from and some of the things that change with them is the scroll bar and the loading bar. Perhaps you can find a control more to your liking. A Theme is a starting point and all of the components can be intermixed. The theme the system is using will be the upper left item in the theme tab and it's label will be custom.

---

### Post by Andy06 on 2010-05-29
Yeah I know that, what I meant was is there a way to get the OLD Dust theme back the way it was?

Customising Dust with different window controls doesn't help. Neither does altering the colour change the loading bar. Those are the two things I would like to change.

Thanks

---

### Post by Spr0k3t on 2010-05-29
There already is a bug posted on Launchpad.net, have a look:

[https://bugs.launchpad.net/dusttheme/+bug/563218](https://bugs.launchpad.net/dusttheme/+bug/563218)

If the border is a problem for you, make sure to follow up with the bug on launchpad.

---

