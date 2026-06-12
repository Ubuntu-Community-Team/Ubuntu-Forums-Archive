---
title: "Can't find a file manager that sorts hex-numbered files"
date: 2011-02-05
forum: General Help
---

### Post by R2D2! on 2011-02-05
I have some files, named E000.svg, E001.svg, E002.svg, ... E07D.svg, E07E.svg, E07F.svg . When I open them in Nautilus, and choose the option Sort Alphabetically, they are sorted:

E000.svg
E00A.svg
E00B.svg
E00C.svg
E00D.svg
E00E.svg
E00F.svg
E001.svg
E01A.svg
E01B.svg

and so on. This is totally useless for me, so I searched for a solution in Google, and found lots of bug reports. It looks like it's a “feature” for sorting 10 after 9; but clearly they have forgotten that many people don't like or don't need that option.

Thinking it was a Nautilus thing, I installed Thunar, but it has the exact useless algorithm. And then I installed PCManFM, but it's also the same.

Does anyone have any idea if I can install a file manager that correctly sorts my files? Or will I need to switch to Windows to have it fixed? (not joking here, Windows Explorer doesn't suffer from this feature)

---

### Post by R2D2! on 2011-02-05
This is driving me crazy. I read on other forum that GNOME Commander wasn't affected by this bug, so I installed it, and it still sorts files the wrong way. I'm believing to think this is an Ubuntu-specific bug, but I have no way to confirm, since I don't have installed another distro.

---

### Post by asmoore82 on 2011-02-06
That *is* interesting.

I've done some testing and noticed that for nautilus, the problem
goes away if the name is all spaced out. Here's my testing routine,
you can use the for loop at the end for a workaround:
```
mkdir test
cd test
touch E0{0,1}{{0..9},{A..F}}.txt
#look in nautilus, screen1
for file in *.*
do
    ext="${file##*.}"
    new="$( echo "${file%.*}" | sed 's/./& /g' )"
    mv -iv "$file" "$new.$ext"
done
#look in nautilus, screen2
```

---

### Post by R2D2! on 2011-02-06
(duplicate post)

---

### Post by R2D2! on 2011-02-06
Well, that's a dirty fix, and it can cause me problems with my scripts (because of the spaces).

What I really want to know is if this “feature” is Ubuntu-specific, or Gnome-specific, or that those all file managers (so far: Nautilus, Thunar, PCManFM, Gnome Commander) implement it independently.

---

### Post by asmoore82 on 2011-02-06
> **R2D2! said:**
> Well, that's a dirty fix,Not perfect; but not "dirty" either.

> **R2D2! said:**
> it can cause me problems with my scripts (because of the spaces).If that's the case, you definitely need to tighten up your scripts.
Finding fault with nautilus sorting but knowing that the spaces will
break your scripts is a pot and kettle situation, don't you think?

> **R2D2! said:**
> What I really want to know is if this “feature” is Ubuntu-specific, or Gnome-specific, or that those all file managers (so far: Nautilus, Thunar, PCManFM, Gnome Commander) implement it independently.I tested this on an aging Fedora box(version 12) - it's the same way.

Here's another ***dingy*** (:lolflag:) workaround without spaces,
translate the names to decimal!:
```
for file in E0??.txt
do
    mv -iv "$file" "$(( 0x${file%.txt} )).txt"
done
[COLOR="Red"]#sample output
`E007.txt' -> `57351.txt'
`E008.txt' -> `57352.txt'
`E009.txt' -> `57353.txt'
`E00A.txt' -> `57354.txt'
`E00B.txt' -> `57355.txt'
`E00C.txt' -> `57356.txt'
`E00D.txt' -> `57357.txt'
`E00E.txt' -> `57358.txt'[/COLOR]
```

---

### Post by R2D2! on 2011-02-06
(duplicate post)

---

### Post by R2D2! on 2011-02-06
I don't want to sound rude, but none of your solutions addresses the REAL problem: the “smart” sorting algorithm. Of course I can change the name of my files (and fix my scripts), but what would happen when I'm checking somebody else's files (for example, via SAMBA or FTP)? If I don't have permissions on the files, then any of those solutions become useless.

P.S. I won't use decimal. Nobody uses decimal for Unicode (those files are glyphs for a font I'm working on).

---

### Post by sidzen on 2011-02-06
Learn PERL and write your own script!
[URL="http://perldoc.perl.org/functions/hex.html"]
Start looking [/URL]

---

### Post by R2D2! on 2011-02-06
Do you want me to write a new file manager from scratch?? That would take me months, if not years. It's easier to fix a bug from an existing program than writing a new one.

---

### Post by asmoore82 on 2011-02-06
> **R2D2! said:**
> I don't want to sound rude, but none of your solutions addresses the REAL problem
A workaround is just that - a workaround; take it or leave it.

> **R2D2! said:**
> the “smart” sorting algorithm.
Continued cheap shots at the algorithm don't help you either. They got decimal
sorting fixed; hex sorting still needs work. If I had to pick one or the other,
I'd pick decimal. Surely any patch that fixes the hex sorting will be rejected
if it breaks the decimal sorting. 

> **R2D2! said:**
> but what would happen when I'm checking somebody else's files (for example, via SAMBA or FTP)? If I don't have permissions on the files, then any of those solutions become useless.Collaborative development: check out; work; check in.
*If* the situation arises, you can always copy the files down and have at them.

---

### Post by coldraven on 2011-02-06
Try using Krusader, it's in the Software Centre.
See my screenshot, this was the default (Krusader) mode but others are available.

---

### Post by R2D2! on 2011-02-06
> **coldraven said:**
> Try using Krusader, it's in the Software Centre.
See my screenshot, this was the default (Krusader) mode but others are available.

If I install it, it will bring dozens of KDE dependencies (remember I'm in Gnome).

Can you show me a screenshot with both Krusader and Nautilus, to see if it's worth installing? All the other fm's I've installed were said to fix the problem, but they really didn't.

---

### Post by R2D2! on 2011-02-06
> **asmoore82 said:**
> Continued cheap shots at the algorithm don't help you either. They got decimal
sorting fixed; hex sorting still needs work. If I had to pick one or the other,
I'd pick decimal. Surely any patch that fixes the hex sorting will be rejected
if it breaks the decimal sorting.

How would fixing hex sorting break decimal sorting? o.O

---

### Post by Elfy on 2011-02-06
People have tried to help you - you're not too interested in the help they've given with their time. 

If you think it's a bug, report it.

---

### Post by R2D2! on 2011-02-06
There are at least 3 bug reports on this sorting method:
[https://bugs.launchpad.net/nautilus/+bug/393411](https://bugs.launchpad.net/nautilus/+bug/393411)
[https://bugs.launchpad.net/nautilus/+bug/322271](https://bugs.launchpad.net/nautilus/+bug/322271)
[https://bugs.launchpad.net/nautilus/+bug/131529](https://bugs.launchpad.net/nautilus/+bug/131529)

And here are other discussions that have taken place here, in Ubuntuforums:
[http://georgia.ubuntuforums.org/showthread.php?t=574775&page=2](http://georgia.ubuntuforums.org/showthread.php?t=574775&page=2)
[http://ubuntuforums.org/showthread.php?t=471154](http://ubuntuforums.org/showthread.php?t=471154)
[http://ubuntuforums.org/showthread.php?t=1588316](http://ubuntuforums.org/showthread.php?t=1588316)

So don't think I'm just stubborn. I'm just trying to find a solution, as well as all these people.

---

### Post by R2D2! on 2011-02-06
Also, an upstream bug:
[https://bugzilla.gnome.org/show_bug.cgi?id=355152](https://bugzilla.gnome.org/show_bug.cgi?id=355152)

---

### Post by Elfy on 2011-02-06
Not looking like there's much in the way of change coming for it then if they are anything to go by. In the meantime please remember all of us volunteer our time when replying to posts. 

> If I install it, it will bring dozens of KDE dependencies (remember I'm in Gnome).If I was you I would try it myself - you can remove the dependencies.

---

### Post by coldraven on 2011-02-07
> If I install it, it will bring dozens of KDE dependencies (remember I'm in Gnome). 			 		

That's why it took three minutes to download and install :lolflag:

---

