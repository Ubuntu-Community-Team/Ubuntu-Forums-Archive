---
title: "Odd default fonts in OOo"
date: 2009-12-07
forum: General Help
---

### Post by ricardisimo on 2009-12-07
I recently tried moving all of the fonts in my /home/ricardisimo/.fonts folder to /usr/share/fonts/Custom instead. There were some problems with fonts displaying (or not) in Firefox, so i moved them all back. However, now I have a curious issue where the default fonts in OpenOffice are now "savatage" (for the serif font) and "Year 2000" (for the sans, or title font). These are weird fonts that I never even noticed, much less used in OpenOffice, and certainly would never have them as the defaults.

Changing the default fonts in Writer is easy enough, but Calc is proving to be more troublesome. How do I change the default fonts in all other components of OOo besides Writer? Thanks.

---

### Post by ricardisimo on 2009-12-08
I think I've figured it out: In Calc, select Format >> Styles and Formatting F11 >> right click on "default" and select Modify... (and similarly edit "Heading", "Result", etc. if need be.)

One problem, though... instead of "Normal", freesans font has "oby&#269;ejné" as the primary option. Why? What language is this, and will it ever affect what I want to do with Calc? Is there a US English version of freefont?

Thanks again for any help.

---

### Post by ricardisimo on 2010-03-22
So much for that being fixed. I've changed the default font repeatedly in the OpenOffice formatting window, as described above. But the next time I open a blank spreadsheet, "Year 2000" is once again the default font.

I've been trying to use freesans as the default, but I'm going to try arial instead. Still, why the hell can't I use whatever font I want as the default? Has anyone else experienced this?

---

### Post by ricardisimo on 2010-08-19
Nothing has changed, and I cannot figure out how to file a bug with anyone. Launchpad doesn't take OOo bugs, and OOo... I have no clue.

No one else has this problem? Can someone at least walk me through how to file the bug? Thanks.

---

### Post by ricardisimo on 2010-08-23
No one? How about this: Which folder dictates font and other settings to OOo? I'll delete it and have it reinstall itself, see if that works. Or I'll just do a complete reinstall of OOo.

---

### Post by ricardisimo on 2010-10-13
I think it's not OOo but system-wide. That same Year 2000 font is also appearing onscreen in Firefox wherever a fixed-width font is called for. I don't get it, though... not only is it not a fixed-width font (at least as far as I can tell) but it's an ugly font which I've never selected for any purposes, let alone system-wide ones.

Any clues where I would start? My suspicion is that if I just remove the font, yet another bizarre font will replace it, so I'd prefer getting to the root of the matter instead. Thanks.

---

### Post by ricardisimo on 2011-04-16
Nothing has been figured out, and the problem is still there. What's worse is that I need to change the fonts to whatever I want every single time I copy and paste into an OOo document. So, I'll have a spreadsheet, for example, which I've set up properly with arial or linux libertine or whatever font I like, but then everything I paste into any cell shows up in savatage or Brady Bunch or some other decorative font.

Weird. No one else has any similar issues?

---

### Post by Iehova on 2011-04-17
Hi ricardisimo,

Has literally no-one replied to this thread since 2009?

My goodness. What do you see in the "Font" tab when you go to the appearance preferences (in Maverick I believe it is system > preferences > appearance)? That lets you set all of the default fonts. Perhaps your Year 2000 font is set there?

I know that's probably the first thing you tried, but I figure you at least deserve a response from someone. :P

---

### Post by grahammechanical on 2011-04-17
Have you tried Tools>Options>Fonts. I do not know if this will work. I have never had to use this function.

By the way "oby&#269;ejné" sounds like it would be a Russian word but with English characters to help pronunciation.

Regards.

---

### Post by Iehova on 2011-04-17
> **grahammechanical said:**
> Have you tried Tools>Options>Fonts. I do not know if this will work. I have never had to use this function.

By the way "oby&#269;ejné" sounds like it would be a Russian word but with English characters to help pronunciation.

Regards.

I suggest it's more likely to be another slavic language that uses latin characters. Not Croatian, because that doesn't have the letter 'é', but maybe slovenian or something?

---

### Post by tredegar on 2011-04-17
If you have been moving fonts around or installing them manually, it is a good idea to update the font cache with **sudo fc-cache -fv** You don't say if you have done this, so perhaps this will help.

---

### Post by ricardisimo on 2011-04-19
Oh my goodness! I almost stopped checking these posts, since I haven't receive many if any replies in ubuntuforums in years. Thank you all for posting. I believe that oby&#269;ejné is Czech, and I would have to assume that the developer of the font in question is/was Czech.

My default system fonts are all either "ubuntu", "sans" or "monospace". These last two are not actual fonts, if I'm not mistaken, but rather pointers. That might actually be a good place to start, is selecting some definite sans-serif font to replace the generic "sans".

tredegar: Thank you. I will try that command right now. I used a utility called [Merlin]("http://blog.coursevector.com/merlin") to rename and organize all of the 1000s of fonts in my .fonts folder. Not sure if that could be part of the problem or not. Does your command affect the system-wide fonts, or my personal ones?

Edit: It does all of my fonts, as it turns out.

---

### Post by ricardisimo on 2011-04-19
grahammechanical: I didn't respond to you at first, because I had already changed the basic fonts in Writer a long time ago, and since a) the problem came back, and b) the problem exists in Calc as well, I figured it didn't work. However, when I looked just now, indeed those very same odd fonts were selected as the defaults for Writer. Let's see if it works and sticks this time. Thanks again to everyone.

---

### Post by ricardisimo on 2011-04-20
Oh, well... so I tried all of the above, and although Writer is now behaving itself, Calc is not. "Brady Bunch" is the default spreadsheet font. You can imagine just how professional that looks. Any other ideas?

---

### Post by simptechmike on 2011-05-12
> **ricardisimo said:**
> Oh, well... so I tried all of the above, and although Writer is now behaving itself, Calc is not. "Brady Bunch" is the default spreadsheet font. You can imagine just how professional that looks. Any other ideas?

I have just the solution you are looking for. I was frustrated myself with the Brady Bunch font issue but discovered how to use whatever font you want.

I put up the tutorial with step by step directions over on my Desktop Publishing site, complete with a free download of the tutorial in OpenOffice format.

[Set Default Font in Calc]("http://manndtp.com/help-center/resources/computer-education/ooo-calc/default-font.php")

Enjoy and shoot me any questions you might have. Hope this helps you!

---

