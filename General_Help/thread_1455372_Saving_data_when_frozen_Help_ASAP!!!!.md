---
title: "Saving data when frozen??? Help ASAP!!!!"
date: 2010-04-15
forum: General Help
---

### Post by House101 on 2010-04-15
Ok, so I was trying to import some fonts, and (like an idiot), while I have all the fonts selected, I click on 'open in font viewer' and now it's stuck. The mouse still moves, but everything else, down to the clock, is dead frozen. I was working on a Photoshop file and didn't have time to save, is there any way to save data before I shut down, and if it's been frozen for 10+ minutes, is it going to eventually unfreeze or just keep churning?
Thanks
house101

---

### Post by House101 on 2010-04-15
Bump??

---

### Post by Johnny B on 2010-04-15
go to tty1 (ctrl+alt+F1) log in and run the 'top' command
find the name of the 'font viewer' process (ctrl+C to quit 'top')
run 'killall font-viewer' (or whatever its name is)
ctrl+alt+F7 to get back to gnome

---

### Post by House101 on 2010-04-15
I actually just woke it up and it managed to open them all! Thank you though, I was getting desperate!!!

---

### Post by House101 on 2010-04-15
> **House101 said:**
> I actually just woke it up and it managed to open them all! Thank you though, I was getting desperate!!!
Didn't matter, while I was trying to shut down all font viewer processes, there was still windows opening; it was too much for the system and Photoshop crashed anyway. There was also an error when I tried to run the top command (my computer happens to be very messed up).
Thanks though!!

---

