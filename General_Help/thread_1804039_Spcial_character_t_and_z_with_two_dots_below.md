---
title: "Spcial character t and z with two dots below"
date: 2011-07-14
forum: General Help
---

### Post by jesuisbenjamin on 2011-07-14
Hello,

I'm looking for a way to write a diacritic, namely two dots below a letter (with special regard to t and z), which is commonly used for transcription of Arabo-Persian scripts. I just can't find them in the special character table. Do you have any idea how i can find them? With all the mad characters available, i'm almost surprised if these weren't included.

Thanks.

---

### Post by dino99 on 2011-07-14
do you have the hex code ?
[http://superuser.com/questions/59418/how-to-type-special-characters-in-linux](http://superuser.com/questions/59418/how-to-type-special-characters-in-linux)


Maybe Gentium:
[http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium)

[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

---

### Post by jesuisbenjamin on 2011-07-14
nope, i can't see it in the character map, imo it should be among Latin extensions.

---

### Post by Vaphell on 2011-07-14
z&#804; = z, ctrl+shift+u, 0324
t&#804; = t, ctrl+shift+u, 0324

it appears that there are no standalone glyphs, you use base char and that u0324 double dot modifier (COMBINING DIAERESIS BELOW)

---

### Post by jesuisbenjamin on 2011-07-14
Thanks. May I ask where you found this info?
Also: any idea as to who's taking care of this stuff? i.e. where can i report these "missing" characters?

---

### Post by Vaphell on 2011-07-14
1. i went to wikipedia for 'arabo-persian' and copied z with dots
2. i scratched head looking at char table as there was no such thing despite the evidence of seeing that char with my own eyes
3. i pasted it into text file and opened the file in mcedit to investigate character number - to my surprise it showed that character as a construct of 2 separate glyphs taking up 3 spaces
```
[z][ &#804; ]
``` z had normal ascii code, double dots with the space showed some oddball 800-something code (decimal). I looked a bit for some low placed dots in char map, found them at u0324.
4. tried z, ctrl+shift+u, 0324 and it worked :)

it appears that it's a modifier that can be used on pretty much any character. It makes cursor go back 1 char and then puts double dot so it overlaps with the previous symbol.

---

### Post by SoFl W on 2011-07-14
Try the compose key and check out the [Compose Table]("https://help.ubuntu.com/community/GtkComposeTable").

---

