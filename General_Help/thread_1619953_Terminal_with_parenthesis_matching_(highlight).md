---
title: "Terminal with parenthesis matching (highlight)"
date: 2010-11-12
forum: General Help
---

### Post by terdon on 2010-11-12
Hi all, 
      I write a lot of short scripts on the fly at the command line. Basically perl one liners, but I often get carried away and end up having several lines of code. Is there any terminal app out there that can do emacs or vi style parenthesis and brackets highlighting?

---

### Post by DaithiF on 2010-11-12
well why not use vi as your line editing mode (set -o vi)

then when typing a long command, hit ESC and v brings your line into vi where you can edit to your hearts content (including brace matching) before :wq exits back to the shell and runs your command

---

### Post by terdon on 2010-11-12
grrrrr I've managed to stick to emacs and avoid vi for the past decade! You're telling me I have to betray my principles!?? Real programmers use emacs and all that.... :) Is there a way to do the same with emacs instead?

In any case, joking apart, thanks for the answer. I'll give it a try.

---

### Post by skillet-thief on 2010-11-12
Or use one of the shell modes in emacs, shell or eshell. You get parenthesis matching for free, and you can easily move over to a buffer in cperl-mode if you need to.

---

### Post by terdon on 2010-11-12
> **skillet-thief said:**
> Or use one of the shell modes in emacs, shell or eshell. You get parenthesis matching for free, and you can easily move over to a buffer in cperl-mode if you need to.

OK, that sounds interesting. I'm not sure what you mean though. Will I need to copy/paste between the terminal and an emacs window? Open a command line emacs? How would I execute the command once I am done writing it?

---

### Post by CharlesA on 2010-11-12
Try this:

```
set -o emacs
```

I don't know if it'll work, but worth a shot, I suppose.

---

### Post by terdon on 2010-11-12
Well, I tried both set -o vi and emacs and neither seems to be doing anything. Will this work for bash or is it specific to Korn shell?

---

### Post by CharlesA on 2010-11-12
It's a bash shell environment varable as far as I know.

---

### Post by terdon on 2010-11-12
Actually, set -o vi seems to do something. I seem to be in a vi environment (I had to type i to edit) and :wq got me back to my command. Ok, so far so good, but there was no brace matching.

set -o emacs got me back to my (normal?) mode, where Ctrl+K kills a line, Ctrl=W a word etc etc.

---

### Post by CharlesA on 2010-11-12
So.. is that.. good?

I stick to vi mostly, since I'm not fond of emacs.

---

### Post by terdon on 2010-11-12
Sorry, that was not clear. 

What I meant to say is that -o emacs seems to do nothing. -o vi does something (I enter a vi-like environment) but has no parentheses matching. Do I need to issue a command in vi to get this?

I would rather do this in emacs mode since I am very used to the shortcuts and do not really know the vi ones. But I can live with vi.

---

### Post by CharlesA on 2010-11-12
I don't know, unfortunately, since I don't really do much in-line editing. I normally just start from scratch in a screen session and go from there.

---

### Post by skillet-thief on 2010-11-12
> **terdon said:**
> OK, that sounds interesting. I'm not sure what you mean though. Will I need to copy/paste between the terminal and an emacs window? Open a command line emacs? How would I execute the command once I am done writing it?

Just do M-x eshell and you'll see. So no, you never leave emacs, which of course is the whole point of emacs ;-)

---

### Post by terdon on 2010-11-19
> **skillet-thief said:**
> Just do M-x eshell and you'll see. So no, you never leave emacs, which of course is the whole point of emacs ;-)


So it is, so it is. Long live emacs!! That is pretty much exactly what I wanted. Thanks!!

---

