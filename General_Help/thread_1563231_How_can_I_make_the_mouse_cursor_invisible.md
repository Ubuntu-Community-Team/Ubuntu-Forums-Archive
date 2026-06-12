---
title: "How can I make the mouse cursor invisible?"
date: 2010-08-28
forum: General Help
---

### Post by superppl on 2010-08-28
So, here's the story. I installed Fallout 3 using PlayOnLinux, and it works fine, except that the mouse cursor is always visible. I thought I found a solution using unclutter, but the cursor reappears when I click, which kinda defeats the solution.

I found [this blog post](http://linux.byexamples.com/archives/253/something-for-my-mouse-cursor/), which almost completely useless to me except for the bottom two lines.
> OMG! my cursor becomes ugly default X windows cursor. Don’t worry, reset it to default by running the line bellow:
```

xsetroot -cursor_name top_left_arrow

```
or this
```

xsetroot -cursor_name left_ptr

```



This makes me wonder if I can't change the cursor theme via console. In that case, I can adjust the PlayOnLinux script to change the cursor theme to an invisible one as the game starts, and change it back to default when I exit the game (which is actually what I'm trying with unclutter right now).

There are a few problems with this: I don't have an invisible cursor theme or know how to make one, I don't know the name of the cursor theme I usually use, and I generally don't know anything about cursor themes.

So in short, what I'm looking for a is a method to temporarily make the mouse cursor invisible, preferably something that can be invoked through command line since I need to edit the PlayOnLinux script to make this work.

I'm running Kubuntu 10.04, KDE 4, and I don't see how my system specs are in anyway relevant.

---

### Post by Smart Viking on 2010-08-28
Just an idea but, does the mouse theme contain pure images, like some code and some images? 

Because then you could simply create a transparent image, and use the mv command to move between the real image and the transparent image. Good luck! :)

---

### Post by superppl on 2010-08-28
I found all the cursor themes under .icons, and using [http://www.ehow.com/how_5026012_make-cursors-file-ubuntu.html](http://www.ehow.com/how_5026012_make-cursors-file-ubuntu.html) , I managed to make invisible cursor. Your idea does work, however only on theme change.

Which leads to another idea: how can I change the KDE cursor theme via command line?

---

### Post by Smart Viking on 2010-08-28
> **superppl said:**
> I found all the cursor themes under .icons, and using [http://www.ehow.com/how_5026012_make-cursors-file-ubuntu.html](http://www.ehow.com/how_5026012_make-cursors-file-ubuntu.html) , I managed to make invisible cursor. Your idea does work, however only on theme change.

Which leads to another idea: how can I change the KDE cursor theme via command line?

That means you made a new cursor, ie a new "theme"?, if you name it as the same name as the theme you are currently using(replacing it) will the change take effect instantly?(take backup of the original file before trying). If it does, then you could simply do something like this, you make copies of both the original, and the transparent, then like of the original is "the.cursor", the copy of the original is "1.cursor" and the transparent is "2.cursor", then you could
```
cp 2.cursor the.cursor
```to make the cursor tranparent, and
```
cp 1.cursor the.cursor
```to make it back to normal. However i have no idea if this will work, worth a try though imo. :)
Edit: If you wanna put them in a script youre better of using full path's, you probably know that but i'll just say it anyway. :)

---

### Post by superppl on 2010-08-28
I didn't create a new theme, I simply created a new cursor.
The cursor theme I'm using (or have been for the last ten minutes :P) is called ComixCursors-Opaque-Green-Small, and it's found under /home/<user>/.icons/ComixCursors-Opaque-Green-Small/cursors/.
The name for the default cursor is conveniently named default, and the cursor I made is called blank. I made a copy of default, and called it defaultbak.

[[IMG]http://img836.imageshack.us/img836/6054/snapshotx.png[/IMG]](http://img836.imageshack.us/i/snapshotx.png/)

So I've tried your idea, i.e. "cp blank default" , and that does change the cursor, but not instantaneously. In fact, the change doesn't take effect until I change to another cursor theme, and change back to the intended cursor theme.

That's why I'm curious if I can change or refresh the current cursor theme via command line.

---

### Post by superppl on 2010-08-29
I am an idiot..........
My advisor at school tells me engineers usually have two problems when tackling problems: either they have too little imagination, or too much. Far too much imagination.

I'm certain this is one of those scenarios. I woke up this morning thinking I really wanna play Fallout 3. It suddenly occurs to me that this is a wine problem. I switch Fallout 3 from 1.1.44 (which PoL defaults it too) to 1.2.0, and there problem solved.

---

