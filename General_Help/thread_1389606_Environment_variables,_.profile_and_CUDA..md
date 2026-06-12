---
title: "Environment variables, .profile and CUDA."
date: 2010-01-24
forum: General Help
---

### Post by kajman on 2010-01-24
Hi!

I've been trying to learn something about GPU programming lately, and I've came to the following issue:
I have to configure the path variables to contain /usr/local/cuda, /usr/local/cuda/bin (in PATH variable) and /usr/local/cuda/lib in LD_LIBRARY_PATH variable. I tried to achieve it using the .profile script.
It looks like this now:
```

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
# CUDA
if [ -d "/usr/local/cuda" ] ; then
PATH="/usr/local/cuda:$PATH"
fi

if [ -d "/usr/local/cuda/lib" ] ; then
LD_LIBRARY_PATH="/usr/local/cuda/lib:$LD_LIBRARY_PATH"
fi

if [ -d "/usr/local/cuda/bin" ] ; then
PATH="/usr/local/cuda/bin:$PATH"
fi

```

What I don't understand is that, these script appends paths correctly to my PATH variable at system startup, but it doesn't do it in case of LD_LIBRARY_PATH. This variable is always empty, and I have to manually append the path, export the variable and run ldconfig which is a little bit annoying. Why is that happening? How to make the script work correctly? (of course the /usr/local/cuda/lib path exists)

---

### Post by Brandon Williams on 2010-01-24
You will always have a pre-export variable called PATH in your environment, but LD_LIBRARY_PATH is not there by default. As a result, you should check for it's existance when adding another value to the list, and you should export the variable to make sure that it is passed through to child processes. I suggest this:
```
if [ -d "/usr/local/cuda/lib" ] ; then
export LD_LIBRARY_PATH="/usr/local/cuda/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}"
fi
```

---

