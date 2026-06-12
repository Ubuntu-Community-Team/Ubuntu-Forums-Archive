---
title: "Ubuntu and Kubuntu fonts are different?"
date: 2009-12-03
forum: General Help
---

### Post by queen3 on 2009-12-03
I've tried to install both Kubuntu and Ubuntu. I really, really like Ubuntu fonts. They're big and thick. I was fan of ClearType for a long time, mostly because it makes fonts thick... I always thought Linux fonts were not good (even once contacted freetype developers for tweaks to recompile it with hinting, etc). But Ubuntu 9.10 changed my mind.

I thought that Kubuntu would be the same, but with KDE. But I can't get fonts to look the same way as they do in Ubuntu! I tried to increase size, I set subpixel hinting with RGB mode, all the same as in Ubuntu. But I cannot get the same effect.

Am I missing something? How do I get Kubuntu fonts to look **exactly** the same as Ubuntu ones?

---

### Post by DodgeV83 on 2009-12-08
Everytime I try Kubuntu, the fonts always push me back to Ubuntu, even after installing "kubuntu-restricted-extras".  Has anyone figured this out?

---

### Post by Zorael on 2009-12-08
Could it be autohinting? It makes certain fonts (or perhaps any font when in bold) wide and blobby. KDE doesn't offer to enable this.
```
$ sudo ln -s /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/10-autohint.conf
```
That would enable it for all users. If you want to make it user-specific, add this tidbit to your **~/.fonts.conf** file.
```
[COLOR="Red"]<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>[/COLOR]

[b][COLOR="Green"] <match target="font">
  <edit mode="assign" name="autohint">
   <bool>true</bool>				<!-- autohinting -->
  </edit>
 </match>[/COLOR][/b]

[COLOR="red"]</fontconfig>[/COLOR]
```
Omit the parts in red if they already exist.

The changes should affect newly started applications. If you start them from a terminal, it will output errors if your .fonts.conf file has errors in it (with the line number where the error is), so that might be a good idea, to make sure it's set up properly.

---

### Post by queen3 on 2009-12-08
You forgot the matching tag at the end - oops, already fixed :).  Will try when I get a chance, but I doubt it is the reason.

---

### Post by queen3 on 2009-12-08
I tried this, it got better but still sucks. Letters are still a bit (hm, if that's a bit) blurry, and what's worse, some of that blurriness is colored, like if I selected BGR instead of RGB - but RGB is selected in both Settings and .fonts.conf. I even installed Liberation fonts (I use them in Ubuntu) but this didn't really improve much.

I've attached a sample of the text.
[ATTACH]139084[/ATTACH]
Not sure if this will look the same on another monitor, of course. For me the word Dolphin is clearly color-blurred.

What is VERY strange, if I set BGR mode in Settings/Fonts, the KDE menu **and** text in Konqueror text area gets non-color-blurred (though plain blurred) but app menus, and Konqeuror page fonts are color-blurred! When I set mode to RGB, Konqueror and menus are OK, but system menu is blurred like on attached picture. Seems like KDE applies different RGB/BGR modes to different widgets.  Now, on my workplace monitor color blur is not that heavy; but for example the capital M has different stems' thickness. This never happens in Ubuntu.

---

### Post by Lindsay.Mathieson on 2010-02-18
Shouldn't it be:

```

<match target="font">
  <edit mode="assign" name="autohint">
   **<bool>true</bool>**				<!-- autohinting -->
  </edit>
 </match>

```

---

### Post by Zorael on 2010-02-18
Doh, yes. Edited.

---

### Post by Lindsay.Mathieson on 2010-02-18
Thanks

---

### Post by hellslinger on 2012-07-11
I've been looking to the solution to this problem for years (no exaggeration). The answer was autohint! Thanks, everyone!

---

### Post by overdrank on 2012-07-11
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

