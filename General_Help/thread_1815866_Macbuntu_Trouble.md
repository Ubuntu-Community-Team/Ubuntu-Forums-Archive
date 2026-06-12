---
title: "Macbuntu Trouble"
date: 2011-08-01
forum: General Help
---

### Post by morris14ccm on 2011-08-01
I recently installed Ubuntu 11.04 to my laptop. I just installed Macbuntu to it. However, the small Apple logo on the toolbar at the upper left of the screen is showing up very tiny. Is there a way to change this after having installed it or not? (Can be seen in screenshot)

Also, attached is a picture of Terminal during the install. It asked me if I wanted to install a group of repositories and I typed "Y", but as I hit enter I must have hit some other button on the keyboard and it ended up aborting that part of the install. Can anyone tell me what exactly didn't install?

Also, the wobbly window feature I selected to be on does not appear to be on. Any way I can fix this?

Thanks,
Chris

---

### Post by blane2 on 2011-08-01
This didn't install
```

sudo apt-get install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins-extra compizconfig-settings-manager fusion-icon mesa-utils python-compizconfig 

```

also try ubuntu classic mode see if the mac theme carries over.
I'm more curious than anything else.

---

### Post by morris14ccm on 2011-08-01
> **blane2 said:**
> This didn't install
```

sudo apt-get install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins-extra compizconfig-settings-manager fusion-icon mesa-utils python-compizconfig 

```also try ubuntu classic mode see if the mac theme carries over.
I'm more curious than anything else.
ok, i did that and it worked, the mac in the menu bar is still small, but it's not that big a deal. wobbly windows and the cube functions still don't work.

yes, it does carry over in classic.

---

### Post by blane2 on 2011-08-01
what GFX card to you have and do you have the correct drivers for it?

---

### Post by morris14ccm on 2011-08-01
> **blane2 said:**
> what GFX card to you have and do you have the correct drivers for it?
Integrated graphics. Not sure about the drivers, but i don't think that seems to be the issue.

---

### Post by blane2 on 2011-08-01
> **morris14ccm said:**
> Integrated graphics. Not sure about the drivers, but i don't think that seems to be the issue.

it's possible 3d effects will not work with your integrated graphics.

```
lspci
```

type that in a terminal and post the results.

---

### Post by morris14ccm on 2011-08-01
i guess that would make sense.

---

### Post by blane2 on 2011-08-01
plug in your computer

i don't think 3d effects are possible with your GFX card 

and I've got no clue how to make the apple bigger... however You used to be able to change the programs icon in ubuntu... 

I'd google how to change the applications icon.. might give you some clues. 


If you can find the image file for the apple in the macbuntu theme, you can probably swap that file with a bigger apple.


I used to change mine all the time using older version of ubuntu.


Also there is a way to get ride of the "docky" icon from the task bar. I don't know if they've put it in the preferences yet or if you need to mannually change it like you used to... 

Google that as well if you want to get rid of the big anchor on your task bar.

for a real mac look switch to classic and get rid of the bottom pannel.

---

### Post by morris14ccm on 2011-08-01
alright, thanks for your help!

2nd day of ubuntu and i love it, wish i ditched windows a while ago!

---

### Post by blane2 on 2011-08-01
if you have any more questions you can PM me. Seems like this forum isn't as helpful as it used to be...

---

### Post by morris14ccm on 2011-08-01
> **blane2 said:**
> if you have any more questions you can PM me. Seems like this forum isn't as helpful as it used to be...
will do
thank you

---

