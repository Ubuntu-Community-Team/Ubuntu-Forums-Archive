---
title: "Compiling Mplayer, error"
date: 2006-04-03
forum: General Help
---

### Post by Strike&gt;&gt; on 2006-04-03
Hello

After reading that building mplayer from source is better than getting it from ap, i gave it a try to see for myself. 

./configure --enable-gui    worked and make install went fine but i got a few errors. The problem is that when i run it, the program pops, but the disappears right away.:confused: 

If not fixable, how can i remove it so i can try another method.
Thank you

---

### Post by taurus on 2006-04-03
Have you at least tried to run it from a terminal so you can see what's the problem is???  Otherwise, just pops and disappears are not really helping at all...  And if you want to remove it, just do (from the same directory where you built it)
```

sudo make uninstall

```

---

### Post by Strike&gt;&gt; on 2006-04-03
Sorry, the pop was an error.  I did run it in terminal, and it worked.

---

### Post by taurus on 2006-04-03
[QUOTE=Strike>>]Sorry, the pop was an error.  I did run it in terminal, and it worked.[/QUOTE]
So now mplayer works!!!

---

### Post by Strike&gt;&gt; on 2006-04-03
Lol jks :D 

And even when i try to open a movie with it, still gives me an error!!

---

### Post by taurus on 2006-04-03
Would you mind sharing the error message so people know exactly what's wrong with it???  :rolleyes:

---

### Post by Strike&gt;&gt; on 2006-04-03
hahaha, i said that the error just appears and dissapears fast,and has no text, so i can't read it. the only thing that i can read is the title, which says error.

---

### Post by taurus on 2006-04-03
Even running it from a terminal!!!  Applications -> Accessories -> Terminal.  Then at the prompt, type
```

mplayer
-or-
gmplayer

```

---

### Post by Strike&gt;&gt; on 2006-04-03
it does run in the terminal but i didn't open a movie via the terminal, and i think it's too late becasue i uinstalled it after you told me how to. 

And thanks for the replies:)

---

### Post by taurus on 2006-04-03
In case you need to know for later.  You can mplayer a movie from a terminal too...
```

gmplayer movie.avi

```

---

### Post by Strike&gt;&gt; on 2006-04-03
I read this forum , that mentioned cvs, are the fonts and skins included or do i have to get them separately?
Thnks

---

### Post by taurus on 2006-04-03
If you download the source for mplayer, I don't believe it comes with skins, fonts, and codecs so you need to install them seperately.  You can get everything from here, [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html).

---

