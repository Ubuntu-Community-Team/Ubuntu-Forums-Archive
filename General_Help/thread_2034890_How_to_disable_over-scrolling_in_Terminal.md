---
title: "How to disable over-scrolling in Terminal"
date: 2012-07-29
forum: General Help
---

### Post by Kols on 2012-07-29
Hi!

This may be a stupid question, and already answered, but after duckduckgo'ing it, and searching in these forums, I still couldn't find it.

When I run certain commands, the output presents a long list. Sometimes, when the list exceeds the bottom of the terminal window, that information is no longer visible. This is very annoying, especially when I'm using aircrack - vital information is lost at the bottom of the window.

tl;dr information is lost at the bottom of the terminal window when a command outputs a lot of information.

Is there a way around this?

Kols

---

### Post by vasa1 on 2012-07-29
A way around would be to pipe the output to a file instead of to the screen.

---

### Post by Kols on 2012-07-29
> **vasa1 said:**
> A way around would be to pipe the output to a file instead of to the screen.

That sounded pretty smart. Will the output continue to write to the file, or will it write only the immediate output?

Also, how to pipe the output to a file? I'm thinking it may be something like

airmon-ng | /folder/file.txt

---

### Post by GreatDanton on 2012-07-29
Take a look at this: [http://en.wikipedia.org/wiki/Redirection_(computing](http://en.wikipedia.org/wiki/Redirection_(computing))

---

### Post by vasa1 on 2012-07-29
> **Kols said:**
> That sounded pretty smart. Will the output continue to write to the file, or will it write only the immediate output?

Also, how to pipe the output to a file? I'm thinking it may be something like

airmon-ng | /folder/file.txt

As suggested by Great Danton, you could look at redirecting:
REDIRECTION with > and >>
> redirects output to a file. If the file already exists, it is overwritten.
>> doesn't overwrite but appends to an existing file (after creating it if need be).

So, it would be something like:
command_name (and what ever arguments are needed) > outputfile
would write the output to a file called outputfile in your home directory or you can specify a path. If you use >> you'll be appending to the same file.

---

### Post by Kols on 2012-07-29
> **GreatDanton said:**
> Take a look at this: [http://en.wikipedia.org/wiki/Redirection_(computing](http://en.wikipedia.org/wiki/Redirection_(computing))

Thanks for the link!

Well, to test it out, I did f

ree -m > /home/user/free.txt

which created a nice textfile with the output. I also tried >> to append with the same command, worked fine.

I notice though, that like I asked earlier, the output in the textfile, is only the immediate output - it doesn't continue writing to the file, which is kinda what I need it to do. How to do that?

Also, I tried using this command

airodump-ng eth1 > /home/user/airodump.txt

the result was that the command created a textfile airodump.txt, but the output was still only sent to the screen. Has this to do with the program itself?

---

### Post by steeldriver on 2012-07-29
The > and >> symbols only redirect the standard output stream (aka 'stdout') - if the program writes messages to the standard error stream ('stderr') as well then those will still appear in the terminal

You can redirect both stdout and stderr to file.txt using:

```
command [options] > file.txt 2>&1 
```which uses the *file descriptors* 1 (stdout) and 2 (stderr); or (in newer versions of bash) the shorthand

```
command [options] &> file.txt
```Alternatively you could *pipe* the output to a filter command such as 'less' which will buffer and paginate it for you:

```
command [options] | less 
```(to pipe just stdout) or

```
command [options] 2>&1 | less 
```to pipe both stdout and stderr (old style) or

```
command [options] |& less 
``` (new style)

Finally, you could look at the options for the command and notice that it already has an option to write to a dumpfile:

```

$ man airodump-ng
.
.
.

-w <prefix>, --write <prefix> Is the dump file prefix to use. 

If this option is not given, it will only show data on the screen. 
.
.
.

```

---

### Post by Kols on 2012-07-30
> **steeldriver said:**
> The > and >> symbols only redirect the standard output stream (aka 'stdout') - if the program writes messages to the standard error stream ('stderr') as well then those will still appear in the terminal

You can redirect both stdout and stderr to file.txt using:

```
command [options] > file.txt 2>&1 
```which uses the *file descriptors* 1 (stdout) and 2 (stderr); or (in newer versions of bash) the shorthand

```
command [options] &> file.txt
```Alternatively you could *pipe* the output to a filter command such as 'less' which will buffer and paginate it for you:

```
command [options] | less 
```(to pipe just stdout) or

```
command [options] 2>&1 | less 
```to pipe both stdout and stderr (old style) or

```
command [options] |& less 
``` (new style)

Finally, you could look at the options for the command and notice that it already has an option to write to a dumpfile:

```

$ man airodump-ng
.
.
.

-w <prefix>, --write <prefix> Is the dump file prefix to use. 

If this option is not given, it will only show data on the screen. 
.
.
.

```

What can I say, other than a big ol' thank you, for such a detailed and easy description on how to do it. 
So thanks a lot!

---

### Post by steeldriver on 2012-07-30
You're welcome - often in Unix/Linux there's more than one way to do things, it just takes a bit of practice to figure out which way is best for a particular situation :)

---

