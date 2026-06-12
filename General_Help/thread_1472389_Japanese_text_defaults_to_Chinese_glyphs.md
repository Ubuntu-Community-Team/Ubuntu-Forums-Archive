---
title: "Japanese text defaults to Chinese glyphs"
date: 2010-05-04
forum: General Help
---

### Post by mikekchar on 2010-05-04
Actually I want to log a bug but I don't really know what package to log it against.

The problem is that by default Pango is choosing the AR PL UMing CN as the font to render Japanese text when the current font doesn't have Japanese glyphs.  But AR PL UMing CN is a Chinese font, so Chinese glyphs for kanji characters (e.g., &#35226;) are displayed.  This is jarring and confusing for Japanese readers.

This situation mostly arises when you have mixed English and Japanese text.  Some applications (for instance Firefox) will allow you to select a font for Asian text.   Thus if the text contains only Asian characters it will use the font you select, rather than what Pango would have selected.  But if it is a mix of English and Japanese, you end up with the wrong glyphs.

Other environments (like gnome-terminal, or a gedit) have difficulties as well.  Since the primary interface requires mono spaced roman characters you run into difficulty selecting fonts.  Most Japanese fonts only have proportional roman characters.  This means that if use a nice roman font and use Japanese text (for instance file names), you end up with Chinese glyphs.

What I want is a mechanism that will work across all of Gnome for selecting the font I want to use for Chinese characters.  That way I can choose either Japanese or Chinese glyphs.

I realize this is low priority.  It only bugs me a little, but many of my Japanese colleagues are put off from using Ubuntu because they are confused by the Chinese glyphs that pop up on my screen from time to time.  As I said, I'd like to file a bug, but I'm not sure against what package...

Any help (or even a solution if there is one!) is appreciated.

---

### Post by zaphod777 on 2010-05-04
Have you installed the additional language in language support? I never have trouble with Japanese characters unless I am writing a web page and don't set the encoding properly. 

I am living in Japan too so I get a lot of Japanese characters.

---

### Post by mikekchar on 2010-05-12
Thanks for the reply.  I stupidly didn't subscribe to my own thread so I didn't notice it -- sorry!  Anyway, I do have the Japanese language pack installed, and quite a few Japanese fonts as well.  But after seeing your response I started playing around and I can be convinced that there is just something screwy on my box.

I will investigate some more and reply if I find something out.  Thanks again for your help!

Edit: I found the answer.  I was originally correct.  In web pages were the encoding is UTF-8, applications will chose the first font capable of displaying that character.  By default it goes in alphabetical order.  So if you have both Chinese and Japanese fonts installed, you might end up with glyphs yo don't want.  Without thinking about it I assumed all these fonts I installed were there by default.  But now that I reflect on it, it's not true.  I installed a lot of fonts because I needed to get glyphs for the bushu (and they only seem to exist in Chinese fonts).

Having said all that, you can select the order that applications will select the fonts by editing your ~/.fonts.conf file.  A good description of setting up Japanese fonts is detailed at the end of the first message in this thread: [http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552)  This solves my problem.

---

