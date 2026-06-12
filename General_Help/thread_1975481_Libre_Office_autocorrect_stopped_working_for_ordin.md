---
title: "Libre Office autocorrect stopped working for ordinal numbers"
date: 2012-05-07
forum: General Help
---

### Post by Paddy Landau on 2012-05-07
In Libre Office, if I enter a sentence such as the following:[INDENT][IMG]http://ubuntuforums.org/attachment.php?attachmentid=217476&stc=1&d=1336407021[/IMG]
[/INDENT]The "st" after the number "1" is automatically set to superscript.

Well, it used to be... until a couple of days ago. It has stopped doing it:[INDENT][IMG]http://ubuntuforums.org/attachment.php?attachmentid=217475&stc=1&d=1336407021[/IMG]
[/INDENT]The following is set, and I have not changed it:
> Tools > AutoCorrect Options > Localised Options > Format ordinal numbers suffixes (1st -> 1^st)How can I get it to start working again? I use that feature often.

---

### Post by Paddy Landau on 2012-05-08
Bump!

---

### Post by Paddy Landau on 2012-05-09
I have found that this has been reported as a bug.

[https://bugs.freedesktop.org/show_bug.cgi?id=38242](https://bugs.freedesktop.org/show_bug.cgi?id=38242)
[https://bugs.freedesktop.org/show_bug.cgi?id=48971](https://bugs.freedesktop.org/show_bug.cgi?id=48971)

Marking as solved because it is being addressed.

---

### Post by BigBaka on 2012-05-28
I wonder how you can mark this topic as solved when it hasn't been solved at all... Just because it is a confirmed bug doesn't mean it's "solved". Seems a trifle misleading. Maybe we should have an "unsolveable" tag?

Anyway, I have the same problem using 12.04 with libreoffice 3.5.3.2. The 1st becomes 1St under auto correct. If someone works out a work around please post here. 

BB

---

### Post by Paddy Landau on 2012-05-28
> **BigBaka said:**
> I wonder how you can mark this topic as solved when it hasn't been solved at all... Just because it is a confirmed bug doesn't mean it's "solved". Seems a trifle misleading. Maybe we should have an "unsolveable" tag?
Good question. To me, "solved" means there is an answer, even if it is still in progress. Perhaps I should unmark it?

Temporary workarounds that I have started to use:

[LIST]
[*]Highlight the st, nd, rd, or th and press Ctrl-Shift-P to quickly set superscript.
[/LIST]
 
[LIST]
[*]Create the first several ordinals (1st, 2nd, 3rd, ...) and set the superscripts using Ctrl-Shift-P (or however you like). For each ordinal do as follows:
[LIST=1]
[*]Highlight the ordinal (e.g. 1st).
[*]Tools > Autocorrect > *paste* > New > OK.
[/LIST]
 
[/LIST]
[INDENT]Now you can type 1st, 2nd, etc. followed by a space or tab and it will auto-correct. This works only for the specific ones you put in, and you can go as far as you have patience for. My patience ran out after 10th.
[/INDENT]These are nowhere near as handy as how it's supposed to work, but let's hope Libre Office fixes its problem soon!

> **BigBaka said:**
>  Anyway, I have the same problem using 12.04 with libreoffice 3.5.3.2. The 1st becomes 1St under auto correct.
That is weird; I cannot duplicate this.  Does the "S" capitalise only if you use "1st" at the start of the sentence, or every time? Which language setting are you using?

---

### Post by freshminted on 2012-08-06
Having the same problem I am grateful to paddy for a workround. The real issue is that the settings put in are unstable, so should an earlier version of Libre Office not suffer this?

---

### Post by Paddy Landau on 2012-08-06
> **freshminted said:**
> The real issue is that the settings put in are unstable, so should an earlier version of Libre Office not suffer this?
I don't understand what you are asking. The settings, as far as they work for me, are stable; unless I have misunderstood your meaning.

You can certainly use an earlier version of LibreOffice, if you wish. Follow [the bug in question]("https://bugs.freedesktop.org/show_bug.cgi?id=38242") (add yourself to its CC List) in order to be alerted when it is solved, and be sure to vote for [the Launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/992807") (the green writing at the top left).

---

