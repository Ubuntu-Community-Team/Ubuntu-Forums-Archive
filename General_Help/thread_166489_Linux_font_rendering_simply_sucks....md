---
title: "Linux font rendering simply sucks..."
date: 2006-04-26
forum: General Help
---

### Post by LightsOut on 2006-04-26
My only gripe with linux right now in a desktop environment (i mainly use kde but I experience this in gnome too) is that fonts basically render like shit. The text just isn't as sharp as it in in windows. The fonts always appear a little bolder and blurrier. I use the MS fonts with the truetype stuff. It still isn't sharp like i would want it. I've googled and googled but I havent found any way to fix this. Anyone else notice this? Anyone ever fix this?

---

### Post by aysiu on 2006-04-26
I beg to differ.

---

### Post by jazzmuzik on 2006-04-26
My TTF fonts are sharp. Do you have an LCD type monitor?

---

### Post by nanotube on 2006-04-26
[QUOTE=LightsOut]My only gripe with linux right now in a desktop environment (i mainly use kde but I experience this in gnome too) is that fonts basically render like shit. The text just isn't as sharp as it in in windows. The fonts always appear a little bolder and blurrier. I use the MS fonts with the truetype stuff. It still isn't sharp like i would want it. I've googled and googled but I havent found any way to fix this. Anyone else notice this? Anyone ever fix this?[/QUOTE]
hmm, fonts render just fine for me... have you tried going to System>Preferences>Fonts and changing some settings? (this is for gnome, don't know where the equivalent would be for kde)

---

### Post by LightsOut on 2006-04-26
yea i have an lcd screen. It shouldnt make a different because fonts on windows using this same screen look fine.

---

### Post by LightsOut on 2006-04-26
[QUOTE=nanotube]hmm, fonts render just fine for me... have you tried going to System>Preferences>Fonts and changing some settings? (this is for gnome, don't know where the equivalent would be for kde)[/QUOTE]

I've tweaked all the setting I can possibly tweak. I've played with the antialiasing and everything and nothing really comes close to being as sharp as they are in Windows. The letters appear to be a little ragged around the edges and just a bit bolder instead of sharp and thin like in xp.

---

### Post by LightsOut on 2006-04-26
[QUOTE=aysiu]I beg to differ.[/QUOTE]

Just by looking at the menu items i can tell that the pic on the right is xp and the one of the left is linux. The one on the right seems a tad bit thinner. Your linux font is still a bit sharper than mine tho. What are your font settings if you dont mind me asking?

---

### Post by aysiu on 2006-04-26
[QUOTE=LightsOut]Just by looking at the menu items i can tell that the pic on the right is xp and the one of the left is linux. The one on the right seems a tad bit thinner. Your linux font is still a bit sharper than mine tho. What are your font settings if you dont mind me asking?[/QUOTE] Anti-aliasing is turned on, as is subpixel hinting.

---

### Post by LightsOut on 2006-04-26
yea i have the same setting pretty much. Fonts in konqueror, firefox, and pretty much every other program that uses a non system type of font, the fonts are kinda blurry and not as sharp like i think they should.

---

### Post by jazzmuzik on 2006-04-26
Just because you've installed MS TTF fonts doesn't mean the browser is using them. You have to go into Preferences and tell it to use Arial for example.

Additionally, it might be worth while going over how to install fonts. There is a truetype font pack you can install via Synaptic...

Manually...

If you have some windows truetype fonts on a windows partition, create a directory called truetype like this:

sudo mkdir /usr/share/fonts/truetype

Copy your windows fonts to this directory:

sudo cp /media/hda1/windows/Fonts/*.ttf /usr/share/fonts/truetype

Fix the permissions:

sudo chmod 644 /usr/share/fonts/truetype/*

Tell the system about the new fonts

sudo fc-cache /usr/share/fonts/

Now, I'm not sure if you need to log out and back in, so do that if it doesn't work. Now go into Firefox, Edit, Preferences and see if you can see fonts like Arial and New Times Roman.

---

### Post by jazzmuzik on 2006-04-26
[QUOTE=LightsOut]yea i have an lcd screen. It shouldnt make a different because fonts on windows using this same screen look fine.[/QUOTE]

Yes, but you may be at a different video sync rate in Windows than in Linux, and that can make a difference. That's why I was thinking you could use the option (or button) on your LCD monitor to find the ideal display size. You press it and it reconfigures the screen to find the ideal sharpness for that particular sync rate.

Additionally, the refresh rate may be too low. If you set it higher you may be able to improve things. Look at System, Preferences, Screen Resolution and try to raise the refresh rate.

---

### Post by ZylGadis on 2006-04-26
Refresh rate doesn't really matter for LCDs (as long as it is above 25Hz, of course, which is the human limit for perceiving smooth video). If he is using his screen's native resolution, that's all he can do for tweaking the monitor.
As far as I know, in Gnome you can set the font size in the Font Preferences, and X will obey that. In other environments (Gdm, for example, which is the Gnome login manager; I suppose KDE, too), you have to manually edit xorg.conf and set the dpi setting. Otherwise you have to use font size 18 or so just to be able to see.
I have set the dpi in my xorg.conf just to be sure, even though I use Gnome;  I use subpixel hinting and antialiasing and everything else I can set in the font preferences menu; I have also installed msttcorefonts, and I use Verdana for all system menus and stuff. Msttcorefonts and Verdana are really artifacts of when I tried adjusting everything I could; I don't really need them, but I'm too lazy to change.
My screen looks perfect :) A fresh install of XP is so ugly in comparison, especially in terms of fonts...

---

### Post by LightsOut on 2006-04-26
would you guys mind posting screen shots of this posting along with the font types you all are using so i can compare with mine?

---

### Post by not28 on 2006-04-26
Font rendering (particularly in firefox) is probably my biggest Linux pet peeve. Being an OSX user, which IMHO has excellent font rendering, this is a huge annoyance. I can't get to my Ubuntu box right now, but I'll try some of the tips given in this thread.

---

### Post by Ramses de Norre on 2006-04-26
This is a screenshot at 1024x1280 and it looks pretty sharp. But I do have some problems with fonts in open office and amsn.

---

### Post by Alienist on 2006-04-26
Yeah, this font thing has been driving me nuts. It would be really helpful if the people who are really satisfied with their font rendering give details of their settings (ie. font, dpi, level of hinting, etc). I've futzed with mine forever and I still can't get something that looks quite right.

---

### Post by Patiek on 2006-04-26
I modified my fonts in firefox to look a bit better with the following settings (found in the screenshot).

---

### Post by LightsOut on 2006-04-26
[QUOTE=Ramses de Norre]This is a screenshot at 1024x1280 and it looks pretty sharp. But I do have some problems with fonts in open office and amsn.[/QUOTE]

yea yours is kinda like mine. its decent but definitely isnt as sharp as it should be.

---

### Post by jazzmuzik on 2006-04-26
[QUOTE=LightsOut]yea yours is kinda like mine. its decent but definitely isnt as sharp as it should be.[/QUOTE]

Windows may still have a bit of an edge on the anti-aliasing. But I wonder if your LCD is part of the problem. Can you post a screenshot?

Here's a screenshot of mine:

[ATTACH]8796[/ATTACH]

---

### Post by MetalMusicAddict on 2006-04-26
I just wanna know why people go as far as to say somthing "simply sucks" instead of asking for help nicely? Im sure you have found good info here and lots of people for whom fonts simply *dont* suck.

With Ubuntu from the start (Warty) Ive been blown away at how much better fonts look than in XP.

---

### Post by not28 on 2006-04-26
[QUOTE=MetalMusicAddict]I just wanna know why people go as far as to say somthing "simply sucks" instead of asking for help nicely? Im sure you have found good info here and lots of people for whom fonts simply *dont* suck.

With Ubuntu from the start (Warty) Ive been blown away at how much better fonts look than in XP.[/QUOTE]
Can you post screenshots/settings, I'd like to see how you have things set up. :mrgreen:

---

### Post by MetalMusicAddict on 2006-04-26
I would have with the above post but I just packed up my PCs. Im moving to North Carolina and Im posting from work. I love showing off my Dell2405 every chance I get but oh well. :)

---

### Post by skymt on 2006-04-26
In my experience, perceived font rendering quality is largely a matter of what you're used to. After switching (mostly) to Linux from the Macintosh, I was annoyed by the "thin, jaggy" fonts. Now OS X rendering is too fuzzy for my adjusted tastes.

In short: you'll get used to it. People always get used to things.

---

### Post by not28 on 2006-04-26
Yeah, that's why only green Linux users complain about something like this. And the problem is only apparent in Firefox. Everything else looks fine.

---

### Post by jazzmuzik on 2006-04-26
[QUOTE=not28]Yeah, that's why only green Linux users complain about something like this. And the problem is only apparent in Firefox. Everything else looks fine.[/QUOTE]

Did you try different fonts in Firefox's Preferences?

---

### Post by not28 on 2006-04-26
[QUOTE=jazzmuzik]Did you try different fonts in Firefox's Preferences?[/QUOTE]

Yes, but I haven't been able to try it extensively because I'm on campus and my Linux machine is at home.

---

### Post by LightsOut on 2006-04-26
[QUOTE=not28]Yeah, that's why only green Linux users complain about something like this. And the problem is only apparent in Firefox. Everything else looks fine.[/QUOTE]

the problem is in firefox, konqueror, and Open Office. Everything else doesn't look THAT bad (i still notice it) but those three definently cause a strain on my eyes. The fonts just render funny. Everything seems much clearer on xp.

Heres a couple screenshots for anyone that was asking...

---

### Post by ZylGadis on 2006-04-27
That's bad indeed. I'm not sure a screenshot would catch that, but what you are experiencing looks to me kind of like a slightly offset phase of your monitor. Have you tried pressing the "audoadjust" button (I mean physical button :) ) on your LCD?
If that does not help, I'd really recommend going down to xorg.conf and adjusting your dpi to 96 or 100 (it looks like it's 75 now). The numbers related to that depend on your resolution, so I can't help much unless I know it. There is a howto somewhere around.

You can get your current dpi like this:

xpdyinfo | grep resolution

---

### Post by sha_man on 2006-04-27
hello, maybe you should try with this thread: [HowTo]("http://www.ubuntuforums.org/showthread.php?t=4456").

And my fonts look like these posted on the screenshot below (zoom to original size for best rendering), this is my /home/username/.fonts.conf:

```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

---

### Post by MOGua on 2006-04-27
[QUOTE=aysiu]I beg to differ.[/QUOTE]

The word "RSS" is rendered pretty bad on your *nix screenshot.

I also feel that font rendering in linux is inferior to Windows ClearType.

I've ran fontconfig countless times with these settings:
auto-hinter, never
auto-hinter, always
native, never
native, always

I also tried playing with the font hintings in System->Preferences->Font

anyways, I will post screenshots of my Segoe UI in XP vs DejaVu Sans in Ubuntu later when I have time.

---

### Post by MOGua on 2006-04-27
Exaustive screenshots:

LOOK AT THE FIREFOX BOOKMARKS TOOLBAR

Ubuntu - Native - Never - Full
[IMG]http://qster.com/screenshots/NativeNever.png[/IMG]

Ubuntu - Native - Never - None
[IMG]http://qster.com/screenshots/NativeNeverNone.png[/IMG]

Ubuntu - Native - Always - Full
[IMG]http://qster.com/screenshots/NativeAlways.png[/IMG]

Ubuntu - Native - Always - None
[IMG]http://qster.com/screenshots/NativeAlwaysNone.png[/IMG]

Ubuntu - Autohinter - Never - Full
[IMG]http://qster.com/screenshots/AutohinterNever.png[/IMG]

Ubuntu - Autohinter - Never - None
[IMG]http://qster.com/screenshots/AutohinterNeverNone.png[/IMG]

Ubuntu - Autohinter - Always - Full
[IMG]http://qster.com/screenshots/AutohinterAlways.png[/IMG]

Ubuntu - Autohinter - Always - None
[IMG]http://qster.com/screenshots/AutohinterAlwaysNone.png[/IMG]

---

### Post by MOGua on 2006-04-27
Exaustive screenshots continued:

LOOK AT THE FIREFOX BOOKMARKS TOOLBAR

Windows - ClearType - Segoe UI
[IMG]http://qster.com/screenshots/WinClearTypeSegoeUI.png[/IMG]

Windows - ClearType - Tahoma
[IMG]http://qster.com/screenshots/WinClearTypeTahoma.png[/IMG]

Windows - ClearType - Calibri
[IMG]http://qster.com/screenshots/WinClearTypeCalibri.png[/IMG]

---

### Post by angkor on 2006-04-27
:shock:  

All this to prove a point? Dude! Have some mercy for the people still on dial up. :)

---

### Post by diegoe on 2006-05-25
If you are using Dapper try my packages here:

[http://ubuntuforums.org/showthread.php?t=182164](http://ubuntuforums.org/showthread.php?t=182164)

---

### Post by PictureThis on 2006-06-13
Finally, sunny conditions inside and outside :cool: 

[[IMG]http://img60.imageshack.us/img60/8933/screenshot37kt.th.png[/IMG]](http://img60.imageshack.us/my.php?image=screenshot37kt.png)

(Anti-aliasing just doesn't work for me ;) )

---

### Post by sicofante on 2006-06-17
By the screenshots from MOGua is pretty obvious to me that Windows renders fonts much better. As a matter of fact, I got here looking for answers about why font rendering in Ubuntu is so bad. Is funny to read this has to do with "being used" (that's a typical Linux excuse, BTW). How does one get used to blurry fonts???

I've been reading somewhere that there are patents preventing Linux font rendering to be as good as Microsoft's. Is this a dead end? Is there any hope, beyond waiting for MS Cleartype patents to expire in 2020 or hoping for ultra high res monitors?

---

### Post by hinachan on 2006-07-10
> **MOGua said:**
> Exaustive screenshots continued:

LOOK AT THE FIREFOX BOOKMARKS TOOLBAR


All three of those have pretty blurry fonts.  The screencap earlier in this thread is much clearer. :)

I tried to eliminate the anti-aliasing (as suggested elsewhere in this thread), but it was impossible.  I made the changes, but there was no "OK" or "APPLY" button to apply them, so as soon as I closed the window...back to blurry font city! :(

Surely, somebody here has to know how to apply changes and make them stick?  Please, before I dehydrate from the watery eyes the default fonts are giving me!! :-?

---

### Post by calande on 2006-07-11
This thread will solve your problem ;)
[http://www.ubuntuforums.org/showthread.php?t=208396](http://www.ubuntuforums.org/showthread.php?t=208396)

---

### Post by hinachan on 2006-07-11
Thank you very much...I didn't find this in my search. :)

---

### Post by hinachan on 2006-07-11
> **skymt said:**
> In short: you'll get used to it. People always get used to things.
Actually, a lot of people can't get used to it, due to vision problems or (in my case) neurological problems that are aggravated by excessive eyestrain.  When I was experimenting with the Ubuntu live CD, people looking over my shoulder were complaining of getting headaches from it.  It's less of a problem with, say, Knoppix or Damn Small Linux, but it's still a problem...especially in OpenOffice.org.  It's not a matter of my being "green", it's a matter of messy fonts causing eyestrain...which, quite frankly, is a problem that should be addressed by the developers of the distros, not the users. ;)

---

### Post by scoutme on 2006-09-16
the best font setup in gnome is, according to me, rgb antialias with NO hint at all. The result is exactly what you have in macosx (they do not use hinting, and use enormous font sizes...), if you choose right fonts.

I'd like windows font rendering, that is way better than macos one, but this solution isn't that bad

---

### Post by calande on 2006-09-16
I don't like fonts in OS X, they are not clear to the eye either...

---

### Post by etc on 2006-09-16
> **diegoe said:**
> If you are using Dapper try my packages here:

[http://ubuntuforums.org/showthread.php?t=182164](http://ubuntuforums.org/showthread.php?t=182164)

Seconding this.

---

### Post by smdeep on 2006-12-22
Hi
I just had to add my two cents. Font rendering is very subjective. No two people can agree on the quality of rendering. For example, I hate Cleatype on WinXP. I never use it. I love the way fonts are rendered in Standard mode on WinXP on both CRT and TFT monitors. I currently use a Samsung 740N. I dont like the Linux way of font rendering and positively hate the font rendering on the iBook G4 OSX 10.4.8 and the Mac Mini (same version of OSX). Personally I like the way fonts are rendered on WinXP standard mode. Some people love antialiased fonts some people hate it. For a long time I could not use Linux full time because of Font rendering. I now use Kubuntu/Ubuntu full time. I have disabled antialiasing for fonts 6pts to 10 and like it . 

Lets not quarrel over font rendering. It is just that some poeple like fonts rendered in a particular way. Fiddle with the font settings in both KDE and Gnome and I am sure everyone will find some setting to their liking.

My biggest concern with font rendering on Kubuntu/Ubuntu at the moment is the greenish cast on fonts. As soon as I have figured out how to get rid of it I will be a much happier man.

:)

---

### Post by calande on 2006-12-22
Namaste, could you provide us with a screenshot of your greenish cast fonts?
Did you have a look at my [tutorial]("http://ubuntuforums.org/showthread.php?t=208396") to display fonts like on Windows?
;)

---

### Post by smdeep on 2006-12-22
Namaste! I am checking out your tutorial at the moment. I will report back.

:)

---

### Post by smdeep on 2006-12-22
> **calande said:**
> Namaste, could you provide us with a screenshot of your greenish cast fonts?
Did you have a look at my [tutorial]("http://ubuntuforums.org/showthread.php?t=208396") to display fonts like on Windows?
;)

Hi

I am happy to report that I am going to nominate you for the Nobel Prize for Font Management under GNU/Linux. Your font.local config rocks! Finally I am very, very happy.

You should write up a tutorial and I am sure it will get slashdotted. I have tried a lot of configs, etc., but this one is surely the best. These files should work for most if not all distros??

Thanks a million, you have saved the eyes of a 42 year old man!
:)

---

### Post by sml on 2007-06-19
> **smdeep said:**
> Hi
Lets not quarrel over font rendering. My biggest concern with font rendering on Kubuntu/Ubuntu at the moment is the greenish cast on fonts.
:)

Lets not quarrel over the colour of fonts either.

---

### Post by screaminj3sus on 2007-06-19
[http://ubuntuforums.org/showthread.php?t=343670&highlight=Improve+font+rendering](http://ubuntuforums.org/showthread.php?t=343670&highlight=Improve+font+rendering)

This Dramatically improved fonts onmy LCD, looks Just as good as XP now. I do agree, on an LCD the default font rendering in ubuntu looks horrible.

---

### Post by calande on 2007-06-19
Great! Happy to see your fonts look the way you want :)

---

### Post by ub-noob on 2007-06-22
> **jazzmuzik said:**
> Just because you've installed MS TTF fonts doesn't mean the browser is using them. You have to go into Preferences and tell it to use Arial for example.

Additionally, it might be worth while going over how to install fonts. There is a truetype font pack you can install via Synaptic...

Manually...

If you have some windows truetype fonts on a windows partition, create a directory called truetype like this:

sudo mkdir /usr/share/fonts/truetype

Copy your windows fonts to this directory:

sudo cp /media/hda1/windows/Fonts/*.ttf /usr/share/fonts/truetype

Fix the permissions:

sudo chmod 644 /usr/share/fonts/truetype/*

Tell the system about the new fonts

sudo fc-cache /usr/share/fonts/

Now, I'm not sure if you need to log out and back in, so do that if it doesn't work. Now go into Firefox, Edit, Preferences and see if you can see fonts like Arial and New Times Roman.

Hi,

I used the above commands and copied my windows fonts.  Now all the fonts are messed up.  For eg. if I go to System->Preferences->Fonts, I don't see any text all I see is squares, in the menu description, drop down values..  The desktop is fine.  The Application, System and other desktop menus are fine.

How can I fix this.

Thank you.

---

