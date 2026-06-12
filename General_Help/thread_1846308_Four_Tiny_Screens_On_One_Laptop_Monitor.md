---
title: "Four Tiny Screens On One Laptop Monitor"
date: 2011-09-18
forum: General Help
---

### Post by Tigrisan on 2011-09-18
I'm running Ubuntu 10.10 on a dual boot Windows XP Toshiba laptop and have been slowly learning how everything works. Things have been great up until today when I closed my laptop. Normally, when I open it, Ubuntu wakes asking for my password. I enter it and everything is fine.

Today when I opened it, I suddenly had four very tiny screens on my one laptop monitor. I made no changes at all since the last time I restarted my laptop and haven't a clue what happened, but these four little windows are so tiny, I need a magnifying glass to read them. 

They are all a mirror image, everything I do on one happens on all of them, but I can't seem to find a way to make them just one window again.

Help. Please?

---

### Post by Frogs Hair on 2011-09-18
It reads like the expo feature on the work space switcher was activated . does it look like the screen shot ? If so try the Esc key , workspace switcher or if you have a Compiz dock icon check that as well .

---

### Post by Tigrisan on 2011-09-18
Mine are two by two (two on top, two on the bottom,) but yes, they're all the same screen.

When I hit the ESC key though, nothing happens at all. I don't get any options and nothing changes.

My reading glasses aren't cutting it for this LOL!

---

### Post by Frogs Hair on 2011-09-18
I have the cube enabled so the spaces appear in a row . (I forgot you cant see the panel) Try Ctrl + Alt up arrow or down arrow. If you are running Compiz , try this command in the terminal in the recovery console found on the session list at the bottom of the login screen after entering your name  . ```
compiz --replace 
```
If Compiz is not installed try this command . ```
metacity --replace
```

---

### Post by GWBouge on 2011-09-18
> **Frogs Hair said:**
> If Compiz is not installed try this command . ```
meacity --replace
```

```
metacity --replace
```

Fixed that for you  =o)

But, if it was Expo/Desktop wall, the workspaces wouldn't be mirrored, no?

Can you double-click on one of the workspaces to view it?  Can you take a screenshot of this?

---

### Post by Frogs Hair on 2011-09-18
> **GWBouge said:**
> ```
metacity --replace
```

Fixed that for you  =o)

But, if it was Expo/Desktop wall, the workspaces wouldn't be mirrored, no?

Can you double-click on one of the workspaces to view it?  Can you take a screenshot of this? Thanks !

---

### Post by Tigrisan on 2011-09-18
Compiz is not installed. And did you mean metacity? I typed the code in and it did nothing.

When I hit Ctrl Alt I can move through the screens with the right and left arrows, the up and down don't do anything. However, though I move to the 'next square/screen", the only thing that happens is I lose whatever is in the top left screen as it 'moves' to the top right screen, then the bottom left and bottom right respectively. At least I think that's what's happening since all four screens show exactly the same thing. If one changes, they all change.

And thank you for helping, by the way.

---

### Post by Tigrisan on 2011-09-18
I tried to take a screenshot of it, but it takes four separate shots of four separate squares. It won't take a shot of the entire monitor unless there's a way to do that and I don't know how, which is quite possible as I said I'm still learning Ubuntu.

I did try the metacity --replace again. It must be running now so I'll wait and see what happens.

---

### Post by Frogs Hair on 2011-09-18
Yes , I meant metacity . Since my cube is enabled the key board shortcuts for the workspace switcher are disabled and not listed and I will have to look then up. Give Crtl + Alt + Ecs a try .

---

### Post by Tigrisan on 2011-09-18
I did the CTRL Alt ESC but it didn't do anything. Then while I was still holding down CTRL Alt, I accidently hit the F1 key and it wigged out. I had to do a hard shutdown, but when I restarted it, I was back to only one screen! YAY!!!

Thank you both so much! I would never have gotten there without your suggestions.

I'm learning. I've been a Windows gal for years but I started on DOS so I think I'll be able to get the hang of it eventually.

Thanks again.

---

### Post by GWBouge on 2011-09-18
> **Tigrisan said:**
> Then while I was still holding down CTRL Alt, I accidently hit the F1 key and it wigged out

That was actually going to be my next suggestion, lol.  Ctrl+Alt+F(1-6) (I think F1 through F6?  I usually use F2 for some reason) bring you to a different run level, and get you away from the GUI Desktop.  Was kindof curious to know if you would just get, basically, a big terminal screen, or if you would have seen 4 little terminal screens, lol.  Along with every other CLI command, you can then use:

```
sudo service gdm restart
```

To try to restart just the desktop, or

```
sudo reboot now
```

To restart the entire machine.  Handy trick to keep around  =o)

---

### Post by Frogs Hair on 2011-09-18
Glad your back up ! I'm curious as to what caused it though . Welcome to the forums BTW .

---

### Post by GWBouge on 2011-09-18
> **Frogs Hair said:**
> I'm curious as to what caused it though .

As am I.  Googling around, I found a claim or two where, if a Compiz effect is active when the computer suspends (such as Expo), it won't ask for a password when it wakes.  Here, almost sounds like the computer was in Expo mode as it suspended, and waking up it thought Expo *was* the desktop.  I wonder if this is repeatable?

---

### Post by Tigrisan on 2011-09-18
Thank you for the welcome :D

I have to be honest, I don't think I want to repeat it! LOL

But I did print your command suggestions and will keep them nearby until i really get the hang of all of this. I've been using it for oh...6 months on and off, but this is the first time I've run into a problem of this kind.

The DH was watching the Lemans race on Firefox prior to closing the lid, but he'd clicked out of FF by then. He had the option watching the live race though to watch up to four different races at the same time, but chose not to. I can't imagine that affecting Ubuntu, but what do I know? Right now, I feel like I don't know much of anything.

Anyway, the laptop is set to sleep when the lid is closed so the only thing I need to do is sign in. When I opened the lid, I got four sign in screens. Oddly enough, when I did a hard restart, the computer booted to the boot screen in one large screen. The minute I chose Ubuntu, it went to the four screens through the boot process. I rather thought if the screen was deliberately set up for four or however many, that the boot screen would at least be just the one screen, but it wasn't.

Thanks so much again. That printing was just too tiny to live with ;)

---

