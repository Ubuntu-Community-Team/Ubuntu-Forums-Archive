---
title: "Gedit/text editor -- faded font?"
date: 2012-09-04
forum: General Help
---

### Post by yossell on 2012-09-04
I like working in gedit, especially now that the latex plugins seem to be working with gedit3. However, all the fonts in gedit seem to be slightly greyed out, as if it's not displaying text in true black. Compared to a pdf printout, the greyness is quite noticeable. I prefer my text like my coffee -- black. 

It seems to be slightly less bad in other text editors, such as leafpad. I'm mucked around with anti-alias settings and hinting, but that doesn't seem to be the issue.

Does anybody else have this issue? Does anybody else have this problem? It only started when I upgraded to 12.04. I'm wondering whether it's partly a ubuntu/gnome issue. Ubuntu tends to make use of slightly greyed out fonts as a kind of design issue, and I wonder if gedit is somehow using Ubuntu's `global' settings here. 

Any suggestions or thought gratefully received. Thanks in advance.

---

### Post by yossell on 2012-09-10
If anyone is interested, it had something to do with the gtk theme that unity uses. Using gnome-tweak, going to theme and setting gtk+ theme to adwaita solved it. I couldn't find a way of editing the font colours in the radiance theme itself though.

---

### Post by vasa1 on 2012-09-10
> **yossell said:**
> If anyone is interested, it had something to do with the gtk theme that unity uses. Using gnome-tweak, going to theme and setting gtk+ theme to adwaita solved it. I couldn't find a way of editing the font colours in the radiance theme itself though.
I haven't encountered this problem at all maybe because of the theme I choose from within gedit itself (Edit, Preferences, Fonts and Colors). There are five themes to choose from.

---

### Post by yossell on 2012-09-11
Interesting -- on my two systems, it's certainly the gtk+ theme which is making the difference. Whatever `black on white' theme in gedit I choose - classic, kate or tango, the weight of the fonts shown in gedit is a function of the gtk+ theme I choose. For me, the faint fonts are most noticeable with the radiance theme. 

I'm on gedit 3.4.1, if that makes a difference.

I guess the classic theme of gedit simply borrows its black from the gtk+ theme. I wonder if it's possible to edit the theme in gedit so that it shows true black...not sure which file to attack though, I'll have a dig around.

---

### Post by yossell on 2012-09-11
To change the font colours of gedit 3 without changing the unity theme, I edited the style xml. 

starting gedit as root, I opened the document classic.xml located in /usr/share/gtksourceview-3.0/styles

Then I put the following just before pallette. 

  <!-- Global Settings -->
  <style name="text"                        foreground="#black" background="#white"/>
  <style name="selection"                   foreground="#white" background="#black"/>
  <style name="cursor"                      foreground="#black"/>
  <style name="current-line"                background="#grey"/>
  <style name="line-numbers"                foreground="#grey" background="#white"/>
  <style name="draw-spaces"                 foreground="#grey"/>

Then I closed gedit. On restart of gedit, black fonts on white background. 

As written, this colour scheme is a little brutal. It can be finessed by adding more subtle colours to the palette, rewriting the above, and then pasting choice of colours below the palette. 

I found that putting these global settings below palette caused gedit to start with error messages, although it displayed everything just as well.

---

### Post by Walter Tross on 2012-11-01
Yes, it is truly annoying that there is no scheme editor in gedit (at least in 3.4.1), and that in the few available ALMOST black-on-white color schemes the "black" depends on the Unity theme. With the Ambiance theme this means that the text foreground color in gedit is #4C4C4C, i.e., 30% of red, green and blue (looks like less because of the gamma, but is still far from true black).

I used your solution yossell, and it worked, thank you!

To do it in a somewhat cleaner way, I copied /usr/share/gtksourceview-3.0/styles/classic.xml to ~/.local/share/gtksourceview-3.0/styles/classic-BW.xml (creating the directories that didn't exist - and BTW, ~ means one's home directory, for those who don't know). Then I added in your <style> tags, following your advice about their position, but I also changed the <style-scheme> tag setting the id to classicbw and the _name to Classic-BW (and I also changed the <author> and <description> tags, but this is less important). This way, when you reopen gedit, Classic-BW appears as a new color scheme right after Classic.

I also tried to leave only the first of your <style> tags, hoping to keep, e.g., the white-on-orange selection, but that didn't work. If one has enough time, it might be worthwhile to study a bit. Here are a few links: [http://askubuntu.com/questions/41101/can-i-change-gedits-background-color-without-changing-to-another-theme](http://askubuntu.com/questions/41101/can-i-change-gedits-background-color-without-changing-to-another-theme) (but replace gtksourceview-2.0 with gtksourceview-3.0).

---

