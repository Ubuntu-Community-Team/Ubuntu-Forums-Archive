---
title: "grep [[:digit:]] malfunctioning"
date: 2009-10-20
forum: General Help
---

### Post by alphaniner on 2009-10-20
I have two machines running 8.04, both fully updated.  On one of the machines, any usage of **grep [[:digit:]]** ie.
```
grep [[:digit:]] file
echo $VAR | grep [[:digit:]]
```
only works if the number '1' is present.

That is, ```
echo 023456789 | grep [[:digit:]]
```
returns nothing but ```
echo 0123456789 | grep [[:digit:]]
```
returns 0123456789.

Also, using strings of digits such as in```
echo 2 | grep [0-9]
echo 2 | grep [0123456789]
``` return nothing.  But if I remove the '1' from the string ie.```
echo 2 | grep [02-9]
echo 2 | grep [023456789]
``` or any other conceivable combination without '1', it returns the number as expected.

:confused:

I have no idea what to make of this.  Any thoughts?

---

### Post by kidders on 2009-10-21
Hi there,

This sounds suspiciously like a shell expansion issue. For example ...

```
$ mkdir ~/foobar
$ cd !$
$ echo 023456789 | grep [[:digit:]]
023456789
$ touch 1
$ echo 023456789 | grep [[:digit:]]
$ echo 023456789 | grep "[[:digit:]]"
023456789
```

The reason my second "echo" returns nothing is because what's actually being executed is **echo 023456789 | grep 1**. It's not really a good idea to pass arguments liable to expansion to utilities like grep without suitable quoting ... unless of course you *want* them expanded. For instance, continuing from above, which of the following is correct depends on whether you're interested in files called "1", "2", "3", etc. or files called "[[:digit:]]" ...

```
$ ls [[:digit:]]
1
$ ls "[[:digit:]]"
ls: cannot access [[:digit:]]: No such file or directory
```

Anyhow, that's just a hunch ... I could well be wrong. A malfunctioning grep is impossibly unlikely really, so there's a rational explanation *somewhere* ... we just have to find it hehe.

---

### Post by alphaniner on 2009-10-21
I think you're right.  A line in my script was creating a file called '1'; I weeded it out late yesterday.  Since then the problem was seemingly intermittent, probably due to the directory I was in.

Are you not using bash?  Because I had to place the quotes differently:

```
testing@caddywompus:~/foobar$ echo 023456789 | "grep [[:digit:]]"
bash: grep [[:digit:]]: command not found
testing@caddywompus:~/foobar$ echo 023456789 | grep "[[:digit:]]"
023456789
```

In any case, thanks.

Of course, now that I understand the 'what' (as in "What is it doing?") the 'why' (as in "Why is it doing this?") is bugging me. :P

---

### Post by kidders on 2009-10-21
Yikes... Sorry for the dumb quoting typo. And in a post *about* quoting, of all places!! You're absolutely right.

The "why" is easier to follow if you choose an example other than grep ... say rm, for instance. Suppose you have a file called "*" in your home directory. You would delete it with **rm "/home/`whoami`/*"** ... leaving out the quotes would do something completely different (and more destructive). Without command line argument expansion, one of the commands wouldn't be possible (ie you would either have to give up the ability to delete files called "*", or delete everything in a given directory).

Command line argument expansion allows you to do "for all" type operations that would otherwise be either impossible or extremely tedious. For instance, suppose you wanted to switch off public access to the ~/public_html directories for all users on a web server. You would expect to be able to type **chmod o-rwx /home/*/public_html** and do them all in one go. Conversely, you would not expect the availability of that kind of notation to prevent you from calling a directory "*". Windows, for example, will not let you call a file "C:\", because it has no way of stripping the special meaning from characters like colons & backslashes. Linux has no such restrictions.

Sticking a bit closer to your original example, suppose you wanted to know the types of all the filesystems on partitions of /dev/sda. **for f in /dev/sda[[:digit:]]; do sudo head -c4096 $f | file -; done** would give you the answer, but if argument expansion wasn't available, you'd be hard pressed to find an easy way to do it that would work reliably.

Anyhow, single/double quotes and escape characters (eg backslash) give you pretty flexible control over the special meanings of character sequences like "[[:digit:]]", and allow you to suppress them when you don't want them. For example, both of these do the same thing:```
touch '[[:digit:]]'
touch \[\[:digit:]]
```They update the timestamp of a file called "[[:digit:]]" (creating it if necessary). In the first example, the single quotes remove the special meaning of the "[[:digit:]]" character sequence; in the second, escaping the first two square brackets is enough to strip the special meaning ... there's no need to escape the others (although you could, if you wanted to).

Moving on to grep, you wanted "[[:digit:]]" to be interpreted by the grep utility itself, not the shell it's running in. Unquoted, your argument was expanded before grep was executed, and what it evaluated to was then passed on to grep. By quoting it, you ensure that grep sees the argument as you typed it, (ie you suppress shell expansion).

Anyhow, I'm not sure if *any* of that helps you. Any clearer?

---

### Post by alphaniner on 2009-10-21
That was quite an explanation... iand actually a bit more than I meant to ask.  I understand the value and function of shell expansion pretty well.  My question was more along the lines of "Why do the 'bracketed expandables' behave differently depending on the contents of the directory?"

I think my confusion was due to a lingering mis-belief that the 'be's were being interpreted by **grep** rather than the shell.  But now I fully realize that, it's clear.  Well, almost clear; why does this work: ```
testing@caddywompus:~/foobar$ ls
1
testing@caddywompus:~/foobar$ echo 3253245 | sed sz[[:digit:]]z#zg
#######
```

:P

---

### Post by kidders on 2009-10-21
> **alphaniner said:**
> why does this workIt doesn't work as well as you think, I'd say. You could break it as follows...```
$ echo 3253245 | sed sz[[:digit:]]z#zg
#######
$ touch 'sz8z#zg'
$ echo 3253245 | sed sz[[:digit:]]z#zg
3253245
```Granted, "sz[[:digit:]]z#zg" is a hell of a lot less likely to successfully match any files in practice, but it's still theoretically possible. Unless there's a specific reason for not doing so, sed's arguments should always be enclosed in single quotes. Without them, arguments may even *execute* things, rather than simply failing to result in a substitution (ie dangerous, rather than just irritating).

As you suggested, it all boils down to whether or not you want your environment pre-processing arguments. Imo, it's best to get into the habit of quoting & escaping instinctively ... even when it's clearly unnecessary. That way, if something you type gets expanded, it's because you wanted it to, rather than because of some odd confluence of circumstances (eg just happening to have a file in the current working directory called "1").

---

### Post by alphaniner on 2009-10-22
Yeah, the only reason I didn't use quotes with sed was because I wanted to allow the shell the possibility to expand the [[:digit:]].  I didn't even know if sed could work without the quotes before I tried it.

It took me a while to figure out why it didn't work after creating 'sz8z#zg' #-o but I get it now.  Linux is freakin' amazing.

Thanks for straightening me out.  You not only showed me what I was doing wrong but you managed to teach me why it was wrong.  I really appreciate it.

---

### Post by kidders on 2009-10-22
Hehe... no problem :)

---

