---
title: "Restore Lucid Original Breadcrumbs?"
date: 2010-06-05
forum: General Help
---

### Post by yasasflash on 2010-06-05
[B][SIZE="3"]I've been misguided and played some bad game with the nautilus light themes.
Now i'm having a theme called "Eclipse" in nautilus.
but the breadcrumbs seems be not rendering perfectly.
they seems to be broken in the flow.
(i've attached the image)
[IMG]http://img17.imageshack.us/img17/8194/screenshotfub.png[/IMG]

Please tell me how to restore the original breadcrumbs in lucid.
what is the gtk engine i need to have?



[/SIZE][/B]

---

### Post by yasasflash on 2010-06-05
need a help guys.

---

### Post by yasasflash on 2010-06-05
any one? please just tell me the required gtk engine for the ambiance theme.

---

### Post by t.rei on 2010-06-05
Ok, so you installed the breadcrumbs thingy. You obviously did some of the many many ways to do so.

There is one, wich I use, because I like them and they render wonderfully in the theme (installed it so it is in every theme) I use is:

there is a .gtkrc-2.0 in my home folder. There is a line pointing to a nautilus.rc. Comment that by placing a # in front. Or delete it (the line). Reload theme by switching back and forth...

Another method would be that this nautilus.rc is somewhere within your currently used theme's folder and mentioned in the gtkrc therein. Same thing, comment or delete.

The other option is that the nautilus breadcrumbs conif is right within your theme. Thats nasty. I'd suggest using some other theme.

Also there is the possibility that you installed the nautilus version of the elementary project:
In that case you can turn off the breadcrumbs in the nautilus settings on the tweaks tab.

Cheers mate.

---

### Post by yasasflash on 2010-06-05
> **t.rei said:**
> Ok, so you installed the breadcrumbs thingy. You obviously did some of the many many ways to do so.

There is one, wich I use, because I like them and they render wonderfully in the theme (installed it so it is in every theme) I use is:

there is a .gtkrc-2.0 in my home folder. There is a line pointing to a nautilus.rc. Comment that by placing a # in front. Or delete it (the line). Reload theme by switching back and forth...

Another method would be that this nautilus.rc is somewhere within your currently used theme's folder and mentioned in the gtkrc therein. Same thing, comment or delete.

The other option is that the nautilus breadcrumbs conif is right within your theme. Thats nasty. I'd suggest using some other theme.

Also there is the possibility that you installed the nautilus version of the elementary project:
In that case you can turn off the breadcrumbs in the nautilus settings on the tweaks tab.

Cheers mate.

whoaaa you are my hero. :):guitar:
it worked like a charm mate.
thank you for million times.
what actually i've done was is in [http://www.webupd8.org/2010/05/install-updated-light-themes-version-in.html](http://www.webupd8.org/2010/05/install-updated-light-themes-version-in.html)
damn. that url.
as you said correctly i tried to install the development version of new ambiance theme. called "eclipse"
how ever it screwed up my breadcrumbs.
But i really do like the eclipse dark effect in the gtk theme.
i wish i can  install it without effecting the breadcrumbs :(
how ever thanks again bro.

---

### Post by t.rei on 2010-06-07
actually I can find no trace within the Equinox theme of it changing the way the PathBar (the breadcrumbs thingy) is drawn. 

Actually thanks for the link - I love that theme and adapted it to the mixture of edited stuff I use. "I am the borg of themes" :P

For me there is no weird spacing like in yours, see:
[[IMG]http://img199.imageshack.us/img199/3167/examplefn.th.png[/IMG]]("http://img199.imageshack.us/img199/3167/examplefn.png")

I have them enabled for all my themes by having a line in my .gtkrc-2.0 in my home dir that includes a nautilus.rc to add them:
```
cat .gtkrc-2.0
include ".themes/nautilus/nautilus.rc"

```


if I comment that line like this:
```
#include ".themes/nautilus/nautilus.rc"
```
the equinox theme uses the default breadcrumbs like it should.

there is no reason why the equinox theme should not work like you want it to. :)

---

### Post by tad1073 on 2010-06-07
or you could use gconf-editor

alt+f2>apps>nautilus>preferences>Always_Show_Location_Entry

---

### Post by t.rei on 2010-06-07
actually thats something entirely different than what I understood he wanted.

Always show location entry will change from clickable 'breadcrumbs' alltogether to the text-entry-field. 

However that not quite what I thought this was about (purely a matter of design).

---

### Post by tad1073 on 2010-06-08
> **t.rei said:**
> actually thats something entirely different than what I understood he wanted.

Always show location entry will change from clickable 'breadcrumbs' alltogether to the text-entry-field. 

However that not quite what I thought this was about (purely a matter of design).

I realized that after I posted my comment.

---

