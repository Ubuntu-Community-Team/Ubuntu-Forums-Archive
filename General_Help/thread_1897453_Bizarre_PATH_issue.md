---
title: "Bizarre PATH issue"
date: 2011-12-19
forum: General Help
---

### Post by reve_etrange on 2011-12-19
I've run into this bizarre issue: calling "git commit", and only that, runs something entirely different.

```

$ git commit
Required JAR libraries not found. Please download:
  loci_tools.jar
from:
  [http://www.loci.wisc.edu/bio-formats/downloads](http://www.loci.wisc.edu/bio-formats/downloads)
as well as the OME Metadata Notebook JARs from:
  [http://www.loci.wisc.edu/software/daily/ome-editor.jar](http://www.loci.wisc.edu/software/daily/ome-editor.jar)
  [http://www.loci.wisc.edu/software/daily/ome-java.jar](http://www.loci.wisc.edu/software/daily/ome-java.jar)
  [http://www.loci.wisc.edu/software/daily/ome-java-deprecated.jar](http://www.loci.wisc.edu/software/daily/ome-java-deprecated.jar)
and place in the same directory as the command line tools.

Please note that the OME Metadata Notebook is legacy software that 
has been discontinued. Use at your own risk.
Aborting commit due to empty commit message.

```

This happens only while in a git working tree with staged changes.  I know something from my user path is the culprit (from removing ~/bin/ from $PATH), and the error message is clearly from a certain JAR and some attendant BASH scripts, none of which have anything to do with git, or even contain the words "git" or "alias" or "commit".

All the other git command work properly and I can avoid the error by using `git commit -m <msg>`.

I can tell it's not a real alias:
```

$ alias -p
alias chimera='/usr/local/chimera/bin/chimera'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias la='ls -A'
alias ll='ls -l'
alias ls='ls --color=auto'

```

But after that, I have no idea how this is arising.  There must be some strange confluence of configuration details...does anyone have a suggestion for where to look next?


**I am an idiot**
There was a file named "editor" on my PATH! D'OH!

---

### Post by gmargo on 2011-12-19
If you do a "git commit" without a "-m message" option, then git starts a text editor.  I suspect your default text editor is based on this java thing.

Do you have an EDITOR or VISUAL environment variable?  Does /usr/bin/editor (which points through /etc/alternatives/editor) point at this java editor?  Do you have a $HOME/.selected_editor file?

Update: saw your update about an 'editor' command.  Glad you solved it.

---

### Post by reve_etrange on 2011-12-19
As per that bolded update above...one of the scripts related to that JAR (it's a library for some obscure biological image formats) was actually called "editor," and I had failed to notice that when I placed them in my ~/bin/, which comes first on my PATH.

So, you are exactly right.

---

