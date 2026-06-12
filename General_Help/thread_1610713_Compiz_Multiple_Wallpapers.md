---
title: "Compiz Multiple Wallpapers"
date: 2010-11-01
forum: General Help
---

### Post by Turwaithien on 2010-11-01
I can't seem to find anyone else having this problem, but it may be that I'm not searching well enough.

Before I upgraded (to Maverick Meerkat)I had multiple wallpapers enabled via Compiz. Now they don't work. When I enable it (in Compiz Config) the background does not change (problem one), also the windows no longer move properly, they're all repeating-y like when the computer's just freaking out for fun(problem two). All of my settings in Compiz are the same for the most part (there's actually more disabled now, because I got tired of some of the more random things I had enabled), so I know my computer is physically capable of the feat. I don't know how to tell what exactly is happening when I enable stuff, I just know when it doesn't work right. :P

I apologize for the ramble.

---

### Post by HiImTye on 2010-11-01
Im intrigued to find out how you managed to get multiple wallpapers working with ubuntu. I havent been able to since 9.04 and gave up and just installed desktop drapes lol

---

### Post by TNT1 on 2010-11-01
Once you get your Cube enabled, and your Wallpapers enabled and set up: you have to tell Nautilus **not** to display the (original) desktop.

Open a terminal, and type "**[COLOR=Green]sudo gconf-editor[/COLOR]**" (without the double quotes, of course) and hit enter.

The gconf editor will pop up - it's actually a graphical editor, like  what you're used to working with.  (I just don't know another way to get  it running with root access.  Sooo...)

Under **[COLOR=Teal]Apps->Nautilus->Preferences[/COLOR]** you'll find a checkbox next to "Show Desktop".  Un-check this checkbox.  By the time you click on the OK and get out of the editor, you *should* be able to see the multiple wallpapers you have selected and set up.

---

### Post by HiImTye on 2010-11-01
yes but also, your icons will disappear and if you have any programs that draw to the desktop they will also disappear

thats why I decided not to use it (I remember now)

---

### Post by londonbabs on 2010-11-01
I have the same kind of problem, and followed many instructions off the net on how to enable compiz wallpaper to do so and then disabling show desktop, only thing is, when I do all this and restart x, I have no more wallpaper, it's just transparent, I can see through all windows into my (3 faced) cube and, of course no wallpaper and no icons, anybody had this problem also on Maverick ?

---

### Post by Turwaithien on 2010-11-02
I disabled the nautilus desktop a while ago, when I originally started using the multiple wallpapers. It's still unchecked (I checked), so that's not my problem.

---

### Post by Turwaithien on 2010-11-02
> **londonbabs said:**
> I have the same kind of problem, and followed many instructions off the net on how to enable compiz wallpaper to do so and then disabling show desktop, only thing is, when I do all this and restart x, I have no more wallpaper, it's just transparent, I can see through all windows into my (3 faced) cube and, of course no wallpaper and no icons, anybody had this problem also on Maverick ?

I think that might be what mine is doing. It also disables my opacity and makes all the windows freak out when moving them (the have a trail or whatever it's called when the edges repeatedly repeat themselves).

---

### Post by beccatoria on 2010-11-03
> **Turwaithien said:**
> I think that might be what mine is doing. It also disables my opacity and makes all the windows freak out when moving them (the have a trail or whatever it's called when the edges repeatedly repeat themselves).

Exactly the same problem here... - I found a workaround to fix it by hitting Ctrl+Alt+F1 (which gets you into a kind of fullscreen terminal) followed by Ctrl+Alt+F7, which takes you back to your desktop, with all wallpapers working.

---

### Post by Darent on 2010-11-11
Just wanted to confirm than the trick of switching to a tty with Ctrl+Alt+F6 and switching back to the desktop "solves" the problem and everything works, compiz with diferent wallpapers. You need to do this each time you log in the desktop or if you switch from metacity to compiz...

I have this problem with maverick and one ATI radeon x1600 and the same happened with a x1500 i tested.

Does somebody know how to solve it permanently?

Thanks, and excuse my poor english ;P

---

### Post by terobin on 2010-11-22
Does this stuff only work if you're using the cube? I've got a 3x3 grid and I'm trying to get different wallpapers on each workspace, but so far I'm having no luck.

Unchecking 'show_desktop' in the nautilus config editor doesn't do anything at all for me.

---

### Post by yophaise on 2011-03-25
> **TNT1 said:**
> Once you get your Cube enabled, and your Wallpapers enabled and set up: you have to tell Nautilus **not** to display the (original) desktop.

Open a terminal, and type "**[COLOR=Green]sudo gconf-editor[/COLOR]**" (without the double quotes, of course) and hit enter.

The gconf editor will pop up - it's actually a graphical editor, like  what you're used to working with.  (I just don't know another way to get  it running with root access.  Sooo...)

Under **[COLOR=Teal]Apps->Nautilus->Preferences[/COLOR]** you'll find a checkbox next to "Show Desktop".  Un-check this checkbox.  By the time you click on the OK and get out of the editor, you *should* be able to see the multiple wallpapers you have selected and set up.

i did all of that but nothing changed... halp?

---

### Post by Inygknok on 2011-03-27
I believe I'm having the same problem as you guys.

[http://ubuntuforums.org/showthread.php?t=1715409](http://ubuntuforums.org/showthread.php?t=1715409)

Check the attachment.  Is that what you're getting?

---

### Post by DeMus on 2011-03-27
I use a program called Wallpapoz to show different picture on my desktop. Just point the program to a folder with pictures, set the time you want to look at a picture and that's it.
Find it here: [_Wallpapoz_]("http://wallpapoz.akbarhome.com/")

I find one small discomfort using this program. For example when playing a game, when the desktop-background changes through Wallpapoz the game stutters a little. It seems the program uses a lot of the CPU (or disk read) to slow down the program in the fore-ground.

---

### Post by harjotsandhu on 2011-04-25
> **Darent said:**
> Just wanted to confirm than the trick of switching to a tty with Ctrl+Alt+F6 and switching back to the desktop "solves" the problem and everything works, compiz with diferent wallpapers. You need to do this each time you log in the desktop or if you switch from metacity to compiz...

I have this problem with maverick and one ATI radeon x1600 and the same happened with a x1500 i tested.

Does somebody know how to solve it permanently?

Thanks, and excuse my poor english ;P

I reconfirm. I, however, have nVidia geForce 9100M G. graphics chipset. Used to work great Ubuntu Karmic Koala.

---

### Post by Darent on 2011-04-26
> **harjotsandhu said:**
> I reconfirm. I, however, have nVidia geForce 9100M G. graphics chipset. Used to work great Ubuntu Karmic Koala.

Hello, i completely forgot about this thread until you answer me. Some months ago I found a solution. 
Basicaly, you have to recompile the plugin with a new wallpaper.c that somebody patched in the launchpad bug site. Sorry i can't point you to the adress where i did find it but it has been a long time and the only thing i have is this atached file with the patch and instructions tu aply it.

I wish it helps. Sorry for my english :S

---

