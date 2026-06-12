---
title: "Some font problems, trying to understand"
date: 2009-09-27
forum: General Help
---

### Post by davygrvy on 2009-09-27
Just went though SPM and installed every font listed including the MS webfont package.  I also installed pIqaD.ttf (a unicode klingon font) by dropping it in /usr/shared/fonts/truetype/ and running fc-cache.

Now here is where it gets odd.

The Klingon font uses the private use area F8D0-F8FF ([http://www.evertype.com/standards/csur/klingon.html](http://www.evertype.com/standards/csur/klingon.html)) The range isn't exactly a "standard", but is the accepted one until the Unicode folks get their chicken/egg problem fixed.

Now how do I force the OS to use this font's glyphs for that range exclusively?  Firefox still won't show Klingon web site correctly ([http://www.wazu.jp/gallery/Test_Klingon.html](http://www.wazu.jp/gallery/Test_Klingon.html)).  Also, the wrong glyphs are being referenced, but can't tell what font is offering them as default.

Ok, that's one problem.  The second is related to this: [http://www.alanwood.net/unicode/latin_1_supplement.html](http://www.alanwood.net/unicode/latin_1_supplement.html)

As far as I know from reading the unicode specs, there are NO GLYPHS DEFINED FOR THE RANGE x80-x9F, yet this site gives them names and glyphs are displayed.  I know why they are being displayed..  The well known Firefox bug that remaps cp1252 characters for that range.  I have looked, but there is no option to enable strict iso8859-1 operation.  Guess I'm going to have to hack the FF source and fix it myself?  It would have been nice of the author of that site to NOT give those characters names that don't fit the standard as written.

Will the remapping of cp1252 characters into x80-x9F ever go away?

Is it possible for me to force the OS to not display any characters in x80-x9F range?

---

