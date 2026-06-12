---
title: "find execdir convert -resize &quot;find: missing argument to `-execdir'&quot;"
date: 2010-02-02
forum: General Help
---

### Post by kiddykoff on 2010-02-02
ok, i'm trying to resize my album art that is dispersed through various artist/album folders. They are mostly 200x200, but i want to make all of them the same size. The code i'm trying to use is,

```
find -iname "cover.jpg" -execdir convert -resize 200x200 {}
```
or
```
find -iname "cover.jpg" -execdir convert {} -resize 200x200
```

i'm getting the error,
```
find: missing argument to `-execdir'
```
on both

can someone tell me whats wrong with my syntax. or am i doing something that's impossible?

---

### Post by geirha on 2010-02-02
You have to tell find where the command ends. You do that with a semicolon, which needs to be escaped from the shell (since ; has a special meaning in the shell). Newer implementations of find also provide a different end-character, +, which makes it pass as many files into one command as possible. In your case, since you want to resize the images in place, that's a wanted feature.

Please make sure to try this out on a test-tree first, and that you have a backup, because it will overwrite the original files, with no chance of recovery if it fails.
```
find . -iname "cover.jpg" -exec mogrify -resize 200x200 {} +
```

See [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind) for a guide on using find.

---

### Post by kiddykoff on 2010-02-03
oh, i see about the ; there. thanks! I don't recall seeing that in the manual, but that website cleared things up thanks.

and running the command in a test tree first is a good idea. thanks a lot!

---

