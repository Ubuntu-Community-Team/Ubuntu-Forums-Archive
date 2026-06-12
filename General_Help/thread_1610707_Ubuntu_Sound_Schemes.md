---
title: "Ubuntu Sound Schemes"
date: 2010-11-01
forum: General Help
---

### Post by brandenmikal on 2010-11-01
Can anyone tell me how to custom make your own sound scheme or make a sound scheme in Ubuntu 10.10?

I've tried the "System > Preferences > Sound" route and it didn't achieve anything for me.

---

### Post by NightwishFan on 2010-11-01
At the moment a non-obvious but direct way is to backup the /usr/share/sounds/ubuntu directory, then replace all of the sounds in there with ones of your own.

---

### Post by brandenmikal on 2010-11-01
> **NightwishFan said:**
> At the moment a non-obvious but direct way is to backup the /usr/share/sounds/ubuntu directory, then replace all of the sounds in there with ones of your own.

Thanks, I will try that :)

Btw, How are you Virgil?

---

### Post by NightwishFan on 2010-11-01
Quite ok, better than usual. :) Thanks for asking, I take it you are doing fine yourself?

You are probably aware of how to do this, but just in case you aren't, you run a root session of Nautilus with gksudo nautilus (or in a term: su -c nautilus --no-desktop --browser). You can back up the directory to a .tar file, and then edit at will. Just restore it when you are done.

---

### Post by brandenmikal on 2010-11-01
> **NightwishFan said:**
> Quite ok, better than usual. :) Thanks for asking, I take it you are doing fine yourself?

You are probably aware of how to do this, but just in case you aren't, you run a root session of Nautilus with gksudo nautilus (or in a term: su -c nautilus --no-desktop --browser). You can back up the directory to a .tar file, and then edit at will. Just restore it when you are done.

Yeah, I didn't actually understand that part of it but thank you for the heads up.

I'm pretty good, today we are taking some of our packages that we packed over to the new place we're moving into down the street. I'm pretty excited about it so far.

---

### Post by NightwishFan on 2010-11-01
That sounds great. I recently got in a new place myself. If you need any more help with the sounds, I should be on for a bit.

---

### Post by brandenmikal on 2010-11-01
> **NightwishFan said:**
> That sounds great. I recently got in a new place myself. If you need any more help with the sounds, I should be on for a bit.

Awesome :] So far, I tried what you said and it didn't show up in the drop down list on the Sound Preferences menu. 

I'm thinking for that I'll have to created an index.theme file much like the one I found in the Ubuntu Studio sound scheme I installed earlier.

---

### Post by NightwishFan on 2010-11-01
I should clarify, my solution was not to make a new theme, just to use an existing one with new sounds. I am sure it is possible to make one, just beyond the scope of my knowledge. I am probably one of the few not disappointed in the lack (as far as I know) of a GUI to do this as I just disable sounds.

I think you can get more sounds with the package:  sound-theme-freedesktop

---

### Post by brandenmikal on 2010-11-01
> **NightwishFan said:**
> I should clarify, my solution was not to make a new theme, just to use an existing one with new sounds. I am sure it is possible to make one, just beyond the scope of my knowledge. I am probably one of the few not disappointed in the lack (as far as I know) of a GUI to do this as I just disable sounds.

I think you can get more sounds with the package:  sound-theme-freedesktop

ah, okay. i will look into that. i'm compiling one right now for halloween. haven't got it to work yet but i made the index.theme file for use with it (lists it basically)

now it's a matter of it picking up the sounds (i may have to rewrite the names to match like the others)

---

### Post by brandenmikal on 2010-11-01
> **NightwishFan said:**
> I should clarify, my solution was not to make a new theme, just to use an existing one with new sounds. I am sure it is possible to make one, just beyond the scope of my knowledge. I am probably one of the few not disappointed in the lack (as far as I know) of a GUI to do this as I just disable sounds.

I think you can get more sounds with the package:  sound-theme-freedesktop

Got it to work finally; I had to rename the sound files to the same names as the others. I'm happy; I learned something pretty vital today. How to create a sound scheme on Ubuntu!

That's what I love about using Linux. You can teach yourself new tricks and have fun in the process. Was a lot of hard work but I got it done and I didn't have to install anything or configure sensitive data.

Thank you for your help!

---

### Post by NightwishFan on 2010-11-01
Enjoy! I will cya around. Hopefully soon enough Gnome will have a GUI for that again like it did in the past.

---

### Post by brandenmikal on 2010-11-01
> **NightwishFan said:**
> Enjoy! I will cya around. Hopefully soon enough Gnome will have a GUI for that again like it did in the past.

I hope so. It would be a LOT easier to work with. Have a nice night!

---

