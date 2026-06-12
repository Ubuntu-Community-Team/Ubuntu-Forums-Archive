---
title: "Emacs: pipe bash file contents to shell buffer"
date: 2011-06-30
forum: General Help
---

### Post by tekkenlord on 2011-06-30
Hello all, 

I was wondering whether there is a way to pass contents of a bash script file into a shell buffer in Emacs (23.2). For example, if my bash file contains a single line "ls -al", I would like to highlight that line, and by pressing a keybind, have the command executed and its output shown in the shell buffer. 

Is it at all possible? Thanks for any suggestions!

---

### Post by furtypajohn on 2011-06-30
Okay, so I was able to get the desired functionality through the use of a keyboard macro.

I did the following:

```
# Start recording the keyboard macro
C-(

# Copy the highlighted text
C-w

# Open a shell
M-x shell

# Go to the end of the shell buffer
M-x end-of-buffer

# Paste the contents to the shell
C-y

# Press enter
_enter_

# Stop recording the keyboard macro
C-)
```

Then when you highlight code you can press C-e to replay the last macro.

See: [http://www.emacswiki.org/emacs/KeyboardMacrosTricks](http://www.emacswiki.org/emacs/KeyboardMacrosTricks)

Take note of the section on saving the keyboard macro to your .emacs file and assigning a keyboard shortcut to that macro.

---

### Post by tekkenlord on 2011-06-30
Thank you. I keep forgetting how important and useful macros can be. 

I tried your suggestion and it works, even though now I would like to optimise it. But this will certainly require some lisp programming. 

Ideally, I want to highlight a region, open a shell buffer (if there is not already one open), cd to the directory where the bash buffer is and then execute the command. Also, I would like all this happening in the background, without seeing what is happening; something similar to what ESS is doing for the R language.

In any case, I am marking the thread as solved! Thanks again.

---

