---
title: "Quick help with piping and output"
date: 2009-10-04
forum: General Help
---

### Post by Nunyah on 2009-10-04
Why won't the following command work?
```

ls -l | ls -d */

```
What i want to do here is to supply ls -l with all my directories as arguments. IE ls -l dir1 dir2 dir3 would give me files in dir1, then dir2 etc.

---

### Post by scragar on 2009-10-04
```
for x in *; do
  [ -d "$x" ] && ls -l "$x"
done;
```
Is that what you want?

---

### Post by Nunyah on 2009-10-04
Kind of yeah, but I want to use a simple one liner kind of like I showed in my example. It's more of a conceptional understanding than actually achieving the result.

If I understand piping well enough, my example should have given arguments to the first ls. I tried using ls -l < ls -d */ without success too.

---

### Post by Johnny B on 2009-10-04
try ```
ls -l `ls -d */`
```
note the backticks

---

### Post by Nunyah on 2009-10-04
Excellent, thanks! Nice to see my logic was almost right! :)

---

### Post by Johnny B on 2009-10-04
unfortunately this won't work with directories that contain spaces

---

### Post by Nunyah on 2009-10-04
Yeah, I noticed that. I don't see how you could get around that without having some kind of script run to insert \ in front on space.

---

### Post by scragar on 2009-10-05
> **Nunyah said:**
> Yeah, I noticed that. I don't see how you could get around that without having some kind of script run to insert \ in front on space.

My loop doesn't worry about spaces. Just saying.

---

### Post by Johnny B on 2009-10-10
the best way would be > ls -R
but thats not what he was asking for, he was asking why his command wouldnt work.

---

### Post by tars_ac on 2009-10-10
I think the important thing is the conceptual understanding of pipes.  Pipes send the result of the first command's standard out to the second command's standard in.  Ls isn't reading standard in (that I know of anyway), which is why the first one doesn't work.  The backticks are just telling the shell to insert the standard out of the result of the stuff inside the backticks into the command, which is almost what you want, except that it doesn't escape spaces like the shell normally does with *, so you end up with issues.

What you're looking for, I believe, is xargs.  Try man xargs to figure out how to use it (that's what I do every time since I use it so infrequently...)

Hope that helps, and sorry if you already knew this stuff.

---

