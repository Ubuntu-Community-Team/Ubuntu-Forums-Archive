---
title: "how does ubuntu render font glyph?"
date: 2009-07-21
forum: General Help
---

### Post by webberhsu on 2009-07-21
Dear All,

I was developing  font engine.  I've ported most of the functions to Freetype.  Thus I package my own fontconfig-2.7.0 and Freetype-2.3.9.  After installed them to ubuntu, the ttf fonts were all displayed good, but my font.

I've ported my engine to Android b4, and everything goes well on the emulator.

I tried to print the log from the ubuntu, and found that normally when system ask to show a character, the system will call FT_Render_Glyph, but when the system ask to show my font, the system called FT_Load_Glyph first, then called FT_Render_Glyph.

Therefore I assumed that the cache system may cause the error, thus I re-checked the fontconfig.  But I found there is no error in fontconfig, I've already ported everything to it except Sfnt Table(which is true type font table)

Could anyone tell me where could the error happened and how could I solve it, please..

One Interesting thing:
I've tried to make my font engine always return bitmap only but outline.  Within some size(9,11,23...etc), my font can be displyed correctly.
I tried to reduce the size of my bitmap.  One amazing thing happened, my font can be displayed in every sizes, but I still don't know why...
It seems like that this could be one solution of my font engine, but it is not the solution I want.  I still want to use the autohint or other special transformation functions in Freetype...

Thnaks for reading this thread, and special thanks for the people who would help me

your sincerely
webber

---

