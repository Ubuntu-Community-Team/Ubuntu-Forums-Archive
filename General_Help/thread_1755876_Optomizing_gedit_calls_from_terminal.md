---
title: "Optomizing gedit calls from terminal"
date: 2011-05-11
forum: General Help
---

### Post by tnanek on 2011-05-11
I am trying to optomize gedit calls from my terminal. The reason for this is that I have found a nice package to theme and increase the functionality of my gedit. Now I essentially want to use it to replace my former prefferred vim.

I already got some tips from other posts, and this is what I've done so far:

I made an alias of gedit to call a bash script. See it below, it's well documented.

```

#!/bin/bash
# To optomize gedit calls from the terminal.
# 
# nohup - to make a command not be tied into the terminal.
# /usr/bin/gedit - the default gedit command.
# $@ - all the arguments passed in.
# $> /dev/null - redirects all the output to empty space.
# & - initiates a new process for the terminal to continue in.
nohup /usr/bin/gedit $@ $> /dev/null &

```

What I'd like to do is silence the output even further if at all possible. Currently, this seems to output pid information of the next terminal session (presuming what its of).

For example, below is the current output of that line in my terminal (and I predict it will be the same from the bash script).

> $ nohup /usr/bin/gedit test &> /dev/null &
[4] 7390
$


So, is there a way to redirect the output of starting a new process for terminal to continue in?

---

