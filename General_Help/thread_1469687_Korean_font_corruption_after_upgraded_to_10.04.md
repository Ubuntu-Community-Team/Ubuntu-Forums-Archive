---
title: "Korean font corruption after upgraded to 10.04"
date: 2010-05-02
forum: General Help
---

### Post by keyser7777 on 2010-05-02
Hi,

After I've upgraded to 10.04, the Korean text has become unreadable or very hard to read, on both KDE/Qt and Gnome/GTK apps. The text appears thiner and some characters/symbols are not fully rendered.

Has anyone encountered the same issue?

Update: In Dolphin and Nautilus the text is not rendered clearly, in Konsole is displayed just fine.

---

### Post by davidge on 2010-05-08
I have the exact same problem. Not only in my default english locale. Even if i log in selecting the korean locale and language, fonts are unreadable in nautilus, gtk menus, etc.

There was a similar problem in 9.04 i think, that was fixed. But to see this again in a LTS release... *sigh*

---

### Post by Ginsu543 on 2010-05-08
I'm sorry to jack your thread but I was wondering what IM you are using to toggle between English and Korean. I have been using Nabi since 8.04, and 10.04 is the first time it doesn't work. Normally, Shift+space is the toggle key, but it just doesn't work for me. Do either of you have the same problem?

To comment on the text corruption issue, when I tried using IBus as the IM, I could toggle between English and Korean but the Korean text would come out incorrect. The word would look right just after typing it, but as soon as I hit ENTER, some of the characters would change. I have no clue why that's the case. This does seem like a regression since Korean worked flawlessly for me in 9.10.

---

### Post by davidge on 2010-05-08
Just the default ubuntu input method backend, Ibus.

Yes, text is also wrong when typing in Ibus, but it's a font problem i think. Web pages in Chrome or Firefox, gtk menus, etc, all display really shitty fonts. It happened in 9.04, and the quick fix was uninstalling a chinese font. After some ubuntu updates it got fixed.

By the way, font are not unreadable at all sizes. Bigger sizes are readable, but the default ones... That's why if you open a page from korean wikipedia, titles are ok, but the main text... hurts :(

What i cannot believe is that after one year, 10.04 has been published with, if not the same bug, another bug that causes the same problem. As you said, 9.10 was flawless.

---

### Post by davidge on 2010-05-08
By the way i see this message title has [kubuntu] in it, but this happens in gnome too. Please add another tag to make clear this is a general ubuntu problem.

---

### Post by Zorael on 2010-05-08
Is this only for upgraders?

Try uninstalling the **ttf-wqy-zenhei** font (as per [this thread](http://ubuntuforums.org/showthread.php?t=1317694)).
```
$ sudo aptitude purge ttf-wqy-zenhei
```

If that doesn't help, try renaming your **~/.fonts.conf** file and restart any applications that this happens in.

---

### Post by keyser7777 on 2010-05-12
> **Zorael said:**
> Is this only for upgraders?

Try uninstalling the **ttf-wqy-zenhei** font (as per [this thread](http://ubuntuforums.org/showthread.php?t=1317694)).
```
$ sudo aptitude purge ttf-wqy-zenhei
```

If that doesn't help, try renaming your **~/.fonts.conf** file and restart any applications that this happens in.

Uninstalling the font above solved my problem. The only side effect it is in Nautilus, where the Korean fonts isn't displayed anymore, only some rectangles. In Firefox everything looks fine, so this doesn't seems a general GTK problem.

I consider the issue solved.

Thanks Zorael

---

