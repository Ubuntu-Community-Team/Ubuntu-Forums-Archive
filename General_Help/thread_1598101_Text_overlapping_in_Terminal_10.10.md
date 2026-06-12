---
title: "Text overlapping in Terminal 10.10"
date: 2010-10-16
forum: General Help
---

### Post by jesuisbenjamin on 2010-10-16
Hello there,

As i used Terminal, i noticed something odd: the text is overlapping itself. In other words space between letters is uneven and can be negative.

See screenshot if you wish.

What could cause that? Is it a Maverick bug? Or has it something local?

Thanks.

---

### Post by dcstar on 2010-10-16
> **jesuisbenjamin said:**
> Hello there,

As i used Terminal, i noticed something odd: the text is overlapping itself. In other words space between letters is uneven and can be negative.

See screenshot if you wish.

What could cause that? Is it a Maverick bug? Or has it something local?

Thanks.

Check your screen resolution and font settings - my 10.10 test system looks ok.

---

### Post by Quackers on 2010-10-16
It looks like some kind of spacing thing. Like it gives each letter the same amount of space, whether it needs it or not. It just seems to be the i j and l characters, which don't normally need the same width space as all other letters.

---

### Post by jesuisbenjamin on 2010-10-16
Thanks guys,

(and good observation Quakers :) )

I have changed the Terminal settings by unchecking "Use the sytem fixed width font" option. The problem is solved.

An hypothesis may be that i changed the default system font of 10.10 (the new Ubuntu font--ugly and unnecessary in my opinion) to Sans. But that's a hypothesis only.

---

