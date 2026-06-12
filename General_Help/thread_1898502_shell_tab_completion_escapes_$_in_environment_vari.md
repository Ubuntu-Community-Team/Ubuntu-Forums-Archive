---
title: "shell tab completion escapes $ in environment variables"
date: 2011-12-21
forum: General Help
---

### Post by zippaplick on 2011-12-21
Recently updated to natty and have run into an annoying problem with bash tab completion. Searching the interwebs has generated some hits on the issue but no solution.

Here's the issue:

I have a bunch of environment variables exported in my .bashrc that I use as shortcuts to commonly used directories, for example:

```
export trunk=~/sandbox/myproject/trunk
```

When using the bash shell I commonly use tab completion to expand this variable by typing something like:

```
cd $trunk/[TAB]
```

This used to expand inline to the real value of $trunk:

```
cd ~/sandbox/myproject/trunk/
```

Now, with bash 4.2, it instead escapes the $ and completely borks the command and my workflow. Hitting tab expands to :

```
cd \$trunk/
```

"\$" is not what I meant, nor the behavior that has existed forever.


Anyone else run into this? It's driving me nuts to have to go back & delete the \ from any command I use tab completion of environment variables on.

---

### Post by Lars Noodén on 2011-12-21
> **zippaplick said:**
> 
Anyone else run into this? It's driving me nuts to have to go back & delete the \ from any command I use tab completion of environment variables on.

I've got bash 4.2 and I've tried but am not able to duplicate the problem.

---

### Post by zippaplick on 2011-12-21
Could you try this to confirm?:

type:

```
cd $HOME/
```

then hit TAB. The trailing "/" is important to replicate this. For me it infallibly expands to:

```
cd \$HOME/
```

I mentioned bash 4.2, since others on the net reporting this refer to that version and that's what I've got. Some hits on a fedora forum about this too.

---

### Post by Lars Noodén on 2011-12-21
> **zippaplick said:**
> Could you try this to confirm?:

type:

```
cd $HOME/
```

then hit TAB. The trailing "/" is important to replicate this. 

For me it does not change.  It stays "cd $HOME/" even after trying the tab-completion.  This is bash 4.2 on Precise.

---

### Post by zippaplick on 2011-12-21
OK, thanks for trying that. Just tried it on my oneiric box and no issue there. 

Must be an issue with natty's version.

---

