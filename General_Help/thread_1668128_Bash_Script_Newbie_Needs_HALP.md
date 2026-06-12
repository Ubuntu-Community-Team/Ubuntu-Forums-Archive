---
title: "Bash Script Newbie Needs HALP"
date: 2011-01-15
forum: General Help
---

### Post by [Shadow] on 2011-01-15
```
#!/bin/bash
set +x
#Script that helps meh create bash files
#****************VARIABLES***********
$filename = $1
#****************FUNCTIONS***********
function createscript
{
echo "#!/bin/bash \n #" > $filename
$(chmod 755 $filename)
$(nano $filename)
exit
}

#****************MAIN*****************
if [ "$1" != "" ]; then
if [ -f $1 ]; then
        echo "That filename already exists"
        exit
else
        echo "Create script using filename $1?"
        createscript
fi
```Hey I am pretty new to Bash and unix. Im trying to get better at it and learn how to write some scripts. Can i get some tips as to why this is not working and whether or not I am approaching this in the right manner? I'm running 10.04LTS if that makes a difference

P.S. Exits with these errors

```
$ bashscript test
/usr/local/bin/bashscript: line 5: =: command not found
Create script using filename test?
/usr/local/bin/bashscript: line 9: $filename: ambiguous redirect
chmod: missing operand after `755'
Try `chmod --help' for more information.

```

---

### Post by garyed on 2011-01-15
I'm not much on scripting either but I think its the function that doesn't like the variable. Try this without the function:

```

if [ "$1" != "" ]; then
if [ -f $1 ]; then
        echo "That filename already exists"
        exit
else
        echo "Create script using filename $1?"
        echo "#!/bin/bash" >$1
        chmod 755 $1
nano $1
fi
fi

```

---

### Post by efflandt on 2011-01-16
You had:

[LIST=1]
[*]Wrong syntax for setting variable (no spaces and do not use $ on variable being set).
[*]You were missing a **fi** for an **if** block.
[*]Not sure what **set +x** is for, so I commented it out.
[*]echo for populating file needs **-e** to expand escaped characters.
[*]Not sure why you wrapped commands with **$()**, because then nano did not work properly.
[/LIST]
This works:
```
#!/bin/bash
#set +x
#Script that helps me create bash files
#****************VARIABLES***********
filename=$1
#****************FUNCTIONS***********
function createscript
{
echo -e "#!/bin/bash\n#" > $filename
chmod 755 $filename
nano $filename
exit
}

#****************MAIN*****************
if [ "$1" != "" ]; then
    if [ -f $1 ]; then
        echo "That filename already exists"
        exit
    else
        echo "Create script using filename $1"
        createscript
    fi
fi
```Note: When you test this, do not call the created file "test" because that is a reserved word in bash and will not execute a script called test (test1, etc, is ok).

---

### Post by [Shadow] on 2011-01-16
Thanks for all the help guys. Sorry about the newbie mistakes. 

> **efflandt said:**
> You had:

[LIST=1]
[*]Wrong syntax for setting variable (no spaces and do not use $ on variable being set).
[*]You were missing a **fi** for an **if** block.
[*]Not sure what **set +x** is for, so I commented it out.
[*]echo for populating file needs **-e** to expand escaped characters.
[*]Not sure why you wrapped commands with **$()**, because then nano did not work properly.
[*]
[/LIST]
1. Could i get a quick reminder as to when you need a $ or not when setting variables?
2. Whoops my bad :D
3. I was setting it to -x for debugging but i turned it off because it didnt help much
4. what are escaped characters and when do i need the -e (besides now)
5.  I was wrapping commands in $() because i read something like that in a guide im working through... 

Thanks for the help. Sorry for the Horrible coding

---

### Post by Crusty Old Fart on 2011-01-16
In my opinion, you would be well served by having a good book that you could read, study, and use as a reference.

You can download a very good one for free from the following link:

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Have fun.

---

### Post by [Shadow] on 2011-01-16
> **Crusty Old Fart said:**
> In my opinion, you would be well served by having a good book that you could read, study, and use as a reference.

You can download a very good one for free from the following link:

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Have fun.


what a small world. That is the exact one I am learning off of. Not well though as you can tell

---

### Post by Vaphell on 2011-01-16
with variables and dollar signs its easy
var=value to assign (without $ when followed by =), but $var or ${var} to use the value (with $ everywhere else)


some characters have a special meaning
examples:
- spaces are a neverending story in scripting.
let's say you want to run
```
some_player file with spaces in filename.mp3
```
it will fail spectacularly because spaces separate parameters. The command will think there are actually 5 params 'file' 'with' 'spaces' 'in' 'filename.mp3'
to succeed you need to put the name in "" or to escape spaces with \ ( \=next char is a normal sign with no additional meaning)
```
some_player "file with spaces in filename.mp3"
some_player file\ with\ spaces\ in\ filename.mp3
```

> is a redirection for many commands so if you want to actually print the > sign you need to do the same ("" or \)
" or ', parentheses, curly braces - same thing



wrapping commands is usually done so you can store the output of a command in a variable to play with it later, e.g.
output=$(ls)
or to iterate over the output of the command
for a in $(ls)
or to use the output as parameters for another command
prog1 $(prog2)

when you simply want to run some command, no strings attached, you don't need to do $()

---

### Post by efflandt on 2011-01-16
> **'[Shadow] said:**
> 1. Could i get a quick reminder as to when you need a $ or not when setting variables?
2. Whoops my bad :D
3. I was setting it to -x for debugging but i turned it off because it didnt help much
4. what are escaped characters and when do i need the -e (besides now)
5.  I was wrapping commands in $() because i read something like that in a guide im working through... 
1, In the shell when you assign a variable you do not use $ on the variable being assigned to.  You only use the $ when using the value of the variable (what has already been assigned to it).  That is different from Perl scripts where you also use $ when assigning variables.
3. I thought maybe the **set +x** was responsible for my prompt (PS1) going inverse.  But something else must have caused that while experimenting, because +x (off) is actually the default unless previously using -x.
4. If you want backslashed escape sequences like \n to be interpreted as a newline for echo instead of literally "\n", you would need to use echo -e.  For example note the difference in output for following (\t is tab):

```
**echo "Hello\n\tWorld"**
Hello\n\tWorld

**echo -e "Hello\n\tWorld"**
Hello
    World
```5. $() or ` ` (backticks) would be if you want to assign the return value of a command to a variable or evaluate it, but that seemed to interfere with interactive use of nano.  You do not need that for command lines in a script that you just want to execute.

I did a lot of Perl scripting years ago for CGI scripts, but am no shell script expert.  So sometimes it takes some experimentation for things to come out right.  **man bash** is a rather large man page and some of it may seem obscure without actual examples or some testing.

---

### Post by Crusty Old Fart on 2011-01-16
> **'[Shadow] said:**
> what a small world. That is the exact one I am learning off of. Not well though as you can tell

Okay...maybe I can add to the confusion :cool: by trying to answer a few of your earlier questions.
> **'[Shadow] said:**
> 
1. Could i get a quick reminder as to when you need a $ or not when setting variables?When you set a variable, you _never_ use a $ on the left side of an equal sign. Think of the equal sign as _storing a value_ in a variable, and the $ as _retrieving the stored value_ from a variable (a.k.a.: parameter expansion). Perhaps some illustration will help:
```

var=one 
echo var = $var

***[COLOR=Red]~~~ output: ~~~[/COLOR]***
var = one

```And just to take it a little further:
```

one=1
varA=one
varB=$one
echo one = $one, varA = $varA, varB = $varB

***[COLOR=Red]~~~ output: ~~~[/COLOR]***
one = 1, varA = one, varB = 1

```> **'[Shadow] said:**
> 
4. what are escaped characters and when do i need the -e (besides now)
Escaped characters in the echo command are those preceded by a backslash \
For example: the newline character: n must be escaped to be evaluated rather than interpreted as a literal n. So, to make n be evaluated as a newline, it must be escaped like this: \n. Whenever you use escape characters in an echo command, you need to use the -e option. There are several other commands that use the -e option, but it has different meanings in different commands. The man pages will tell you what the options do for the command you're wanting to use.

Suppose, in the example from the code box above, we wanted to print each of our variables on it's own line, using one echo command. For this, we would use escape characters for newlines, enclose the text in "", and would need the -e option in the echo command as follows:
```

one=1
varA=one
varB=$one
echo "one = $one\nvarA = $varA\nvarB = $varB" #<--incorrect
echo -e one = $one\nvarA = $varA\nvarB = $varB #<--incorrect
echo -e "one = $one\nvarA = $varA\nvarB = $varB" #<--correct

***[COLOR=Red]~~~ output: ~~~[/COLOR]***
one = 1\nvarA = one\nvarB = 1
one = 1nvarA = onenvarB = 1
one = 1
varA = one
varB = 1


```> **'[Shadow] said:**
> 
5.  I was wrapping commands in $() because i read something like that in a guide im working through... It seems that most of the difficulty you're having with this is due to some confusion over how expansion is done, whether it's parameter expansion, or command substitution. See chapters 8 and 35 of your book.

---

### Post by [Shadow] on 2011-01-19
Thanks guys. All of you were so helpful. I definitely had quite a few aha! and of course! moments. Thanks for all your insight!

---

