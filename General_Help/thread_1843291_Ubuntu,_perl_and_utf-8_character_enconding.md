---
title: "Ubuntu, perl and utf-8 character enconding"
date: 2011-09-13
forum: General Help
---

### Post by aaalbatrosss on 2011-09-13
Beginner in Perl.

I made a Perl script that parse data from html site. My script encodes the parse data in UTF-8, one of the data contains romanian characters, so encoding the data results in incorrect characters such as:
(befor and after I set default environment (Ubuntu 10.04) to use the Romanian code page)

[COLOR="Red"]**&#355;**[/COLOR] = [COLOR="Red"]**þ**[/COLOR] (incorrect); [COLOR="Red"]**&#351;**[/COLOR] = [COLOR="Red"]**º**[/COLOR] (incorrect); [COLOR="Red"]**&#259;**[/COLOR] = [COLOR="Red"]**ã**[/COLOR] (correct);

line example to parse from html (without html tags):

[COLOR="Red"]**Distribu&#355;ia**[/COLOR]: **Robert Downey Jr.** (Sherlock Holmes) **Jude Law** (Dr. John Watson) **Rachel McAdams** (Irene Adler) **Mark Strong** (Lord Blackwood) **Kelly Reilly** (Mary Morstan) **Eddie Marsan** (Inspectorul Lestrade) **James Fox** (Sir Thomas)

I want to split this with:

```
my ($credits, $line)
foreach $credits (split /(?=\w+:)\s*/, $line) {
...
```

Output, because **&#355;** is encoded incorrect as "**þ**", this is interpreted as "non-word character", line breaks incorrectly here, is:

[COLOR="Red"]**Distribuþ**[/COLOR]
**Robert Downey Jr.** (Sherlock Holmes)
**Jude Law** (Dr. John Watson)
**Rachel McAdams** (Irene Adler)
**Mark Strong** (Lord Blackwood)
**Kelly Reilly** (Mary Morstan)
**Eddie Marsan** (Inspectorul Lestrade)
**James Fox** (Sir Thomas)

Output wanted (correct):

[COLOR="Red"]**Distribu&#355;ia**[/COLOR]
**Robert Downey Jr.** (Sherlock Holmes)
**Jude Law** (Dr. John Watson)
**Rachel McAdams** (Irene Adler)
**Mark Strong** (Lord Blackwood)
**Kelly Reilly** (Mary Morstan)
**Eddie Marsan** (Inspectorul Lestrade)
**James Fox** (Sir Thomas)

If I use "\p{Alpha}" variable instead of "\w", partially solve the problem (line breaks correctly, but displays the "[COLOR="Red"]**Distribuþia**[/COLOR]" rather than "[COLOR="Red"]**Distribu&#355;ia**[/COLOR]", look like this (incorrect):

[COLOR="Red"]**Distribuþia**[/COLOR]
**Robert Downey Jr.** (Sherlock Holmes)
**Jude Law** (Dr. John Watson)
**Rachel McAdams** (Irene Adler)
**Mark Strong** (Lord Blackwood)
**Kelly Reilly** (Mary Morstan)
**Eddie Marsan** (Inspectorul Lestrade)
**James Fox** (Sir Thomas)

---

