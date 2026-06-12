---
title: "vim ,help with copying two parts from 2 lines"
date: 2010-03-05
forum: General Help
---

### Post by mihalisla on 2010-03-05
Hello I need some help with vim that  i cannot find.
Suppose that i have this text :

1 abc
2 def
3 ghi
4 klm

Now I want to copy(yank) only the parts:
ab from line one and hi from line three at the same time

So how can this be done with vim ???
P.S I know how to copy one line and one part of a line
What I want to do is to copy two parts from 2 different lines at the 
same time and paste them as they are some where else in the file

Thank you in advance!!!

---

### Post by flippo on 2010-03-05
Not sure *exactly* what your asking, but it sounds like vim's record and playback feature is right for you.

push q when in normal mode to inititalize the record.  Press the key you would like to record to, then recording will pop up.  Then record your actions, when you playback vim will redo every key you press while "recording" is present.  Press q again to stop it.  when your ready to play back just push '@<key you recorded to>'.

---

### Post by mihalisla on 2010-03-06
All I'm saying is that we have a text before us and what we do
is :

We select a part from a line ,we scroll down a bit,
then we select another part from another line with ctrl+....,
we copy it and then we paste the contents we copied  somewhere else


Thank u for your reply

---

### Post by flippo on 2010-03-06
You can do that record and play back, and if you haven't learned to use it yet, you should.  Its one of vim's more powerful aspects.

For example, given the file:```
hello friend
my name
is flippo
... ...
```

If I wanted to get the text "hello name" in the clipboard when I had hello highlighted I could highlight the h in hello then type in the keys:
qa0yejo[esc]pA [esc]k0wywj$pddkk0q
Then whenever I hit @a I would get the first word of line 1 and the 2nd word of line 2 in my clipboard.

NOTE: this key combo has not been tested, it may contain typos, but the idea is what I'm stressing.

---

### Post by mihalisla on 2010-03-06
thank u very much for your reply!
That is what I wanted!!!

---

