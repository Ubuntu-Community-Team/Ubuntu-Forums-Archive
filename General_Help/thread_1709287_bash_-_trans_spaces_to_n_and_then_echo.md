---
title: "bash - trans spaces to \n and then echo?"
date: 2011-03-18
forum: General Help
---

### Post by Lorin Ricker on 2011-03-18
Okay, now I've run into something subtle:  I want to take a string of space-delimited words, translate the space-chars (" ") into newlines (**\n**) and just echo the result, which *_should output each word on a separate line_*, right?  Like this:

```
echo -e $( dirs | tr " " "\n" )
```Actually, I want to reformat the output of **dirs** -- so let's say that it generates something like:

```
~/dir3 ~/dir2 ~/dir1 ~
```...and, just for the heck of it, I want it to print it this way:

```
~/dir3
~/dir2
~/dir1
~
```But this code-frag spits out only the original single line, no matter what I do; even works this way with a **printf** instead of the **echo** command.

I know that the tr is basically working, as I can demonstrate: replacing the "\n" with "X" produces:

```
~/dir3X~/dir2X~/dir1X~
```I've tried other tricks/variants, all with the same result:  output on one line.

Any ideas or advice?  Any bash experts out there?  TIA :)

---

### Post by Lorin Ricker on 2011-03-18
I just rendered the specific question somewhat moot -- a little online digging reminds me that **dirs** has a **-v** option, which prints DIRSTACK in vertical (multiline) format, what I wanted.

But, putting **dirs** aside, what about the general question?  Given a string of space-delimited workds, how to translate spaces into newlines and echo the result the way I want?  I'm missing something here!... TIA

---

### Post by jwbrase on 2011-03-18
I find that just ```
dirs | tr " " "\n"
```

works without the echo. Echo seems only to put a newline in when there's an explicit escape sequence in the input. If there's an actual newline in the input it converts it to a space.

---

### Post by Telengard C64 on 2011-03-18
> **Lorin Ricker said:**
> ...and, just for the heck of it, I want it to print it this way:

```
~/dir3
~/dir2
~/dir1
~
```

```
foo$ pushd /etc
/etc ~/foo
etc$ pushd /tmp
/tmp /etc ~/foo
tmp$ help dirs
dirs: dirs [-clpv] [+N] [-N]
    Display the list of currently remembered directories.  Directories
    find their way onto the list with the `pushd' command; you can get
    back up through the list with the `popd' command.

    The -l flag specifies that `dirs' should not print shorthand versions
    of directories which are relative to your home directory.  This means
    that `~/bin' might be displayed as `/homes/bfox/bin'.  The -v flag
    causes `dirs' to print the directory stack with one entry per line,
    prepending the directory name with its position in the stack.  [b][u]The -p
    flag does the same thing, but the stack position is not prepended.[/u][/b]
    The -c flag clears the directory stack by deleting all of the elements.

    +N  displays the Nth entry counting from the left of the list shown by
        dirs when invoked without options, starting with zero.

    -N  displays the Nth entry counting from the right of the list shown by
        dirs when invoked without options, starting with zero.
tmp$ dirs -p
/tmp
/etc
~/foo
tmp$ dirs | tr ' ' '\n'
/tmp
/etc
~/foo
tmp$
```

HTH

---

### Post by Lorin Ricker on 2011-03-18
Many thanks for the quick responses!  Both are very helpful!  -- L

---

### Post by Telengard C64 on 2011-03-18
> **Lorin Ricker said:**
> Many thanks for the quick responses!  Both are very helpful!  -- L

NP. It gave me an excuse to review the Bash builtins  :D

---

