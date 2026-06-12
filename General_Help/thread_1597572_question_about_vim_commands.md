---
title: "question about vim commands"
date: 2010-10-15
forum: General Help
---

### Post by oren tal on 2010-10-15
I read a pdf book about vim, the book say that if I use the command 4b then the cursor moves 4 words back, or 4w it moves 4 words forward.
However while b and w command work for me, they always make the cursor move one word.
The same happen to me with command $, it move the cursor to the end of the line but 2$ still move it to the end of the line and not to the end of the next line as the book claim.

is it problem with the vim definition?

---

### Post by WorMzy on 2010-10-15
I think there's probably a problem with your .vimrc file. Post it here and we'll take a look at it.

(Press Ctrl+H in nautilus to view hidden files)

---

### Post by oren tal on 2010-10-15
> **WorMzy said:**
> I think there's probably a problem with your .vimrc file. Post it here and we'll take a look at it.

(Press Ctrl+H in nautilus to view hidden files)

I have this file in my home directory, however it is empty file.
I created it with "touch .vimrc"

---

### Post by oren tal on 2010-10-15
> **oren tal said:**
> I have this file in my home directory, however it is empty file.
I created it with "touch .vimrc"

I erased the file and it solved the problem, so I guess you are right.

I created this file in the first place because this book suggested it, but I guess it was wrong.

---

### Post by WorMzy on 2010-10-15
There's no point having a blank one, you're supposed to put your own custom configuration inside it, enabling the hidden features of vim which you want enabled. Using vim without one is basically the same as just using vi.

You can find an example .vimrc file at /usr/share/vim/vim73/vimrc_example.vim

---

### Post by oren tal on 2010-10-15
> **WorMzy said:**
> There's no point having a blank one, you're supposed to put your own custom configuration inside it, enabling the hidden features of vim which you want enabled. Using vim without one is basically the same as just using vi.

You can find an example .vimrc file at /usr/share/vim/vim73/vimrc_example.vim

thanks

---

