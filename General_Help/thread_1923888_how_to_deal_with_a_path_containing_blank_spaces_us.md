---
title: "how to deal with a path containing blank spaces using unoconv from command line in ba"
date: 2012-02-11
forum: General Help
---

### Post by Luca Borrione on 2012-02-11
On lubuntu Oneiric I'm using unoconv (0.4-1) to convert file from odt to pdf.
If the filepath doesn't contain blank spaces like

```
unoconv -f pdf /media/data/test/file.odt
```

everything works great.
But if I need to apply this command on a file with blank spaces on its path like

```
unoconv -f pdf "/media/data/test (0)/file.odt"
```

then on my system the command hangs with no result.
I tried with single quote too, with the same result.
Using quotes around the filepath param on my first example guides to the same result.
I searched the manual but there's no flag available to specify the input file.

So how can I specify a path with blank spaces to unoconv?

If there's no way to use unoconv on a filepath containing blank spaces, then is there any other alternative command which easily accept paths with blank spaces I can use?

---

### Post by duanedesign on 2012-02-11
Try  bash's escape character \

```
unoconv -f pdf /media/data/test\ (0)/file.odt
```

---

### Post by Cheesemill on 2012-02-11
You need to use a \ (also known as an escape character) in front of any special characters (spaces, for example).

For instance if you need to type the path:
```
/path/with a/space
```You would actually type:
```
/path/with\ a/space
```Another method is to surround the entire path with single quotes (strong quoting):
```
'/path/with a/space'
```Or with double quotes (weak quoting) as you have done:
```
"/path/with a/space"
```

I have no idea why this isn't working for you, it's part of the bash specification.

For the differences between single character, strong, and weak escaping take a look here:
[http://wiki.bash-hackers.org/syntax/quoting](http://wiki.bash-hackers.org/syntax/quoting)

However, I find that the easiest way is to use tab completion. For example typing:
```
/path/w
```and then hitting the tab key will complete the path for you.

---

### Post by Luca Borrione on 2012-02-11
Hi guys and thank you both for taking the time to help me.
In the meanwhile I noticed I couldn't open libreoffice writer at all through its link on the start menu. Clicking on it simply produced nothing.

So I started thinking the maybe something in libreoffice was wrong, as unoconv depends from it. Using top I haven't noticed anything suspicious so I decided to try rebooting.

On a new session everything worked as expected so both
```
unoconv -f pdf /media/data/test\ \(0\)/file.odt
unoconv -f pdf '/media/data/test (0)/file.odt'
```

worked great producing me the pdf file quickly and without any error.
I really don't know why the described behaviour was noticed,
maybe I gave too many wrong commands which might have freezed something.

Thank you Cheesemill for the link I'll take a deep look at it.

---

### Post by Rebelli0us on 2012-02-11
The parentheses require escape character too

\(0\)

Linux command line is ugly

---

