---
title: "Is my graphics card too hot"
date: 2011-11-01
forum: General Help
---

### Post by RogerD on 2011-11-01
Hi

I'm experimenting with 11.10 and Unity on my spare PC - there are definitely some pluses.

The big problem is that I'm getting very poor windowing performance - the edges of windows lag behind my mouse pointer - makes the whole experience pretty terrible.

In theory, with my hardware I should be getting excellent graphics performance, but I'm beginning to wonder if the problem isn't with my fanless Asus EN6200LE graphics card, which Psensor indicates is running at 71 degrees.

Could this be the problem?

Roger D

---

### Post by Jaybyrrd on 2011-11-01
> **RogerD said:**
> Hi

I'm experimenting with 11.10 and Unity on my spare PC - there are definitely some pluses.

The big problem is that I'm getting very poor windowing performance - the edges of windows lag behind my mouse pointer - makes the whole experience pretty terrible.

In theory, with my hardware I should be getting excellent graphics performance, but I'm beginning to wonder if the problem isn't with my fanless Asus EN6200LE graphics card, which Psensor indicates is running at 71 degrees.

Could this be the problem?

Roger D

Alright so I have a 9800 GTX+ which in theory should run extremely well also! However I have a similar problem,I think that better drivers need to be made and some bugs ironed out more than anything so that is probably the problem. (At least my current conclusion). If you run Unity 2D the problems disappear for me at least, (you should try and see), and 71 Degrees, especially for a fanless card, is not unbearably hot. My 9800 GTX+ under stress runs at 80 Degrees (benchmark stress) and it has a fan. So considering you only have a heat sink you are probably ok. 

Hope that helps! :)

---

### Post by RogerD on 2011-11-01
Yes, that's a great help - I was thinking of buying another graphics card.

I've tried 2D and, yes, the windowing problems go away, but the workspace switcher doesn't work.

Shame to say, but it looks as though 11.10 is still 'work in progress'. I'll stick to LTS 10.04 until I'm forced to change.

Thanks for your help.

Roger D

---

### Post by Jaybyrrd on 2011-11-01
No problem, glad I could be of help. I am kind of interested as to why the workspace switcher doesn't work for you. Are you sure you're hotkey is set to Super+S. If so that is odd. Did you upgrade to 11.10 or clean install to it?

---

### Post by RogerD on 2011-11-01
I did a clean install, but what's this about my hotkey - never heard of that before - and setting it to Super+S?

---

### Post by 2F4U on 2011-11-01
71 degrees seems to me a bit hot. My fanless ATI 4550 runs below 60 degrees with the open source ATI drivers and it would run around 50 degrees with the proprietary ATI drivers. I am using KDE with the default desktop effects enabled. Just to give some numbers.

---

### Post by TBABill on 2011-11-01
That 71 degrees most likely came from trying to push 3D using the open source driver through an older card. Mine did exactly the same thing with the same result on an older ATi card. 2D works extremely well with it and the machine is quite a bit cooler.

---

### Post by Gatemaze on 2011-11-01
Temperature should be fine for a busy graphics card.

---

### Post by Jaybyrrd on 2011-11-01
Like I said the extra heat probably comes from the fact that the card is stressed or under working stress, and you should be able to view all four workspaces and switch between them by using Super+S

---

### Post by RogerD on 2011-11-01
I can view all four workspaces in 3D, however, when I switch to 2D, only one workspace - the top left is shown. The other three are just blank. If it wasn't for this I'd happily use 2D.

Something wrong somewhere.

---

### Post by stinkeye on 2011-11-01
> **RogerD said:**
> I can view all four workspaces in 3D, however, when I switch to 2D, only one workspace - the top left is shown. The other three are just blank. If it wasn't for this I'd happily use 2D.

Something wrong somewhere.
Because you are no longer using compiz as your window manager 
you will need to change the setting for Metacity.

In the terminal run 
```
gconf-editor /apps/metacity/general/num_workspaces
```
and set your number.

Not sure if gconf-editor is in the default install.
May need to download.

---

### Post by RogerD on 2011-11-01
OK, I've done that and, yes, I've got 4 desktops, but it still isn't working properly - e.g. I select the bottom left window, but, eventually, a clicked application finally opens in the top left. It's as though my PC is finding the whole business of processing all this windowing information just too much.

Back to good old 10.04, but thanks for all your informed help and interest.

RogerD

---

### Post by Jaybyrrd on 2011-11-01
No problem! And sorry it didn't work out, mark this thread [solved]?

---

