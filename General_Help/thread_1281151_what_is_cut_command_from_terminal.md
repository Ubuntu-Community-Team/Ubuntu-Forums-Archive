---
title: "what is cut command from terminal?"
date: 2009-10-03
forum: General Help
---

### Post by abhilashm86 on 2009-10-03
i know to use cp command to copy, what is cut function command, i'm now using almost terminal, its great......
but when i use cp, it'l just copy that file to another location, how to use cut in terminal?

---

### Post by Belathor on 2009-10-03
Check out the mv command.

---

### Post by abhilashm86 on 2009-10-03
> **Belathor said:**
> Check out the mv command.

yup did it, thanks, first i thought mv is only for renaming files!!

---

### Post by PGScooter on 2009-10-03
hmm.. I don't think this would be too difficult to make aliases that accomplish this.

for example
alias newcut='export CUTPATH=$pwd/'
alias newpaste='mv $CUTPATH ./'

I really doubt those ones will work, but they give you an idea. If this is really important and you can't figure out a way, post back and I'll try to look into it in a few days when I will be on a comp with ubuntu.

good luck!

---

