---
title: "changing default japanese font"
date: 2009-08-19
forum: General Help
---

### Post by nkobel003 on 2009-08-19
I've followed a few tutorials on how to make MS Mincho/Gothic the default font when viewing and typing in Japanese, but I want to change that to another external font. The font is called [AquaBlue]("http://www.geocities.jp/teardrops_in_aquablue/fnt/aquap2_5.zip"), and it's already installed (although it only works in romaji and not kana/kanji in say openoffice.org).

Can anyone show me how to make AquaBlue the default font in everything that is Japanese? Mozilla, scim, text editor, openoffice, etc. Thank you!

---

### Post by Anuovis on 2009-12-08
If you followed the tutorial about creating a fonts.conf file, I think it is enough to put the desired font higher on that list. I know it worked in Open Office for me. Thunderbird keeps using his own default font, so it might be application-specific in some cases. Firefox also has font preferences that can be different from system defaults.

I followed _**[this thread]("http://ubuntuforums.org/showthread.php?t=812552")**_. Look under [I][B]Rebuilding the font cache.

[/B][/I]

---

### Post by Zorael on 2009-12-08
As described in that thread, you can define what font orders comprise the virtual fonts Serif, Sans-serif and Monospace. 

Whenever a character is to be displayed using that virtual font, it will first try to display it with the first font in its list. If that font doesn't contain that character, it will try the next, then the next, and so forth.

Basically every unicode font have roman characters, but they're not always very pleasant to the eye, so a common approach is to put a "good" roman font up top (Times New Roman, DejaVu family, Arial, etc), and then one or more good unicode fonts afterwards. If the roman font doesn't contain the character that is to be displayed - in this case, a Japanese kana or kanji - it'll display it in your unicode font. So that's what you want to set to AquaBlue.
```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <alias>
  <family>serif</family>
  <prefer>
   <family>Times New Roman</family>
   <family>[COLOR="RoyalBlue"]AquaBlue[/COLOR]</family>
  </prefer>
 </alias>
 <alias>
  <family>sans-serif</family>
  <prefer>
   <family>DejaVu Sans</family>
   <family>[COLOR="RoyalBlue"]AquaBlue[/COLOR]</family>
  </prefer>
 </alias>
 <alias>
  <family>monospace</family>
  <prefer>
   <family>DejaVu Sans Mono</family>
   <family>[COLOR="RoyalBlue"]AquaBlue[/COLOR]</family>
  </prefer>
 </alias>
</fontconfig>
```
Obviously, this only works if applications are set up to use the virtual Serif, Sans-serif and Monospace fonts. So you would have to tell Firefox et al to use those instead of directly using a "real" font.

---------

Additionally, you can set up per-font fallbacks. If you have an application that will display something in DejaVu Sans no matter what you do, you can just define a good unicode fallback for that font directly.
```
 <alias>
  <family>DejaVu Sans</family>
  <prefer>
   <family>DejaVu Sans</family>
   <family>Kochi Gothic</family>
  </prefer>
 </alias>
```
New in Karmic is that per-font fallbacks like this seems to be included in the virtual font definitions. So if you have a virtual font defined to have a font order of ([COLOR="SeaGreen"]Font A[/COLOR], [COLOR="DarkOrange"]Font B[/COLOR]) - and then you define a font fallback for [COLOR="SeaGreen"]Font A[/COLOR] as ([COLOR="SeaGreen"]Font A[/COLOR], [COLOR="RoyalBlue"]Font C[/COLOR]) - the true font order for the virtual font will be (([COLOR="SeaGreen"]Font A[/COLOR], [COLOR="RoyalBlue"]Font C[/COLOR]), [COLOR="DarkOrange"]Font B[/COLOR]).

You can likewise make complete font replacements; such as to make all calls for DejaVu Serif end up with Times New Roman, instead. I replace a few fonts to make web pages render nicer.
```
 <!-- FONT REPLACEMENT
	Some fonts look positively ugly so changing them to the virtual sans-serif, sans and monospace
    -->

 <!-- serif -->

 <match target="pattern">
  <test name="family" qual="any">
   <string>Times</string>
  </test>
  <edit mode="assign" name="family">
   <string>serif</string>
  </edit>
 </match>
 <match target="pattern">
  <test name="family" qual="any">
   <string>Nimbus Roman No9 L</string>
  </test>
  <edit mode="assign" name="family">
   <string>serif</string>
  </edit>
 </match>

 <!-- sans-serif -->

 <match target="pattern">
  <test name="family" qual="any">
   <string>Bitstream Vera</string>
  </test>
  <edit mode="assign" name="family">
   <string>sans-serif</string>
  </edit>
 </match>
 <match target="pattern">
  <test name="family" qual="any">
   <string>Bitstream Vera Sans</string>
  </test>
  <edit mode="assign" name="family">
   <string>sans-serif</string>
  </edit>
 </match>
 <match target="pattern">
  <test name="family" qual="any">
   <string>Helvetica</string>
  </test>
  <edit mode="assign" name="family">
   <string>sans-serif</string>
  </edit>
 </match>
 <match target="pattern">
  <test name="family" qual="any">
   <string>Nimbus Sans L</string>
  </test>
  <edit mode="assign" name="family">
   <string>sans-serif</string>
  </edit>
 </match>

 <!-- monospace -->

 <match target="pattern">
  <test name="family" qual="any">
   <string>Bitstream Vera Sans Mono</string>
  </test>
  <edit mode="assign" name="family">
   <string>monospace</string>
  </edit>
 </match>
 <match target="pattern">
  <test name="family" qual="any">
   <string>Courier</string>
  </test>
  <edit mode="assign" name="family">
   <string>monospace</string>
  </edit>
 </match>
 <match target="pattern">
  <test name="family" qual="any">
   <string>Nimbus Mono L</string>
  </test>
  <edit mode="assign" name="family">
   <string>monospace</string>
  </edit>
 </match>
```
There's likely a way of nesting those replacements to fewer lines.

I'll attach my ~/.fonts.conf, might give you some examples to work with.

---

