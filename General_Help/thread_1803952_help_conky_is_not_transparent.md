---
title: "help conky is not transparent"
date: 2011-07-14
forum: General Help
---

### Post by elliotn on 2011-07-14
guys please help my conky has a background but I want it transparent, I use to have Ubuntu but then I installed kubuntu-desktop but the conky background has the Ubuntu wallpaper although I have removed Ubuntu-desktop. check the snapshot, please help

---

### Post by Quackers on 2011-07-14
First thing to try is to change
background no
to
background yes

Then save the file and conky should start up again. How does it look now?

---

### Post by elliotn on 2011-07-14
> **Quackers said:**
> First thing to try is to change
background no
to
background yes

Then save the file and conky should start up again. How does it look now?

no changes still same thing even if I put yes

---

### Post by Quackers on 2011-07-14
Ok, with background yes still in there try changing
own_window_type overide
to
own_window_type normal
or 
own_window_type desktop

and see what happens then.

I had problems with kde and conky. From memory (as I don't have it any more) I think I used the line(s)
own_window_argb_visual yes
and possibly this one too
own_window_argb_value 0  # value can be from 0 to 255 where 255 is opaque

but with either of these lines in use the
own_window_type cannot be override iirc.

Try a few permutations, saving the file after each one.

---

### Post by elliotn on 2011-07-14
> **Quackers said:**
> Ok, with background yes still in there try changing
own_window_type overide
to
own_window_type normal
or 
own_window_type desktop

and see what happens then.

I had problems with kde and conky. From memory (as I don't have it any more) I think I used the line(s)
own_window_argb_visual yes
and possibly this one too
own_window_argb_value 0  # value can be from 0 to 255 where 255 is opaque

but with either of these lines in use the
own_window_type cannot be override iirc.

Try a few permutations, saving the file after each one.

none worked

---

### Post by Quackers on 2011-07-14
Sadly I don't have a kde desktop to experiment on any more. From memory I think kde draws its desktop differently.
Googling should help as this problem has cropped up many times for others :-)
It's definitely solvable!
Good luck!

---

### Post by elliotn on 2011-07-14
i give up 

thanks for trying

---

