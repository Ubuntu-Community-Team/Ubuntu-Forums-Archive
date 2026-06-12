---
title: "installing new fonts"
date: 2011-04-07
forum: General Help
---

### Post by gggecko on 2011-04-07
Hey guys,

I am wondering how to install new fonts on Ubuntu 9.10 netbook remix. I've only ever installed fonts on windows xp before and am confused about how to do this. Thanks in advance.

GGGecko

---

### Post by falko on 2011-04-07
Install the package ttf-mscorefonts-installer - this will give you Windows TTF fonts such as Arial, Times New Roman, etc.

---

### Post by gggecko on 2011-04-07
Sorry, I wasn't very specific with the question. What I meant was other, non-core fonts, like subway, ethopool etc. I have all the fonts I want on my USB but don't know where to put them. But thanks for helping me get the core fonts :).

---

### Post by coffeecat on 2011-04-07
If they are .ttf font files, open your home folder and press ctrl-H to show hidden files and folders. Now create a new folder called '.fonts' (no quotes) if not already there. Don't forget the leading dot - this makes it hidden. Now simply open the .fonts folder and copy your .ttf files in there. Fonts installed!

In fact, some other font types are supported this way. If not ttf simply try them and see.

This way installs the fonts for your account only. If you want them installed system-side for all accounts/users, post back and I'll show you how.

When you get to run a version of Ubuntu newer than 9.10, all you do is double-click on the font file and it will get installed. You might want to think of upgrading or reinstalling soon because 9.10 is about to go end-of-life and be unsupported.

---

### Post by deathadder on 2011-04-07
You may need to regenerate the font cache using the following command afterwards:
```
sudo fc-cache -f -v
```
The alternative is to restart X

---

### Post by gggecko on 2011-04-07
> **coffeecat said:**
> If they are .ttf font files, open your home folder and press ctrl-H to show hidden files and folders. Now create a new folder called '.fonts' (no quotes) if not already there. Don't forget the leading dot - this makes it hidden. Now simply open the .fonts folder and copy your .ttf files in there. Fonts installed!

In fact, some other font types are supported this way. If not ttf simply try them and see.

This way installs the fonts for your account only. If you want them installed system-side for all accounts/users, post back and I'll show you how.

When you get to run a version of Ubuntu newer than 9.10, all you do is double-click on the font file and it will get installed. You might want to think of upgrading or reinstalling soon because 9.10 is about to go end-of-life and be unsupported.
I tried this, ended up with a folder called .fonts that had a few new truetype fonts in it, but then I used open office word processor a couple of minutes later and the fonts were not there! do I just need to reboot, or is there something else?

GGGecko

---

### Post by ~Plue on 2011-04-07
> **gggecko said:**
> I tried this, ended up with a folder called .fonts that had a few new truetype fonts in it, but then I used open office word processor a couple of minutes later and the fonts were not there! do I just need to reboot, or is there something else?

GGGeckono need to reboot, just do as in post #5 and it'll appear

---

### Post by gggecko on 2011-04-07
> **~Plue said:**
> no need to reboot, just do as in post #5 and it'll appear
I tried that aswell but it didn't seem to make a difference, should I also consider waiting 'till I've upgraded from 9.10?
cheers

---

### Post by ~Plue on 2011-04-07
upgrading wouldn't make a difference... they are just fonts..
did you restart open-office afterwards ?

---

### Post by gggecko on 2011-04-07
> **~Plue said:**
> upgrading wouldn't make a difference... they are just fonts..
did you restart open-office afterwards ?
ah... thankyou, I didn't close it before having another look at it, thanks to everyone who helped.:)

---

### Post by dirty_harry on 2011-04-07
might be useful:

```
gksudo nautilus /usr/share/fonts/
```

---

### Post by searchfgold6789 on 2011-04-07
If you LOVE fonts then try the link in my signature ;)
Have a nice day,
 - search

---

### Post by coffeecat on 2011-04-07
> **deathadder said:**
> You may need to regenerate the font cache using the following command afterwards:
```
sudo fc-cache -f -v
```The alternative is to restart X

As a point of information, you have to run fc-cache if you copy fonts into a subfolder in /usr/share/fonts/ but it is not necessary for fonts in ~/.fonts. I see a lot of posts saying you have to run fc-cache after putting fonts into ~/.fonts; you don't.

It used to be in earlier releases of Ubuntu that you had to restart the xserver to see the fonts, but this hasn't been so for some time now. It really is very elegant now. Copy the fonts into ~/.fonts and you are ready to go.

The OP needed to restart OpenOffice to see the new fonts, which I see they have done now.

---

### Post by deathadder on 2011-04-07
> **coffeecat said:**
> As a point of information, you have to run fc-cache if you copy fonts into a subfolder in /usr/share/fonts/ but it is not necessary for fonts in ~/.fonts. I see a lot of posts saying you have to run fc-cache after putting fonts into ~/.fonts; you don't.

It used to be in earlier releases of Ubuntu that you had to restart the xserver to see the fonts, but this hasn't been so for some time now. It really is very elegant now. Copy the fonts into ~/.fonts and you are ready to go.

The OP needed to restart OpenOffice to see the new fonts, which I see they have done now.
I tend to only throw fonts in /usr/share/fonts, it's good to know about not needed fc-cache for ~/.fonts :)

---

### Post by coffeecat on 2011-04-07
> **deathadder said:**
> I tend to only throw fonts in /usr/share/fonts, it's good to know about not needed fc-cache for ~/.fonts :)

It's really very impressive how quickly they get picked up. :) Also, something I mentioned to the OP, from Lucid onwards if you double-click on a ttf font, a "font-viewer" window opens with a preview of the font and an "Install Font" button. This creates ~/.fonts if not present and copies the file into it. I don't think many people have discovered this yet, because I haven't seen it mentioned in "how do I install fonts?" threads. Or perhaps I missed the ones that were.

---

### Post by deathadder on 2011-04-07
Cool, good to know! 

Thanks for sharing :)

---

### Post by ~Plue on 2011-04-07
> **coffeecat said:**
> As a point of information, you have to run fc-cache if you copy fonts into a subfolder in /usr/share/fonts/ but it is not necessary for fonts in ~/.fonts. I see a lot of posts saying you have to run fc-cache after putting fonts into ~/.fonts; you don't.

It used to be in earlier releases of Ubuntu that you had to restart the xserver to see the fonts, but this hasn't been so for some time now. It really is very elegant now. Copy the fonts into ~/.fonts and you are ready to go.

The OP needed to restart OpenOffice to see the new fonts, which I see they have done now.
ah..didn't know that. thanx :)

---

