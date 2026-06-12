---
title: "Panel transparency doesn't work"
date: 2010-04-30
forum: General Help
---

### Post by blazemore on 2010-04-30
Good evening everyone (or whatever the time is where you are)

I have a problem, well not really a problem, more of an annoyance.

I'm using Ubuntu 10.04 LTS, and I'm trying to make my panel semi-transparent.

Unfortunately, the whole thing won't go transparent, only the blank areas without applets!

I know you can hack it in Compiz, but then *everything* goes transparent, including text and icons, which I don't want.

As you can see from the screenshot, I'm using the Radiance theme, but this also occurs with Ambience.

Any ideas?
Thanks!

---

### Post by karmic-koala on 2010-05-01
Doesn't work for me either. Have you tried this :

[http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244](http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244)

I am a bit skeptic though.

---

### Post by WorMzy on 2010-05-01
Change your theme (Systtem -> Preferences -> Appearance) from Ambiance to something else. I have a custom theme using Clearlooks controls and Mono-Light icons and transparency works fine*.


*in the usual 'not-real-transparency' GNOME way.

---

### Post by karmic-koala on 2010-05-01
Nay, doesn't work for me. I am using orange-theme and transparency doesn't work. Have a look
[http://yfrog.com/jmscreenshotnohp](http://yfrog.com/jmscreenshotnohp)[IMG]http://yfrog.com/jmscreenshotnohp[/IMG]
Doesn't work in Radiance as well. (just for info, I am on Lucid)

---

### Post by WorMzy on 2010-05-01
Have you set the panel to use transparency? (Right-click on the panel -> Properties -> Background)

---

### Post by karmic-koala on 2010-05-01
Okay, maybe there's a wee mixup here. I was referring to transparency behind icons in panel and not making the whole panel transparent.

For example in the attached image skype icon looks okay but evolution doesn't.

---

### Post by blazemore on 2010-05-01
You all misunderstand. Right-click a blank area in the top panel.
Select Properties
Select the Background tab
Select the radio button that says Solid colour
Drag the transparency slider left and right, and watch what happens to the panel.
Specifically, watch what happens to the panel applets, especially the menu (Applications, Places...)

---

### Post by Kirky_D on 2010-05-01
> **karmic-koala said:**
> Doesn't work for me either. Have you tried this :

[http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244](http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244)

I am a bit skeptic though.

This works

---

### Post by blazemore on 2010-05-01
> **Kirky_D said:**
> This works

No it doesn't. That is for FULL transparency regardless of what is set in the preferences. I just want the preferences to correctly set the transparency of the panel.

---

### Post by WorMzy on 2010-05-01
> **blazemore said:**
> You all misunderstand. Right-click a blank area in the top panel.
Select Properties
Select the Background tab
Select the radio button that says Solid colour
Drag the transparency slider left and right, and watch what happens to the panel.
Specifically, watch what happens to the panel applets, especially the menu (Applications, Places...)

I don't think I misunderstood. You have solid colour behind those applets, and you want them to not have this solid colour, but instead have the same level of transparency as the rest of the panel, right?

So, from this:
[IMG]http://www.ubuntu-pics.de/bild/55514/top_expanded_edge_panel_085_V0149T.png[/IMG]
To this:
[IMG]http://www.ubuntu-pics.de/bild/55515/top_expanded_edge_panel_086_GOm2cv.png[/IMG]

Right?

In which case, what I said earlier is the solution. Change your theme. In particular the controls.

I misunderstood what karmic-koala wanted, although this solution might work in that case too. I haven't tested it.

---

### Post by blazemore on 2010-05-01
And what if I wanted something in between those two images?
Your hack only works for a full background, or no background at all.

---

### Post by WorMzy on 2010-05-01
Did you try it?

With ~50% transparency:
[IMG]http://www.ubuntu-pics.de/bild/55520/top_expanded_edge_panel_087_jt00E7.png[/IMG]

Also works with transparent images:
[IMG]http://www.ubuntu-pics.de/bild/55521/top_expanded_edge_panel_088_57natB.png[/IMG]

---

### Post by Sir Digby on 2010-05-01
The solution posted earlier works for me, allowing the Panel Properties slider bar to correctly control the transparency of the whole panel.

---

### Post by stovicek on 2010-05-01
> **blazemore said:**
> And what if I wanted something in between those two images?
Your hack only works for a full background, or no background at all.

Well, to be specific, it's my hack. You'll still need to utilize it if you want to achieve the goal I think you're attempting to reach.

The Ambiance and Radiance themes use a background image for the panel. The problem lies with the icons which inherit the image but don't respect the panel's transparency setting.

If you use the "hack", it just removes the image being used. If you go to that panel's Properties > Background tab, selecting "None (use system theme)" will still give the panel a gray color. If you choose "Solid color" and click the "Color" button, you can then choose any of the millions of colors your screen can represent.

You can use the color dropper below the color wheel to select a color already on your screen, such as the gray that appears in the window borders. You can also enter that color's value in the "Color name:" entry box which happens to be #3C3B37 . Click OK and head back to the slider to set the transparency you desire.

The "hack" in question: [http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244](http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244)

---

### Post by aviramof on 2010-05-01
Change theme to clearlooks and that it.

[http://ubuntuforums.org/showthread.php?t=1457898](http://ubuntuforums.org/showthread.php?t=1457898)

---

### Post by ijustwantyourhalf on 2010-05-02
The answer is in the third post in this thread.

[http://ubuntuforums.org/showthread.php?p=9212797](http://ubuntuforums.org/showthread.php?p=9212797)

This makes the Ambiance theme panel work just like the old panel in the 9.04/9.10 default theme. After you alter the theme config you can adjust the transparency as normal from  "right click on panel > properties > background tab > solid color > etc."

-Don

---

### Post by 4hp007 on 2010-06-23
> **karmic-koala said:**
> Doesn't work for me either. Have you tried this :

[http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244](http://www.rebelzero.com/howto/full-transparent-panel-with-lucids-ambiance-radiance-themes/244)

I am a bit skeptic though.
Worked for me well thanks for sharing\\:D/

---

