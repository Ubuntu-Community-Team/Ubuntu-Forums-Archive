---
title: "vim help"
date: 2010-07-28
forum: General Help
---

### Post by l3ecl on 2010-07-28
When I want to edit a line in vim, I type the : followed by a number to go to that line.
So for example ":8" would go to line 8. I was wondering if there was a way to omit the
 : character, so I would only have to type 8 and it would go to 8.

---

### Post by anglican on 2010-07-28
> **l3ecl said:**
> When I want to edit a line in vim, I type the : followed by a number to go to that line.
So for example ":8" would go to line 8. I was wondering if there was a way to omit the
 : character, so I would only have to type 8 and it would go to 8.No, because vim uses the number as a way of repeating an action e.g. 8x deletes 8 characters, 8dd deletes 8 lines... and so on. Having to type a colon first is not exactly a strain!

H

---

### Post by jobix on 2010-07-28
This doesn't really address your concern of having to type an extra character, however, if you have something against the ":" character, you can use the "G" character instead. :) The difference is that it comes after the line number. So, to go to line 8 from wherever you are, you type: "8G"

---

### Post by l3ecl on 2010-07-28
> **anglican said:**
> No, because vim uses the number as a way of repeating an action e.g. 8x deletes 8 characters, 8dd deletes 8 lines... and so on. Having to type a colon first is not exactly a strain!

H

I seldom use this repeat function, however I use colon + number alot more to jump around lines.

Is there any way at all I can edit this at .vimrc?

---

### Post by jobix on 2010-07-28
If your main objective is to jump around lines, you could consider "marking" lines. If you type "mk" (without the double quotes) wherever your cursor is, this gets marked. Let's say you go down the file to some other place. Then, when you want to return to the original place, you type, ""k" (without the double quotes) and the cursor returns you there. The advantage here is that you don't have to remember line numbers.

---

### Post by l3ecl on 2010-07-28
> **jobix said:**
> This doesn't really address your concern of having to type an extra character, however, if you have something against the ":" character, you can use the "G" character instead. :) The difference is that it comes after the line number. So, to go to line 8 from wherever you are, you type: "8G"

i just want to move faster with less keystrokes. Is there a way to edit capital G to lowercase g and have it do the same thing?

---

### Post by ruehara on 2010-07-28
> **l3ecl said:**
> i just want to move faster with less keystrokes. Is there a way to edit capital G to lowercase g and have it do the same thing?


:map G g. This will last until you exit your current vim session or give the command :map G G. You can map pretty well any key to anything this way. One command I use a lot when I'm searching for a repeating pattern in a very large file is "map n nzz". This makes each 'search next' result display in the middle of the screen.

---

### Post by l3ecl on 2010-08-02
> **ruehara said:**
> :map G g. This will last until you exit your current vim session or give the command :map G G. You can map pretty well any key to anything this way. One command I use a lot when I'm searching for a repeating pattern in a very large file is "map n nzz". This makes each 'search next' result display in the middle of the screen.

that map nzz is a pretty genius idea
is there a way i could make these settings permanent? i tried writing "map G g" in my .vimrc but it didin't work.

---

