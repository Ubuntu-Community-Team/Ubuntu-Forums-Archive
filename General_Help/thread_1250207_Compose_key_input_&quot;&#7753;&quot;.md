---
title: "Compose key input &quot;&#7753;&quot;"
date: 2009-08-26
forum: General Help
---

### Post by chrismiceli on 2009-08-26
Hi,
I am trying to input the letter "&#7753;".  However, I am unsure how.  I use the compose key for many letters.  In /usr/share/X11/locale/en_US.UTF-8/Compose it says that the key combination is 
<dead_belowmacron> <n> : "&#7753;"   U1E49 # LATIN SMALL LETTER N WITH LINE BELOW

However, I don't know what the dead_belowmacron key is.  Could anyone help me?

Thanks.

---

### Post by CatKiller on 2009-08-26
There is a way to input Unicode characters directly, if you know their numbers. So, in this case, you could use <Ctrl><Shift><u> and type 1e49<space> to get &#7753;.

---

### Post by chrismiceli on 2009-08-26
Yeah, I know this one; however, like the Compose key for é is <Multi-key> <apostrophe> <e>.  I can create my own I suppose.  Something like <Multi-key> <underscore> <n> for which there is no combination.

---

### Post by chrismiceli on 2009-08-26
Ok this didn't work.  Where does Ubuntu look for its compose key information?  It isn't in /usr/share/X11/locale/...

---

### Post by CatKiller on 2009-08-26
> **chrismiceli said:**
>  Where does Ubuntu look for its compose key information?  It isn't in /usr/share/X11/locale/...

Don't forget that you need to restart X for your changes to take effect.

According to [this page]("http://blog.cyberborean.org/2008/01/06/compose-key-magic"), you can create per-user Compose sequences by putting your table in a ~/.Xcompose file. Also according to that page, there's a [problem]("http://bugzilla.gnome.org/show_bug.cgi?id=321896") with using custom sequences in GTK apps. I have no idea if that's been fixed since the page was written, or if you need to do the fix suggested in the comments.

---

### Post by chrismiceli on 2009-08-28
I created a .XCompose file and it was ignored.  Also, I did restart X.  I'm not sure if anyone can recreate this problem though.

---

