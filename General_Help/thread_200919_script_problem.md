---
title: "script problem"
date: 2006-06-21
forum: General Help
---

### Post by maka on 2006-06-21
Hi, im trying to write a script where it runs some commands if a certain program is not running.

can anyone tell me how to do that?

thanks.

---

### Post by IYY on 2006-06-21
Something like this, maybe...

```
psname="someprocess"
if [ `ps aux | grep "$psname | grep -vq "grep $psname"` ]
then
       #run your command
fi
```

This will also work, but might write something to stdout:

```
psname="someprocess"
if [ `pgrep $psname"` ]
then
       #run your command
fi
```

---

### Post by tonyr on 2006-06-21
What scripting language?  Sh? Bash?  Csh? Perl?  Python? (etc etc etc...)

In general, capture the output of **ps aux**, which produces a list of all
running processes, and scan it for the target program name.  The exact syntax
for doing this depends on your scripting language.

EDIT: Well, I guess I came in second.

---

### Post by maka on 2006-06-21
[QUOTE=IYY]Something like this, maybe...

```
psname="someprocess"
if [ `ps aux | grep "$psname | grep -vq "grep $psname"` ]
then
       #run your command
fi
```

This will also work, but might write something to stdout:

```
psname="someprocess"
if [ `pgrep $psname"` ]
then
       #run your command
fi
```[/QUOTE]


thanks for thehelp. one problem.. when i try to run this script it gives me this error:

"too many arguments"
on this line:
```
  if [ `ps aux | grep "$psname" | grep -v "grep $psname"` ]
```

i took off the -q option because nothing showed up with the -q there.  maybe thats the problem?

---

### Post by tonyr on 2006-06-21
[QUOTE=maka]thanks for thehelp. one problem.. when i try to run this script it gives me this error:

"too many arguments"
on this line:
```
  if [ `ps aux | grep "$psname" | grep -v "grep $psname"` ]
```

i took off the -q option because nothing showed up with the -q there.  maybe thats the problem?[/QUOTE]

You are correct to remove the **q**, but that is not the whole solution.
Change the line to this:
```

if [ `ps aux | grep "$psname" | grep -v "grep $psname" | wc -m` = '0' ]

```

I'll post an explanation if you wish.

---

### Post by maka on 2006-06-21
[QUOTE=tonyr]You are correct to remove the **q**, but that is not the whole solution.
Change the line to this:
```

if [ `ps aux | grep "$psname" | grep -v "grep $psname" | wc -m` = '0' ]

```

I'll post an explanation if you wish.[/QUOTE]

it works! =D> yeah if you can post an explanation, that'd be great

---

### Post by IYY on 2006-06-21
You can keep the q, by the way. You don't need any output. The reason it didn't work before (sorry, untested) is because the 'if' thing just does comparissons, and woouldn't actually consider 0 to be 'true'. So, you check if the output is 0 (successful execution) and if so, launch your command.

---

### Post by maka on 2006-06-21
[QUOTE=IYY]You can keep the q, by the way. You don't need any output. The reason it didn't work before (sorry, untested) is because the 'if' thing just does comparissons, and woouldn't actually consider 0 to be 'true'. So, you check if the output is 0 (successful execution) and if so, launch your command.[/QUOTE]

oh ok. thanks for the help guys. :D

---

### Post by tonyr on 2006-06-21
[QUOTE=maka]it works! =D> yeah if you can post an explanation, that'd be great[/QUOTE]

Here ya go...

I'm going to give a short version and then a long version. 
I'm not sure at what level to pitch the long version, so forgive me if it
covers things you already know.

**THE SHORT VERSION**
```

**`ps aux | grep "$psname" | grep -vq "grep $psame"`** produces NO OUTPUT 
at all, because
the **-q** option means exactly that: silent mode, or "produce no output"

The back ticks surrounding that piped sequence mean "replace this quoted 
command with its output result".  Without the **-q**, it is possible for the 
output to be LARGE. bash does not like LARGE things in an **if [ <condition> ]** 
statement.

`ps aux | grep "$psname" | grep -vq "grep $psame | **wc -m**`  
The added **wc -m** command says "count the characters in the final output".
If the target process name is present, the count will be a number 
greater than zero; if it is absent, the count will be zero.

if [ `ps aux | grep "$psname" | grep -v "grep $psname" | wc -m` = '0' ]

The if statement can be interpreted like this:
if [ number-of-characters-in-search-result = 0 ]
then process is absent
else process is present

```

**THE LONG VERSION**
```

[CODE]
if [ `ps aux | grep "$psname" | grep -v "grep $psname" | wc -m` = '0' ]

```

**ps aux** produces a list of all of the running processes with some
other information: process ID, user ID, memory size etc.  

**grep "$psname"** looks for the target process name (the one you are
interested in) in the output of **ps aux**.  That's what the '**|**' 
character between **ps aux** and **grep "$psname"** is for.

**grep -v "grep $psname"** does a 'negative' search on the output
of **grep "$psname"**.  It's, like, "print out every line with my program
name that **doesn't** have **grep** in it".  We are doing that
because in this arrangement of commands, the process "grep $psname"
could possibly still be running, and we want to ignore it, since the goal
of this exercise to to show that the total search turned up nothing.

Now things get a little more complicated.  I'm sure that **IYY** intended
for the result of
**`ps aux | grep "$psname" | grep -vq "grep $psname"`**
to be something that could be tested for a TRUE/FALSE result.  The
single quotes around that whole thing mean "do this command thing here
and replace the quoted thing with the result so that the rest of the 
enlosing expression can use it".  The single quote things are actually 
backward single quotes or 'back ticks', and have that special meaning in 
**bash** syntax (and other shells, too).  

In this case the rest of the enclosing expression is **if [ <something> ]**,
and there are rules in **bash** that apply to what happens when the 
<something> is actually several somethings.  

Now,  "the result" of that command string in the **if** statement has two
interpretations.  One is "what was the output af all of this", and the 
other is "did this thing work  at all or did something go wrong".  The first 
interpretation should be pretty  obvious: either it produced some output or 
it didn't.  The second  one is reported  by **bash** as a **completion status** 
which shows up as a number in a **bash** shell variable.  A **completion status** 
of zero usually  means **success**. I'm not sure which  one of these  
interpretations **IYY** was expecting, since how things are interpreted  
as TRUE/FALSE varies widely.   For example, sometimes, in some scripting 
languages,  empty strings can be  interpreted as FALSE.  I'm not sure what 
**bash** does about  this.

The **bash** way to run a command and capture the **completion status** value
is to use the built-in keyword **command**.  You can look that up in **man bash** 
or a bash manual somewhere.  I think it is intended to be used with single 
command expressions.  I don't know how **bash** treats **completion status** 
in a piped sequence (oh, yeah, that '|' character is called pipe, and the 
command thing inside the back quotes can be called a **pipe sequence** or 
**piped sequence**).

That's not what the original piped sequence does.  It follows the first 
interpretation and produces whatever the final output of all of those 
commands is.  That's where the  **q** in **-vq** comes into play.  
The **-q** option to **grep** (see **man grep**) means "don't  
produce any printed output at all", with the intention 
that the **completion status** is all that is of interest.  That means that 
no matter what the command sequence does, NOTHING is produced as 
output and that is exactly what you saw.  
When you took out the **-q**, a WHOLE LOT of 
something was produced.  That's where the rules of **if [ <something> ]** 
kick in.    If there are too many things in <something>, **bash** doesn't like 
it and complains.  You saw that, too.  
**man bash** gives rules of interpretation for the number of 
things in <something> for 1, 2, 3, 4, and  5-or-more things.  
It is the 5-or-more that causes problems.

So what did I do?  I added another command to the end of the piped sequence, 
**wc**, which means **word count**.  It can produce a result of number of 
lines, words, or characters, or all three.  I used the **-m** argument which 
means "number of characters only, please". 

Oh, and I left the -q out so that SOMETHING would be produced if it 
were possible to produce any output.  The use of **wc** says 
"Were there ANY characters in the output", and the actual answer is 
either zero, which is printed out, or some number greater than zero.   
Then I modified the **if [ <something> ]** statement to be 
**if [ <something> = '0' ]**, a conditional comparison producing a 
TRUE/FALSE result, expecting that the result of <something> would 
be the number of characters in the final output.
[/CODE]

---

### Post by maka on 2006-06-26
> **tonyr]Here ya go...

I'm going to give a short version and then a long version. 
I'm not sure at what level to pitch the long version, so forgive me if it
covers things you already know.

**THE SHORT VERSION**
```

**`ps aux | grep "$psname" | grep -vq "grep $psame"`** produces NO OUTPUT 
at all, because
the **-q** option means exactly that: silent mode, or "produce no output"

The back ticks surrounding that piped sequence mean "replace this quoted 
command with its output result".  Without the **-q**, it is possible for the 
output to be LARGE. bash does not like LARGE things in an **if [ <condition> ]** 
statement.

`ps aux | grep "$psname" | grep -vq "grep $psame | **wc -m**`  
The added **wc -m** command says "count the characters in the final output".
If the target process name is present, the count will be a number 
greater than zero said:**
> 

The if statement can be interpreted like this:
if [ number-of-characters-in-search-result = 0 ]
then process is absent
else process is present

```

**THE LONG VERSION**
```

[CODE]
if [ `ps aux | grep "$psname" | grep -v "grep $psname" | wc -m` = '0' ]

```

**ps aux** produces a list of all of the running processes with some
other information: process ID, user ID, memory size etc.  

**grep "$psname"** looks for the target process name (the one you are
interested in) in the output of **ps aux**.  That's what the '**|**' 
character between **ps aux** and **grep "$psname"** is for.

**grep -v "grep $psname"** does a 'negative' search on the output
of **grep "$psname"**.  It's, like, "print out every line with my program
name that **doesn't** have **grep** in it".  We are doing that
because in this arrangement of commands, the process "grep $psname"
could possibly still be running, and we want to ignore it, since the goal
of this exercise to to show that the total search turned up nothing.

Now things get a little more complicated.  I'm sure that **IYY** intended
for the result of
**`ps aux | grep "$psname" | grep -vq "grep $psname"`**
to be something that could be tested for a TRUE/FALSE result.  The
single quotes around that whole thing mean "do this command thing here
and replace the quoted thing with the result so that the rest of the 
enlosing expression can use it".  The single quote things are actually 
backward single quotes or 'back ticks', and have that special meaning in 
**bash** syntax (and other shells, too).  

In this case the rest of the enclosing expression is **if [ <something> ]**,
and there are rules in **bash** that apply to what happens when the 
<something> is actually several somethings.  

Now,  "the result" of that command string in the **if** statement has two
interpretations.  One is "what was the output af all of this", and the 
other is "did this thing work  at all or did something go wrong".  The first 
interpretation should be pretty  obvious: either it produced some output or 
it didn't.  The second  one is reported  by **bash** as a **completion status** 
which shows up as a number in a **bash** shell variable.  A **completion status** 
of zero usually  means **success**. I'm not sure which  one of these  
interpretations **IYY** was expecting, since how things are interpreted  
as TRUE/FALSE varies widely.   For example, sometimes, in some scripting 
languages,  empty strings can be  interpreted as FALSE.  I'm not sure what 
**bash** does about  this.

The **bash** way to run a command and capture the **completion status** value
is to use the built-in keyword **command**.  You can look that up in **man bash** 
or a bash manual somewhere.  I think it is intended to be used with single 
command expressions.  I don't know how **bash** treats **completion status** 
in a piped sequence (oh, yeah, that '|' character is called pipe, and the 
command thing inside the back quotes can be called a **pipe sequence** or 
**piped sequence**).

That's not what the original piped sequence does.  It follows the first 
interpretation and produces whatever the final output of all of those 
commands is.  That's where the  **q** in **-vq** comes into play.  
The **-q** option to **grep** (see **man grep**) means "don't  
produce any printed output at all", with the intention 
that the **completion status** is all that is of interest.  That means that 
no matter what the command sequence does, NOTHING is produced as 
output and that is exactly what you saw.  
When you took out the **-q**, a WHOLE LOT of 
something was produced.  That's where the rules of **if [ <something> ]** 
kick in.    If there are too many things in <something>, **bash** doesn't like 
it and complains.  You saw that, too.  
**man bash** gives rules of interpretation for the number of 
things in <something> for 1, 2, 3, 4, and  5-or-more things.  
It is the 5-or-more that causes problems.

So what did I do?  I added another command to the end of the piped sequence, 
**wc**, which means **word count**.  It can produce a result of number of 
lines, words, or characters, or all three.  I used the **-m** argument which 
means "number of characters only, please". 

Oh, and I left the -q out so that SOMETHING would be produced if it 
were possible to produce any output.  The use of **wc** says 
"Were there ANY characters in the output", and the actual answer is 
either zero, which is printed out, or some number greater than zero.   
Then I modified the **if [ <something> ]** statement to be 
**if [ <something> = '0' ]**, a conditional comparison producing a 
TRUE/FALSE result, expecting that the result of <something> would 
be the number of characters in the final output.
[/CODE]


thanksman.  it makes sense now! :cool:

---

