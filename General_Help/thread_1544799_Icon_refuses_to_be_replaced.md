---
title: "Icon refuses to be replaced"
date: 2010-08-03
forum: General Help
---

### Post by HelloIndustries on 2010-08-03
**Final update: **No matter what has been tried throughout this thread, the gnome foot icon refuses to budge, so: I give up.
I'll update this again *IF* the creator of the icons ever responds to me....



```
Hi all.

I'm using this icon theme:
[http://tiheum.deviantart.com/#/d2v6x24](http://tiheum.deviantart.com/#/d2v6x24)

The icon theme is Faenza, and it's currently doing the popular rounds, and well deserved it is, too. Great icon theme.

Anyway; I want to use my own start-here.png.
I've replaced it everywhere i can think of:

/home/USER/.icons/Faenza/places/16
/home/USER/.icons/Faenza/places/22
/home/USER/.icons/Faenza/places/24
/home/USER/.icons/Faenza/places/32
/home/USER/.icons/Faenza/places/48
/home/USER/.icons/Faenza/places/scalable

Edit: Also all the usr/share/icons versions

Yet still the icon (gnome foot) remains, and i can't figure out why.

Anyone got any ideas?
```

---

### Post by HelloIndustries on 2010-08-06
I hate to have to bump this, but it's annoying me and i'd really appreciate the help.

---

### Post by WorMzy on 2010-08-06
What "start-here.png"? Do you mean the distributor logo that's shown next to the Application's menu?

Try naming the file "distributor-logo.png".

---

### Post by HelloIndustries on 2010-08-06
> **WorMzy said:**
> What "start-here.png"? Do you mean the distributor logo that's shown next to the Application's menu?

Try naming the file "distributor-logo.png".

That's the one, yeah.

The dist logo isn't it, and all other instances of the icon have been replaced with me preferred icon. It's really odd.

Technically, it SHOULD be the icon i want, now.
Unfortunately for me, the creator of the icons isn't replying to my question about this (via his/her deviantart page).

---

### Post by pastalavista on 2010-08-06
Have you tried putting it in /user/share/icons ? I don't mess with appearance much but that's where all my theme icons are.

---

### Post by HelloIndustries on 2010-08-06
> **pastalavista said:**
> Have you tried putting it in /user/share/icons ? I don't mess with appearance much but that's where all my theme icons are.


D'oh! How could i forget that!
Anyway, i've replaced all those, restarted the panel, and switched from, and back to the icon theme and it's STILL there! I'm confused now....

---

### Post by WorMzy on 2010-08-06
After checking it out, it does seem to be the start-here icon that gets used. Where are you putting it?

"~/.icons/THEMENAME/scalable/places/start-here.png" works for me. You have to restart gnome-panel for the change to take effect.

---

### Post by HelloIndustries on 2010-08-06
Yeah. i've done all that, replaced all instances of start-here.png/.svg with my preferred icon in:

usr/share
username/icons

Yet still it refuses. And it's just this one icon, i've replaced a few others without problem.

---

### Post by Izobalax on 2010-08-07
I'm using Faenza-Dark but curiously the changes I made to get a different "start-here.png" were made in standard "Faenza":

1. Copied the ubuntu "distributor-logo.png" from "/home/USER/.icons/places/24/"
2. Backed up the gnome foot icon "start-here.png" as "start-herebak.png"
3. Pasted in the Ubuntu icon in the same folder and re-named it "start-here.png". 
4. Alt+F2 > "killall gnome-panel". 
5. New start-here icon works. 

And this is for the menubar applet. You do it different for the main menu single icon applet.

/izo\

---

### Post by HelloIndustries on 2010-08-07
> **Izobalax said:**
> I'm using Faenza-Dark but curiously the changes I made to get a different "start-here.png" were made in standard "Faenza":

1. Copied the ubuntu "distributor-logo.png" from "/home/USER/.icons/places/24/"
2. Backed up the gnome foot icon "start-here.png" as "start-herebak.png"
3. Pasted in the Ubuntu icon in the same folder and re-named it "start-here.png". 
4. Alt+F2 > "killall gnome-panel". 
5. New start-here icon works. 

And this is for the menubar applet. You do it different for the main menu single icon applet.

/izo\


Well, so far i have this:

[IMG]http://i901.photobucket.com/albums/ac212/helloiamdene/starthere.jpg[/IMG]

---

### Post by WorMzy on 2010-08-07
After examining one of the scripts that came with the icon pack I'm using (which has the option to change the distributor's logo) it could be controlled by ~/.icons/THEMENAME/apps/checkbox-gtk.[png|svg]

---

### Post by HelloIndustries on 2010-08-07
> **WorMzy said:**
> After examining one of the scripts that came with the icon pack I'm using (which has the option to change the distributor's logo) it could be controlled by ~/.icons/THEMENAME/apps/checkbox-gtk.[png|svg]


I looked in username/.icons/faenza/apps/[sizes]/ but there is no checkbox-gtk.
There is a checkbox.png, but that literally looks like a checkbox, not the gnome foot.

---

### Post by WorMzy on 2010-08-07
It's definitely not checkbox, that image exists in this theme too, but it's something unrelated.

Are you using faenza? because according to the deviantart page, it comes with a script to set the distribution logo too.

---

### Post by HelloIndustries on 2010-08-07
> **WorMzy said:**
> It's definitely not checkbox, that image exists in this theme too, but it's something unrelated.

Are you using faenza? because according to the deviantart page, it comes with a script to set the distribution logo too.

Previously, i installed without running the script.
I tried the script and i just get errors:

```
Icon themes will be installed in /home/dene/.icons. To make them available for all users, run this script as root.
Do you want to continue ? [Y]es, [N]o : y
tar: Faenza.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Faenza-Dark.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Which distributor logo do you want to use ? [D]ebian, [F]edora, [L]inux Mint, [O]pensuse, [M]andriva, [U]buntu : u
/media/Data/GUI/Ubuntu/Icons/Faenza_Icons_by_tiheum/install.sh: line 34: cd: ./Faenza/places/scalable/: No such file or directory
/media/Data/GUI/Ubuntu/Icons/Faenza_Icons_by_tiheum/install.sh: line 35: cd: ./Faenza/places/48/: No such file or directory
/media/Data/GUI/Ubuntu/Icons/Faenza_Icons_by_tiheum/install.sh: line 36: cd: ./Faenza/places/32/: No such file or directory
/media/Data/GUI/Ubuntu/Icons/Faenza_Icons_by_tiheum/install.sh: line 37: cd: ./Faenza/places/24/: No such file or directory
/media/Data/GUI/Ubuntu/Icons/Faenza_Icons_by_tiheum/install.sh: line 38: cd: ./Faenza/places/22/: No such file or directory
/media/Data/GUI/Ubuntu/Icons/Faenza_Icons_by_tiheum/install.sh: line 39: cd: ./Faenza/places/16/: No such file or directory

cp: cannot stat `./Faenza/': No such file or directory
cp: cannot stat `./Faenza-Dark/': No such file or directory
Installation complete. Enjoy !
```


Looking at the themes distributor logos, none of them are the gnome foot icon i'm trying to replace, so i'm not sure how it'll help.

I'm confused :(

---

### Post by WorMzy on 2010-08-07
Interesting. I downloaded the theme and ran the script, and it ignored my choice completely and gave me the foot.

So I replaced ~/.icons/Faenza-Dark/places/[16|22|24]/start-here.png with the other theme's start-here.svg, restarted gnome-panel, and the image changed.

I can't say why the script didn't work for you.. did you cd to the script's directory before you ran it, or did you just run it from ~?

---

### Post by HelloIndustries on 2010-08-07
> **WorMzy said:**
> Interesting. I downloaded the theme and ran the script, and it ignored my choice completely and gave me the foot.

So I replaced ~/.icons/Faenza-Dark/places/[16|22|24]/start-here.png with the other theme's start-here.svg, restarted gnome-panel, and the image changed.

I can't say why the script didn't work for you.. did you cd to the script's directory before you ran it, or did you just run it from ~?


it works (and did previously) for the Main Menu applet, but not for the Menu Bar applet, which is the one i want to change.

The script refuses to install the damn icons, so i had to do it manually.

---

### Post by WorMzy on 2010-08-07
I just tried it with the normal Faenza theme, and replacing the various start-here.pngs worked fine with that theme too; both Main Menu and Menu Bar use the start-here.svg I replaced it with.

You've replaced the icon in every folder, right?
~/.icons/Faenza/places/16
~/.icons/Faenza/places/22
~/.icons/Faenza/places/24
~/.icons/Faenza/places/32
~/.icons/Faenza/places/48
~/.icons/Faenza/places/scalable [it's a .svg in here]
~/.icons/Faenza-Dark/places/16
~/.icons/Faenza-Dark/places/22
~/.icons/Faenza-Dark/places/24

If so, I really don't know why it's refusing to change. You could try switching to a different theme and then back again, to see if that forces it to update the image.

---

### Post by HelloIndustries on 2010-08-07
> **WorMzy said:**
> I just tried it with the normal Faenza theme, and replacing the various start-here.pngs worked fine with that theme too; both Main Menu and Menu Bar use the start-here.svg I replaced it with.

You've replaced the icon in every folder, right?
~/.icons/Faenza/places/16
~/.icons/Faenza/places/22
~/.icons/Faenza/places/24
~/.icons/Faenza/places/32
~/.icons/Faenza/places/48
~/.icons/Faenza/places/scalable [it's a .svg in here]
~/.icons/Faenza-Dark/places/16
~/.icons/Faenza-Dark/places/22
~/.icons/Faenza-Dark/places/24

If so, I really don't know why it's refusing to change. You could try switching to a different theme and then back again, to see if that forces it to update the image.

Yep, all replaced, and even checked the fallback/inherit thems just in case. It isn't there any more, yet the icon persists after an icon theme switch, and a gnome panel kill/restart.

I agree, it's very, very odd.
I suppose i'll just have to live with the smaller menu (with chosen icon) over the other, standard menu with the horrible foot....

Maybe one day the creator of the icons will respond....

Thanks for the help, anyway :)

---

### Post by WorMzy on 2010-08-07
No problem, sorry we couldn't get it working. :(

---

### Post by HelloIndustries on 2010-08-07
> **WorMzy said:**
> No problem, sorry we couldn't get it working. :(

It's all good. We all tried, that's the main thing :)

---

### Post by Izobalax on 2010-08-07
You can use [Cardapio](http://www.omgubuntu.co.uk/2010/06/cardapio-alternative-gnome-panel-menu.html) menu if you want, it's pretty much replaced the menubar for me. 

/izo\

---

### Post by skrimpy on 2010-09-02
Don't know if you figured out a way around this, but if not...

I use the same icon set as you and didn't want the foot on my panel bar.  I used Ubuntu Tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) to change it to the icon I wanted.

Just grab Ubuntu Tweak then go to Desktop --> Gnome Settings and click the foot icon next to where it says "Click this button to change the menu logo image"

---

