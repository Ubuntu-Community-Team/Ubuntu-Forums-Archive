---
title: "Cairo-dock maximized windows issue"
date: 2010-06-08
forum: General Help
---

### Post by Manuwash on 2010-06-08
Hey guys, I was trying to fix something on my cairo-dock and it dissapeared not to be seen again, so I had to reinstall. Unfortunately it installed another version than the one I originally had ( forgot which one) and I had to go through a whole new ordeal to get it working. Good thing out of the bad is that I got some nice new themes I didnt have before. Bad part of it, check the picture:

I used to have the option to reserve space for the dock but before I could see the description of the dock icon I was hovering over, now the description remains below the maximized window, and depending on the theme, also part of the dock, which doesnt look good ( i use small themes, and I dont mind if a tiny bit of the dock is over the maximized window).

So anyone here who has been going through the same cairo dock adventures can lend a hand to this wayfarer fallen into disgrace? :p

---

### Post by kerry_s on 2010-06-08
what do you have the setting on?

---

### Post by 4Orbs on 2010-06-08
If you right-click on an empty spot on Cairo dock, a menu will open and you can find, on that menu, the option to open the configuration settings for the dock. That's where your answer is kept.

---

### Post by Manuwash on 2010-06-08
Kerry, that option you tell me is in conflict with the reserve space for dock, when I select it my dock goes to hell and starts having graphic conflicts leading me to a restart, when all is well again except I am in the same position as before. I am 100% sure my previous version of cairo dock worked fine in this regards, but this one seems to lack an option to keep the dock on top of other windows, as far as it seems at least.

for 40rbs, I have been going crazy over the settings and googling already my friend, to no avail.

---

### Post by kerry_s on 2010-06-09
> **Manuwash said:**
> Kerry, that option you tell me is in conflict with the reserve space for dock, when I select it my dock goes to hell and starts having graphic conflicts leading me to a restart, when all is well again except I am in the same position as before. I am 100% sure my previous version of cairo dock worked fine in this regards, but this one seems to lack an option to keep the dock on top of other windows, as far as it seems at least.

for 40rbs, I have been going crazy over the settings and googling already my friend, to no avail.

i don't understand, that is the setting where you select exactly that.

maybe you need to delete the ~/.config/cairo-dock & start all over again, you keep saying it was different, perhaps the settings are not done in the same way as the old.

---

### Post by Manuwash on 2010-06-09
Dude I fixed it, deleted the whole ~/.config/cairo-dock and reinstalled version 2.1.0 now its working well again ( problem was with the version I had, 2.0.9) Im so freaking happy, this thing drained quite a bit of my time and energy LOL

Thanks for the help!

Btw I have another question, when it asks me if I want to enable the opengl mode, I am afraid of trying that and messing everything up, I have an ati radeon xpress 1250 card, should it work with it? and basically what makes the opengl mode better? animations? effects?

---

### Post by fabounet on 2010-06-09
go to simple mode (the button in the bottom-left of the config panel), then just choose the visibility you want ("prevent windows from overlapping the dock" I think).

by the way reinstalling the software has no effect, since the user files are kept (and in this case they are in ~/.config/cairo-dock/current_theme)

---

### Post by Manuwash on 2010-06-09
Thanks fabounet, I already solved it, it was the version 2.0.9 that was giving me lots of trouble. Are you the one who makes the themes? nice job ;)


Hey check it out, the annoying bug of the upper panel not being transparent when you have different cube wallpapers, wish there was a way around that one, Id love to use the different wallpapers but I like the transparent panels too. (im going off topic here LOL)

[IMG]http://www.glx-dock.org/mediacolor/album3/1273522736_3f23769277_big.jpg[/IMG]

---

### Post by kerry_s on 2010-06-09
> Btw I have another question, when it asks me if I want to enable the opengl mode, I am afraid of trying that and messing everything up, I have an ati radeon xpress 1250 card, should it work with it? and basically what makes the opengl mode better? animations? effects?

yes, you want that. it use's the vid cards hardware acceleration, in theory it should be faster & smoother.

---

### Post by Manuwash on 2010-06-09
Yeah well it doesnt let me, tells me my opegl is not up to date, any idea how to update this driver? I ve been looking around but to no avail.

---

### Post by kerry_s on 2010-06-09
> **Manuwash said:**
> Yeah well it doesnt let me, tells me my opegl is not up to date, any idea how to update this driver? I ve been looking around but to no avail.

what ubuntu version are you using? cause i just removed my cairo-dock & it was 2.1.3, so i'm guessing your using like karmic which would be out of date by a year, i'm on 10.04 lucid.

---

### Post by Manuwash on 2010-06-09
Yeah Im using karmic, I tried installing lucid but ran into too much hassle with my ati card. Anyways right now after a catastrophic update I did nothing works at all, not even compiz, im about to boot vista and forget about all this, its totally draining me.

---

### Post by kerry_s on 2010-06-09
> **Manuwash said:**
> Yeah Im using karmic, I tried installing lucid but ran into too much hassle with my ati card. Anyways right now after a catastrophic update I did nothing works at all, not even compiz, im about to boot vista and forget about all this, its totally draining me.

yeah, linux will do that to you, it's always work in progress.
i just fixed a panel loading really slow problem, turns out i had the login set to not ask password & the recent updates didn't like that, took me half a day to finally find the problem. i was uninstalling/reinstalling & resetting things to default looking for the cause. 
i kept my cool though, can't afford another screen right now. :lolflag:

anyways your welcome to come & go as you please, if you feel you need a break, you can try again later. i myself will often take a break from linux when things start changing in ways i don't like.

if it's just the effects giving you problems try not using them.
the default gnome stuff can provide what you need to get the job done.

i'm just using the normal gnome-panels now, but still setup in the way i like it.

---

### Post by Manuwash on 2010-06-10
Hey thanks for the support man, I appreciate it.

Really for me it has been a whole week fighting to get things working. I first installed sabayon because I had read about it being a good distro to start with, but it killed my vista boot and wasn´t working too sharply, I had some issues with that but I kept my cool. My roomate, who is a programmer and a linux freak, told me to get a ubuntu live cd and install it, and he would help me out to put it "on point" (his words). Matter of fact, he never helped me at all, and I struggled a lot trying to troubleshoot the lucid lynx 10.4 version which refused to work with my ATI radeon card. 

Finally after a week of struggle, even calling another friend who is also very knowledgeable with linux ( he works maintaining servers for an important bank, and he uses linux for that, so he knows his ****), and to no avail, I decided to get the karmic koala and finally that seemed to work. But my relationship with 9.10 has been terrible, everytime I go forward 2 squares the damn thing takes me back 4. It´s been stressing the hell out of me really. I´ve done a lot of effort to learn about the way it works, use terminals ( I would never use DOS in vista, what for?), learn commands, fix scripts. The only thing I wanted was to have a pretty, fast and functional desktop for my chill out internet needs ( chat, internet, getting nice apps). But the damn thing refused to give me a break. 

When finally I had it all set up, working like a charm, I do an update and truly the only solution I see now is to reinstall. But of course I would have to go through the whole downloading and setting up things again, and I am drained bro, I have no more energy.

I will do as you said, give it a break, when I have some more energy I might engage in a new linux adventure, but now I can´t see myself googling for troubleshooting one second more.

Also I might get a desktop pc which I am not sure but it might be a dual core much better than my old samsung laptop, so I might try hooking up my external hdd there and see what happens.

Until then and thanks.

---

