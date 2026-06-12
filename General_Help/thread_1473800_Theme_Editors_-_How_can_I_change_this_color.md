---
title: "Theme Editors - How can I change this color?"
date: 2010-05-05
forum: General Help
---

### Post by Roasted on 2010-05-05
Any idea? I want to change the reddish/orangeish/pinkish color to something else, such as a slate gray or something. What file do I need to edit? gtkrc? xml?

[[IMG]http://img266.imageshack.us/img266/8563/screenshota.png[/IMG]](http://img266.imageshack.us/i/screenshota.png/)

---

### Post by WorMzy on 2010-05-05
If you don't mind installing a program, try gnome-color-chooser. It'll let you change any colour that your theme uses.

---

### Post by Roasted on 2010-05-05
> **WorMzy said:**
> If you don't mind installing a program, try gnome-color-chooser. It'll let you change any colour that your theme uses.

I know, but I want to zip this up into a theme and submit it to gnome-look.org. So I want it to be "complete".

---

### Post by WorMzy on 2010-05-05
Oh, I see. I have no experience with this, but looking at Ambience theme, it seems colours are set in the '/gtk-2.0/gtkrc' file.

---

### Post by Roasted on 2010-05-07
anybody?

---

### Post by Roasted on 2010-05-08
:mad:

---

### Post by kolinab on 2010-05-09
Sorry, I don't know either . . . but I did put together some links last night where I think the answer can be found. Looks like this theme tweaking can be pretty time consuming. There are some tutorials in the links I posted at:

[http://ubuntuforums.org/showthread.php?t=1476845](http://ubuntuforums.org/showthread.php?t=1476845)

---

### Post by Roasted on 2010-05-09
It was easy for me to find the other colors, because I would simply take a screenshot, use the eyedropper tool in gimp, find the hex value of the color and then search for it in the gtkrc and xml files. But with that particular color since it has a sense of "fading" to it, it's not 1 solid color, so I can't seem to find it as easily as the others...

---

### Post by Roasted on 2010-05-09
This is what I don't like:

[http://yfrog.com/2qscreenshot1tp](http://yfrog.com/2qscreenshot1tp)

When I go through directories that have a lot of items, I get this for a split second. I don't like the pink. This little thing popping up constantly annoys me moreso than I ever thought. I want to change it. How can I change it?

---

### Post by WorMzy on 2010-05-09
According to my Gnome Color Chooser, that one is stored as base[NORMAL].

---

### Post by Roasted on 2010-05-09
I looked at that, but I can't seem to figure out exactly where the issue is. When I did a search of the entire GTKRC file for base[NORMAL], the only color code associated with any of the entries found was 300a24, which is a purple color.

Here's the pastebin of the GTKRC file. Any ideas?

[http://pastebin.com/CZ3eZaPG](http://pastebin.com/CZ3eZaPG)

---

### Post by Roasted on 2010-05-10
up :confused:

---

### Post by Roasted on 2010-05-12
up'ing till I can figure it out. Any ideas?

---

### Post by stinkeye on 2010-05-12
I think it's called "radiocheck" in your gtkrc.
Line 452 of your pastebin file.

---

### Post by john1066 on 2010-05-12
Hate to say it - but glad to see I'm not the only one with this problem. What a shocking color that pink - and all my videos now run pinkish as well. Can only imagine this is some sort of joke. Enough to send you to Windows 7. Sorry to say I have no solution for you.

John

---

### Post by x-shaney-x on 2010-05-12
I think #B02610 is the colour.
It doesn't look like the colour you see in the theme because it is mixed with the foreground or background colour (or both).

---

### Post by Roasted on 2010-05-12
Hmm... this is weird. I searched for B02610 but I didn't find it. I don't know how my gtkrc differed from the paste bin, but when I searched for that entry in that segment I had listed this color as follows - FE765E.

I opened gimp, plugged that in and saw it was indeed a pink color. I adjusted it accordingly but NOTHING CHANGED.

I need to get rid of this pink color. It's such a puke thing to look at, even if it's only for a split second.

Any ideas?

---

### Post by Landshark on 2010-05-12
Editing the colors in themes doesn't seem to do it, since the "pink" continues to exist within manu themes.  Same with gnome-color-chooser: The pink doesn't seem to show up as an existing color, so I don't know what to change.  But the color itself literally hurt my eyes and may drive me back to another distro.  Even as I write this, the background of the input box is that DAMN PINK.

So much good work went into this release, and there isn't any clear way to change this default? WTF.

---

### Post by x-shaney-x on 2010-05-12
I'm slightly confused now.
I looked at the Ambiance gtkrc and it is indeed #FE765E that gives the pink colour.

Personally I like the colour so I have kept it in my own custom mod but I have just tried changing ALL the #FE765E entries in gtkrc to #2BD934, which is a bright green colour so I would notice what had changed and it did change all the pink to green.

Presumably you have your modified version in your own .themes directory?
Could it be there is a mistake in your own theme causing it to be ignored so when you select Ambiance it is actually using the one in /usr/share/themes?  (I have done that myself).  Unless you have already re-named it then ignore what I said.

---

### Post by Landshark on 2010-05-12
Sorry. I was poaching someone else's thread.  Didn't mean to be a troll and will step to the sidelines. One quick question:

The text box within which I am typing this reply really is purple-pink. Within the theme profile, how is this area designated? Is this the bg_color or base_color?

---

### Post by x-shaney-x on 2010-05-12
It *should* be base_color but that isn't always the case with all themes.
In the default Ambiance/Radiance themes base_color is set to #ffffff which is white.

---

### Post by Roasted on 2010-05-12
It seems as if it was something more than that ONE line in the area of 452. Because as somebody else said, they changed ALL instances of the pink hex color to green and it worked. I too changed all instances of the pink hex color to "777777" which is a gray-ish color. In fact, when it was all said and done I didn't think it was half bad.

The only thing is, not only did it change the background color when switching through directories (which is awesome) but it changed the actual color of the buttons when you select something, such as downloading a file and it says open with or save.

So I threw it in a Google Doc. If you wish, download it and try it out. I also suggest that you download a file, doesn't matter what. Anything to get the pop up screen that says "Open With... *programs listed here*" and "Save File As", etc. 

Tell me what you think about that color. Now that I know exactly where it needs changed, I'll find a really good color to throw in that place and re-upload it to Gnome-Look.org.

[http://docs.google.com/leaf?id=0B96Ld5Ukgbx8MjNkYjRmMmMtOWM4Yy00OTEzLWI1ODMtNTBiZmI0ZTU5N2M5&hl=en](http://docs.google.com/leaf?id=0B96Ld5Ukgbx8MjNkYjRmMmMtOWM4Yy00OTEzLWI1ODMtNTBiZmI0ZTU5N2M5&hl=en)

---

### Post by Roasted on 2010-05-13
I threw together a slightly different one, offering a burnt-orange color for the progress bar when moving files/downloading files, etc. The only thing is, this goes hand in hand with that background problem from before.

The upside? A light orange color is more pleasing to the eyes than a light pink color as I was dealing with before.

So the big question comes about - Is it possible I can actually SEPARATE the progress bar color from the background color in Nautilus?

Here's the other mockup I did:

[http://docs.google.com/leaf?id=0B96Ld5Ukgbx8NTg5MDZkYzktNTBiNy00Nzg1LWI1MzYtYjYwMDZhMDhhMGVl&hl=en](http://docs.google.com/leaf?id=0B96Ld5Ukgbx8NTg5MDZkYzktNTBiNy00Nzg1LWI1MzYtYjYwMDZhMDhhMGVl&hl=en)

---

### Post by Landshark on 2010-05-13
Thank you. I will play around with these.

---

### Post by Roasted on 2010-05-13
I'm kind of in a sticky situation here. I can't seem to figure out how to separate the Nautilus background color from the progress bar. So I need to choose a color that doesn't look pinkish when going through Nautilus BUT also flows nicely with the rest of the theme.

Any suggestions on color choices?

OR

Any suggestions on how I can separate the progress bar color from the Nautilus background color?

---

### Post by x-shaney-x on 2010-05-13
@ Roasted

When I tried your themes my nautilus background stayed white.
Are you sure you don't have it set to a custom colour within nautilus?

---

### Post by Roasted on 2010-05-13
> **x-shaney-x said:**
> @ Roasted

When I tried your themes my nautilus background stayed white.
Are you sure you don't have it set to a custom colour within nautilus?

Yes - positive I don't. The background color doesn't come up all of the time. It seems it only comes up when I navigate through directories that have a TON of things inside. For example when I open my Pictures folder, I have about 17,000 pictures in various folders and freely roaming in the main Pictures folder itself. When I hit that and navigate forward/back from there I almost always see the background color. In a lot of instances though, it does stay white.

---

### Post by Roasted on 2010-05-13
K. Got it.

[http://docs.google.com/leaf?id=0B96Ld5Ukgbx8ODljMDFmNmQtMWRmZC00Zjk2LWExMjQtZmQzOWFjMTk5NTYz&hl=en](http://docs.google.com/leaf?id=0B96Ld5Ukgbx8ODljMDFmNmQtMWRmZC00Zjk2LWExMjQtZmQzOWFjMTk5NTYz&hl=en)

You guys who have edited the GTKRC in this instance would know that there are 6 occurances of the colors we were changing to figure it out. I went down each one and adjusted only 1 at a time and would re-compress, and re-add the theme accordingly. I found which one it is. It's the entry on line 115 of the GTKRC file.

I uploaded YET ANOTHER version of this theme. It has a burnt orangish progress bar, and a relatively dark gray/dark tan "focus color". This focus color is what we SOMETIMES see in the background of Nautilus when we navigate through folders, etc. I also noticed this color effects the way the "tabs" are shaded in certain menus. Example - Go to Appearances, pick a theme, and hit "customize". See how the main tab you're on had a different color to it, particularly a grayish shade? That color entry in the GTKRC file directly corresponds with the background color in Nautilus when moving through folders. I think the color I picked was half decent.

NOW... any last recommendations? Is there any other suggestions about the color of the progress bar, etc? 

Can I just say I had no involvement with creating the original Ambiance theme. I just really liked that theme but wanted to change the colors and dove into it more heavily than I expected I would. Anyway when this is all said and done I'll re-upload it to gnome-look.org, overwriting my current "Ambiance - v2" entry I have now. Kudos to the original authors of this theme. 

Any last suggestions as I express my open source right to change this theme around? (as noted in the theme itself). :)

---

### Post by Roasted on 2010-05-17
Okay - new color I'd like to change.

When I highlight something in openoffice spreadsheet, or often times on certain web sites with a drop down list, the highlight color is very light.

Does anybody have a clue where in this GTKRC file I could edit that color??

[http://pastebin.org/242887](http://pastebin.org/242887)

---

### Post by Roasted on 2010-05-18
:confused::confused::confused:

---

### Post by Roasted on 2010-05-18
:(:(:(

---

### Post by Roasted on 2010-05-21
:(:(:(

---

### Post by Roasted on 2010-05-24
Come on. No ideas???

---

