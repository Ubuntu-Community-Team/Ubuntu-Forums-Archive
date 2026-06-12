---
title: "Send command to another terminal"
date: 2010-09-10
forum: General Help
---

### Post by oinkl on 2010-09-10
I open up 2 xterms on my desktop, A(/dev/pts/0) and B(/dev/pts/1).

I can write from A to B using redirection e.g. echo "test" > /dev/pts/1

How do I run a command from A on B? e.g. "clear"


Ideally I should be able to do this from a script.
Thanks.

---

### Post by anubhavrocks on 2010-09-10
I think you are looking for something like openvt.

man openvt

---

### Post by oinkl on 2010-09-10
Hmm I couldn't get openvt to work.

Basically I'm putting the 2 terminals side by side, and using terminal B to display the contents of the current working directory, by running the following in A:

export PROMPT_COMMAND="ls -a > /dev/pts/1"

but this fills up the screen pretty fast. I was actually looking for a way to clear up the second terminal.

Any advice? Thanks.

---

### Post by john newbuntu on 2010-09-10
Does this work or am I misunderstanding something.
```
unset PROMPT_COMMAND
clear > /dev/pts/1
```

Edit: This works on my terminals

---

### Post by oinkl on 2010-09-10
> **john newbuntu said:**
> Does this work or am I misunderstanding something.
```
unset PROMPT_COMMAND
clear > /dev/pts/1
```

Tried that at first, does not work.

clear is run in the current terminal, and has no output, so nothing is redirected to the 2nd terminal.

So net effect is A is cleared, nothing happens in B.

---

### Post by john newbuntu on 2010-09-10
```
clear | tee /dev/pts/1

```

BTW, my version of bash is: GNU bash, version 4.1.5(1)-release (i486-pc-linux-gnu)

---

### Post by v1ad on 2010-09-10
> **john newbuntu said:**
> Does this work or am I misunderstanding something.
```
unset PROMPT_COMMAND
clear > /dev/pts/1
```

Edit: This works on my terminals

you are my hero with that command :D thanks.

---

### Post by oinkl on 2010-09-10
> **john newbuntu said:**
> ```
clear | tee /dev/pts/1

```

BTW, my version of bash is: GNU bash, version 4.1.5(1)-release (i486-pc-linux-gnu)

Thanks, this worked very nicely

---

