---
title: "command line argument protection"
date: 2010-12-27
forum: General Help
---

### Post by MichaelBurns on 2010-12-27
Is there a standard accepted way to "protect" arguments to commands in bash, so that they are passed to their command as intended rather than being interpretted as bash reserved words?  I'm getting overwhelmed with contextual ambiguities in bash, grep, etc..  For example, it is not obvious to me what is the best way to pass a regular expression that contains literal spaces to grep (bash apparently interprets these before passing the regular expression to grep).  Also, is quotation on the command line ***ALWAYS*** interpretted by bash rather than by the command to which it may be passed as part of an argument?

---

### Post by noah++ on 2010-12-27
Are you familiar with [escape characters]("http://www.hypexr.org/bash_tutorial.php#spaces")? Otherwise, can you give an example of a command that doesn't behave as you'd want?

---

### Post by MichaelBurns on 2010-12-27
> **noah++ said:**
> Are you familiar with escape characters?Yes.  Escaping is a form of quoting, that is, single character quoting, and the problem for me is that there is quoting for bash and then quoting for the argument to the command that I run from bash, and sometimes the way that I choose to handle this feels really sloppy.  I have always eventually figured out how to do it with quoting, but, for lack of a better way of saying it, it just feels dangerous.  I would just like to know if there is some argument protection policy that will ALWAYS work in bash, and could NEVER cause a problem for the command that takes the argument.

> **noah++ said:**
> ... can you give an example of a command that doesn't behave as you'd want?grep, as in:
```

grep -v -e unwanted text myfilename

```
I have written it in a form that emphasizes the problem to the human reader.  It just looks ambiguous.  Of course, I know that I could use any of the following three quoted versions
```

grep -v -e unwanted\ text myfilename
grep -v -e "unwanted text" myfilename
grep -v -e 'unwanted text' myfilename

```
and then some, but it makes me nervous.  That quoting is for bash's sake, but it is buried in the grep arguments, and my human mind is boggled when it gets only a little bit more complex than this.  I realize my own limitations; I know that I know nothing: a little bit of knowledge is a dangerous thing.

Maybe I just need to step away from the computer for a while.

Thanks for responding.

---

### Post by noah++ on 2010-12-27
My advice:
1. Check out the *xargs *command.
2. When in doubt, quote.

---

### Post by MichaelBurns on 2011-01-03
OK, here's an example of failed quoting:
```

user@computer:~$ find /my/dir/ -name foo* -exec 'cp {} /my/other/dir/. ;'
find: missing argument to `-exec'

```
The idea is that the **-exec** action of the **find** command has certain syntax that needs to be protected from bash, namely **{}** to represent the file that was found, and **;** to represent the end of the commands to be executed.

I will be investigating **xargs** now.

BTW, escaping *did* work:
```

user@computer:~$ find /my/dir/ -name foo* -exec cp \{\} /my/other/dir/. \;

```
I don't understand why it should complain with the single quotes but accept the escaping.  At the risk of sounding lazy, I hate escaping; it forces me to remember arbitrary shell needs (and it looks so damn sloppy).

---

### Post by endotherm on 2011-01-03
there are several kinds of quotes in bash that have differant meanings:
" => treat as a single string, but intepret all vars and keywords
' => treat as a string literal. no expansion or interpretation
` (backqoute, on the tilde key) => interpret/expand

[http://wiki.bash-hackers.org/syntax/quoting](http://wiki.bash-hackers.org/syntax/quoting)

---

### Post by MichaelBurns on 2011-01-03
> **endotherm said:**
> there are several kinds of quotes in bash that have differant meanings:
...
' => treat as a string literal. no expansion or interpretation
...

Yes, I know this, and that was precisely my intent, so I am still confused.  I wanted **-exec** to expand and interpret, not bash.  But instead, **-exec** apparently completely ignored my arguments.

---

### Post by endotherm on 2011-01-03
I've seen that error before. I seem to recall having gotten around it by adding a plus sign ('+') to the end of the -exec line, but was never sure why that worked.

---

### Post by nothingspecial on 2011-01-03
> **MichaelBurns said:**
> OK, here's an example of failed quoting:
```

user@computer:~$ find /my/dir/ -name foo* -exec 'cp {} /my/other/dir/. ;'
find: missing argument to `-exec'

```


quote the -name parameter, and quote the result (ie '{}') and escape the ;

so


```
find /my/dir/ -name 'foo*' -exec cp '{}' /my/other/dir/ \;
```

---

### Post by MichaelBurns on 2011-01-04
@endotherm&nothingspecial
Thank y'all for taking time to reply.  However, we're getting a bit off-track.  The point is: what will *always* work?  So far, we've learned that single quotes will *not*.  I.e., we (I) have answered the question from the OP:
> ... is quotation on the command line ALWAYS interpretted by bash rather than by the command to which it may be passed as part of an argument?
with an apparent "no".  That was the purpose of my example.  How to use the **-exec** action of the **find** command is simply a matter of trial-and-error.  But, that's the point: trial-and-error bad; predictability good.

It seems that escaping may be the only form of quoting that always "works".  I just simply don't like this; the rules are too arbitrary for me; it goes beyond the simple concept of quoting to contextual quoting (i.e. it behaves differently depending on which character it quotes).  Also, I think that there is something deeper going on sometimes.  E.g. the command operated by the **-exec** action may need to see spaces, but these spaces cannot be protected from **bash** for some reason.  So, perhaps **bash** itself is interpretting **-exec** and the words that follow!  Hmm...  that actually gives me an idea.  I'll get back with my idea and results if it works.

@noah++
I appologize; I haven't gotten very far into my investigation of the **xargs** command.  I will try to make a point of it later tonight.

BTW, I realize that this thread is pretty damn boring, and so I do appreciate any participation whatsoever.  That's also part of the point.  I want to get past these boring discussion and move on to more interesting and complex bashfu.

---

### Post by nothingspecial on 2011-01-04
You have to quote the find parameters so they are not expanded by the shell.

In my example .......

........ to make this easy .......

What you are finding 'foo*'

And what you have found '{}'

 I cannot find the words to explain it plainly, not that anyone else has.

Help

---

### Post by sisco311 on 2011-01-04
*The rules for evaluation and quoting are taken from the posix specification for the `standard' Unix shell.*
See: [http://www.gnu.org/software/bash/manual/bashref.html#Basic-Shell-Features](http://www.gnu.org/software/bash/manual/bashref.html#Basic-Shell-Features)

I will try to explain why:
```

find /my/dir/ -name 'foo*' -exec 'cp {} /my/other/dir/. ;'

```fails.

The -exec option needs at least 2 arguments, a command and a ; or + sign. (well, in case of the **-exec command {} +** syntax it needs at least 3)
**cp {} /my/other/dir/. ;** is quoted, so it's treated as a single argument and find throws the **missing argument to `-exec'** error, because the second argument (; or +) is missing.

Now lets see what happens if we try to run:
```

find /my/dir/ -name 'foo*' -exec 'cp {} /my/other/dir/.' ;

```

Now we have two arguments, but find still throws the **missing argument to `-exec'**. Why? Because before bash runs the find command it evaluates the ; sing.

```
command1 ; command2
```
means run command1 then command2.
So:
```
comamnd ;
```
is simply interpreted as:
```
command
```

Now lets quote the ; sign:
```

find /my/dir/ -name 'foo*' -exec 'cp {} /my/other/dir/.' \;

```
and output is something like:
```
find: `cp ./foo1 /my/other/dir/.': No such file or directory
find: `cp ./foo2 /my/other/dir/.': No such file or directory
```

find replaces {} with the file names, but because **cp {} /my/other/dir/.** is quoted **cp ./foo1 /my/other/dir/.** is interpreted as a single command. Yes, **cp ./foo1 /my/other/dir/.** is a valid path to file, "cp .", "foo1 ", "my", "other" and "." are valid directory names.

Hope this makes sense.

---

### Post by endotherm on 2011-01-05
thank you sisco. what is the '+' for if you don't mind me askin

---

### Post by sisco311 on 2011-01-05
**-exec command {} ;** runs the command separately on each file found:
comannd file1
comamnd file2
command file3
...

**-exec command {} +** collects the filenames into groups or sets, and runs the command once per set:

command file1 file2 file3 file4 ... file999
command file1000 file1001 ...

---

