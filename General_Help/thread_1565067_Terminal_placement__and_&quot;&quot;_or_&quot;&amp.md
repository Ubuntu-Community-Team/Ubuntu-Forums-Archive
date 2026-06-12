---
title: "Terminal placement  and &quot;|&quot; or &quot;&amp;&quot;  R-cran"
date: 2010-08-31
forum: General Help
---

### Post by oaxacamatt1 on 2010-08-31
Hi all,
I would like to run R-base/cran in a gnome-terminal window in a specific place on the desktop, eg bottom right corner. 

I have figured out how to locate and position the terminal window using 'xwininfo' but now I would like to start up 'R' from the top panel icons.  

I cant seem to get R working after opening the terminal window!?!
For example:  gnome-terminal --geometry 69x30-0-24 && R

Should I be using the pipe '|' or something else??
Cheers,
M

---

### Post by WorMzy on 2010-08-31
Try this:

```
gnome-terminal --geometry 69x30-0-24 _-e R_
```

"-e" executes the following command in the terminal.

---

### Post by oaxacamatt1 on 2010-08-31
Hey W,
Thank you very much for the info, it works well.  

I have one more curiosity question.  If I were to look for that info in the future, where would I have found it.  Which man page?
Cheers,
Matt

---

### Post by WorMzy on 2010-08-31
```
man gnome-terminal
```

If any. But that man page doesn't exist on my system (I use Arch linux), so I use:

```
gnome-terminal --help-terminal-options
```

---

### Post by TwoEars on 2010-08-31
Or, you know, google > man gnome-terminal, that's what I do when I'm on Windows and I need to remember the syntax for a script.

---

