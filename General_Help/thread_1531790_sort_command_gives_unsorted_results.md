---
title: "sort command gives unsorted results"
date: 2010-07-15
forum: General Help
---

### Post by Skaperen on 2010-07-15
It sure looks not quite sorted to me.  See lines 3 and 4.

```
altair/root /root 250# sort -k1 < files.out | head -6
/bin base-files
/bin bash
/bin/bash bash
/bin bsdutils
/bin/bunzip2 bzip2
/bin/bzcat bzip2
altair/root /root 251# 
```

Shouldn't lines 3 and 4 be the other way around?

---

### Post by ajgreeny on 2010-07-15
I don't see why.

Surely
```
/bin/bash bash
/bin bsdutils
```
is the correct order for this.  Why do you think it is wrong?

---

### Post by Skaperen on 2010-07-15
> **ajgreeny said:**
> I don't see why.

Surely
```
/bin/bash bash
/bin bsdutils
```is the correct order for this.  Why do you think it is wrong?
Then see lines 2 and 3.

The sorting is on column 1.  Generally that has always been "longer string collates higher when the common substring is equal".  But in this case note that lines 1 and 2 and 4 (NOT 3) have "/bin".  So even if the sort order for different length is reversed, it's still not right somewhere ... e.g. it's inconsistent (as if the length difference meant "pick a random number").

FYI, on my Slackware system, it sorts it this way:```
/bin base-files
/bin bash
/bin bsdutils
/bin/bash bash
/bin/bunzip2 bzip2
/bin/bzcat bzip2
```

---

### Post by ajgreeny on 2010-07-15
OK, I see what you mean.  Can't help, I'm afraid.

---

### Post by prodigy_ on 2010-07-15
```
sort -k1,1
```

---

### Post by dcstar on 2010-07-16
> **Skaperen said:**
> 
.........
FYI, on my Slackware system, it sorts it this way:
.........

Look at this:

[http://ubuntuforums.org/showthread.php?t=894734](http://ubuntuforums.org/showthread.php?t=894734)

---

### Post by Skaperen on 2010-07-16
> **dcstar said:**
> Look at this:

[http://ubuntuforums.org/showthread.php?t=894734](http://ubuntuforums.org/showthread.php?t=894734)

The only thing it seems to suggest there is LC_COLLATE=C which doesn't change anything.  This is more like sorting

1
12
123
1
12
123
1
12
123

and getting

1
1
12
1
12
123
12
123
123

One should get at least consistency on any collate:

123
123
123
12
12
12
1
1
1

might be wrong, but would at least be consistent.  What I'm getting is not even consistent.

---

### Post by Skaperen on 2010-07-16
> **prodigy_ said:**
> ```
sort -k1,1
```
Now this does change things and it now sorts consistently on column one.  The default is to sort to end of line instead of within one column, and that is still broken.

Actually, the behaviour looks like it is ignoring special characters as if -d were specified (it isn't), even if LC_COLLATE=C is specified (where it absolutely should not).  See here where using '<' and '>' as separators has no effect.  But even reversing to '>' and '<' leaves things in exactly the same order.  It's entirely not seeing any collation of special characters.  For base reference, I tried '0' and '1' vs. '1' and '0' at the end which gets expected results.
```
altair/phil /home/phil 560> cat data.in | LC_COLLATE=C sort
/bin base-files
/bin bash
/bin/bash bash
/bin bsdutils
/bin/bunzip2 bzip2
/bin/bzcat bzip2
altair/phil /home/phil 561> cat data.in | LC_COLLATE=C sort -k1
/bin base-files
/bin bash
/bin/bash bash
/bin bsdutils
/bin/bunzip2 bzip2
/bin/bzcat bzip2
altair/phil /home/phil 562> cat data.in | LC_COLLATE=C sort -k1,1
/bin base-files
/bin bash
/bin bsdutils
/bin/bash bash
/bin/bunzip2 bzip2
/bin/bzcat bzip2
altair/phil /home/phil 563> cat data.in | tr ' /' '<>' | LC_COLLATE=C sort
>bin<base-files
>bin<bash
>bin>bash<bash
>bin<bsdutils
>bin>bunzip2<bzip2
>bin>bzcat<bzip2
altair/phil /home/phil 564> cat data.in | tr ' /' '><' | LC_COLLATE=C sort
<bin>base-files
<bin>bash
<bin<bash>bash
<bin>bsdutils
<bin<bunzip2>bzip2
<bin<bzcat>bzip2
altair/phil /home/phil 565> cat data.in | tr ' /' '01' | LC_COLLATE=C sort
1bin0base-files
1bin0bash
1bin0bsdutils
1bin1bash0bash
1bin1bunzip20bzip2
1bin1bzcat0bzip2
altair/phil /home/phil 566> cat data.in | tr ' /' '10' | LC_COLLATE=C sort
0bin0bash1bash
0bin0bunzip21bzip2
0bin0bzcat1bzip2
0bin1base-files
0bin1bash
0bin1bsdutils
altair/phil /home/phil 567> 
```

---

### Post by prodigy_ on 2010-07-16
> **Skaperen said:**
> The default is to sort to end of line instead of within one column, and that is still broken.
It's not broken. RTFM, seriously. Man is a bit vague on -k option, I agree, but it does tell what the default behavior (if you omit POS2) is.

---

### Post by The Cog on 2010-07-16
> **prodigy_ said:**
> It's not broken. RTFM, seriously. Man is a bit vague on -k option, I agree, but it does tell what the default behavior (if you omit POS2) is.

You must have a different manual to me.

---

### Post by The Cog on 2010-07-16
try: 
cat data.in | LC_ALL=C sort

---

### Post by Skaperen on 2010-07-16
I don't see where in the man page that it should leave portions of the file unsorted, or sort parts forward and other parts in reverse.  All it mentions about POS2 is that if omitted, it goes to the end of the line.  But that is not relevant when the first part indeed has differences.  Where there are no differences in the first part, a later part would, of course, determine the sort order.  But those lines would still be in a group, in a position determined by the first part.

```
/bin bash
/bin/bash bash
/bin bsdutils
```

In all 3 of these lines, the first 4 characters ("/bin") are the same, so they have no effect.  The next character is "/" in line 2, and " " in both lines 1 and 3.

Now, if the sort treats " " as a delimiter, it's a matter of comparing "/bin" to "/bin/bash" and rules for different length keys would apply, whatever they are.  But no imagined rule can put "/bin/bash" between two instances of "/bin".

Or maybe the sort treats " " as part of the data to compare.  If so, it has "/" to compare against, under some collation.  In ASCII that would be " " before "/".  But even if the order is reversed, there is no way to get "/" between two instances of " ".  You have to either get the two " " cases first, or last, depending on sort order.

A third possibility exists.  It is comparing " " against "/" and treats them as equal.  Then we might indeed get what I'm seeing happen.  Do you think this is what is happening?

A remote fourth possibility is that it is using " " as the delimiter AND treats two strings of different length as equal if the common subset of the string is the same ... by ignoring the excess of the longer string.

I believe the fourth logic to be too absurd to even be an option.  The third might be under some odd collation meant to ignore special characters.  There is an option (-d) that might even do that.  But there is no option to NOT do what -d does.  It would make no sense to make -d be a default because there is no --do-not-do-dash-d or whatever.

It works as I would expect it to work, on Slackware.  It is an older version, too.

---

### Post by Skaperen on 2010-07-16
> **The Cog said:**
> try: 
cat data.in | LC_ALL=C sort
Right.

But the default collation ... what is it?  It just seems to be too utterly absurd for any practical use to be an option, much less being thrust on us as the default.

---

### Post by prodigy_ on 2010-07-16
> **The Cog said:**
> You must have a different manual to me.
Most probably. Mine's from Karmic (coreutils v7.4).

---

### Post by The Cog on 2010-07-16
I found this reference which looks useful:
[http://teaching.idallen.com/net2003/06w/notes/character_sets.txt](http://teaching.idallen.com/net2003/06w/notes/character_sets.txt)
[http://wiki.archlinux.org/index.php/Locale](http://wiki.archlinux.org/index.php/Locale)

To my mind, all the sorting functions are fundamentally unreliable, in a completely undocumented way, requiring a bodge environment setting to fix them. No command argument available to correct it. What a mess!

---

### Post by dcstar on 2010-07-17
> **Skaperen said:**
> Right.

But the default collation ... what is it?  It just seems to be too utterly absurd for any practical use to be an option, much less being thrust on us as the default.

It is whatever is set in the LOCALE definition you are using.

---

