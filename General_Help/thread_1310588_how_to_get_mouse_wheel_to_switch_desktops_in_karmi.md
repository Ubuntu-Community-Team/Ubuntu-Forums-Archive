---
title: "how to get mouse wheel to switch desktops in karmic?"
date: 2009-11-01
forum: General Help
---

### Post by Meow27 on 2009-11-01
well, this feature was apparently disabled in karmic.

what options and sub options do i need to change in the compiz config manager, if thats where i need to change them from?

-meow

---

### Post by BitJunkie on 2009-11-01
Go to System->Preferences->CompizConfig Settings Manager. Click on Viewport Switcher then click on the Desktop-based Viewport Switching. Set Move Next to Button5 and Move Previous to Button4. That's how I fixed mine.

---

### Post by Meow27 on 2009-11-02
it worked. thanks

---

### Post by JC Cheloven on 2009-11-02
> **BitJunkie said:**
> Go to System->Preferences->CompizConfig Settings Manager. Click on Viewport Switcher then click on the Desktop-based Viewport Switching. Set Move Next to Button5 and Move Previous to Button4. That's how I fixed mine.
You helped me also, and probably many others around here. Thanks :-)

---

### Post by zeroseven0183 on 2010-01-28
> **JC Cheloven said:**
> You helped me also, and probably many others around here. Thanks :-)

Including me! Thanks!

---

### Post by BitJunkie on 2010-01-28
I'm glad to see this is still helping people! :D

---

### Post by fig_wright on 2010-05-19
Just what I needed :)

---

### Post by Meck1982 on 2010-05-29
For those who want a quick command line solution:

[FONT="Courier New"]gconftool -t string -s /apps/compiz/plugins/vpswitch/allscreens/options/next_button "Button5"
gconftool -t string -s /apps/compiz/plugins/vpswitch/allscreens/options/prev_button "Button4"[/FONT]

Also see my [**blog entry**]("http://gingedas.net/node/302")

---

### Post by elliotn on 2010-05-29
Me too.

---

### Post by tweaksource on 2010-06-21
Move next Button5, Move Prev Button4 works for me.

Your post is still helping. You rock!!! :guitar:

I really appreciate it.

---

