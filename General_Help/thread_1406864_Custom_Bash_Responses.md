---
title: "Custom Bash Responses?"
date: 2010-02-14
forum: General Help
---

### Post by Camaguey on 2010-02-14
I've been trying to customize my terminals, and the next step is implementing new functions. Normally, Bash commands and scripts are complicated, dealing with multiple files and doing things to them, but for now I just want the terminal to return a pre-determined response. For example:
```

"what are my chances?"
> Insufficient Data

```

10 points for the answer, 5 points for naming the movie:popcorn:

---

### Post by cjhabs on 2010-02-14
#!/bin/bash
                echo Please, enter your name
                read NAME
                echo "Hi $NAME!"

Check out:
[http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by falconindy on 2010-02-14
```
mkdir $HOME/bin
export PATH="$PATH":$HOME/bin
echo 'echo Insufficient Data' > "$HOME/bin/what are my chances\?"
chmod +x "$HOME/bin/what are my chances\?"
"what are my chances\?"
```
That's the closest you're going to get without writing your own interpreter or generating your own locale file. Bash isn't some sentient **Alien** you can have a conversation with.

---

### Post by Camaguey on 2010-02-27
> **falconindy said:**
> ```
mkdir $HOME/bin
export PATH="$PATH":$HOME/bin
echo 'echo Insufficient Data' > "$HOME/bin/what are my chances\?"
chmod +x "$HOME/bin/what are my chances\?"
"what are my chances\?"
```That's the closest you're going to get without writing your own interpreter or generating your own locale file. Bash isn't some sentient **Alien** you can have a conversation with.
I did that with successful results, and without the backslash before the question mark. I've looked more into this and I think editing my ~/.bashrc file is also possible:
```

alias "what are my chances"='echo "Insufficient Data"'

```I've also gotten bash to play music while scrolling the lyrics in a single command :D
[http://bbs.archlinux.org/viewtopic.php?id=92151](http://bbs.archlinux.org/viewtopic.php?id=92151)
Now how do I thank you?

---

