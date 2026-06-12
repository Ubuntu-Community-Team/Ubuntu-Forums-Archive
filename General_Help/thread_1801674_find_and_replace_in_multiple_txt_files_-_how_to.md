---
title: "find and replace in multiple txt files - how to?"
date: 2011-07-10
forum: General Help
---

### Post by Keypel on 2011-07-10
I have around 600 individual *.txt files. What I want to do is find "http" and replace it with "hxxp". 

Can any one give me a command that will do this? 

EDIT

Never mind. Google had tons of info on this. Should have known better. :(

sed -i~ 's/old_string/new_string/g' *.txt

Maybe this thread will be useful to someone else.

---

### Post by Habitual on 2011-07-11
+1 for finding your own solution.
+1 for using Gurgle. 

is "sed -i~" a typo?

---

### Post by Vaphell on 2011-07-11
no, -i~ = replace in place but create backups with ~ suffix

---

### Post by sisco311 on 2011-07-11
> **Vaphell said:**
> no, -i~ = replace in place but create backups with ~ suffix

True, but this definition is a little bit vague and the man page does not reveal much more details.

In GNU and BSD sed,  "sed -i" overwrites the original file with a new one, breaking any links the original may have had.

I would use [ed]("http://en.wikipedia.org/wiki/Ed_(text_editor)") for `in-place' editing of files and [sed]("http://en.wikipedia.org/wiki/Sed") for editing streams.

---

### Post by Keypel on 2011-07-15
My old string is

auth-user-pass 

My new string is

auth-user-pass ./pass.txt

I'm getting errors. Is it because of the space? Is it because of the forward slash?

[error]sed: -e expression #1, char 36: unknown option to `s'[/error]

I'm using

```
sed -i~ 's/auth-user-pass /auth-user-pass ./pass.txt/g' *.txt
```

---

### Post by Keypel on 2011-07-17
bump

---

### Post by sisco311 on 2011-07-17
See:
```
man sed
```
and
```
info sed
```

If you use a forward slash as a delimiter then you have to escape the slashes in the `regexp' and `replacement'
```
sed 's/foo/bar\/oops/g' file
```
or
```
sed 's_foo_bar/oops_g' file
```'

---

### Post by Keypel on 2011-07-17
Thanks for your reply but I didn't understand the man page or your reply.

Is this right:

```
sed -i~ 's/auth-user-pass/auth-user-pass .'s_foo_bar/oops_g'pass.txt/g' *.txt
```

I'm guessing my interpretation of your reply is wrong because the above didn't work.

---

### Post by Vaphell on 2011-07-17
sisco suggested that you either choose another separator of the expression (other than /) so it doesn't collide with / in pattern or escape / belonging to the pattern with \

s[any char]old pattern[the same char]new pattern[the same char]g
eg
s:a/b:c:g
s_a_b/c_g


or s/old[COLOR="Blue"]\/[/COLOR]pattern/new pattern/g

---

### Post by Keypel on 2011-07-17
I'm not grasping what you are trying to tell me. regular expression is difficult for me. I'm sorry, I really want to learn this.

If my old string is 

auth-user-pass 

and I want to replace it with

auth-user-pass ./pass.txt

and the documents I want to change are all *.nfo files..

exactly what is the command I have to type? 

If I could get the exact command, maybe I could understand it.

---

### Post by Vaphell on 2011-07-18
it has nothing to do with regular expressions, but everything with ambiguosity of syntax in your sed parameter.

s/auth-user-pass/auth-user-pass ./pass.txt/g

You defined that / separates functional parts of the parameter (first char after s is assumed to be the one used as a separator, so in your case it's /). Now tell me, how sed is supposed to know which **3** of **4** /'s are the separators and which one belongs to the replacement string? There are 2 possibilities.
If you have / in any of your strings (pattern, replacement) do not use / as a separator, use : or _ or any other symbol that doesn't appear in pattern and replacement. It's that simple.

let's test it with some string and with # as separator of sed parameter
```
$ echo $'auth-user-pass\nabc' | sed 's#auth-user-pass#& ./pass.txt#g'
**auth-user-pass ./pass.txt**
abc
```

yup, it works. & in replacement is the value of matched string (shorter expression)
final sed command
```
sed -i~ 's#auth-user-pass#& ./pass.txt#g' *.nfo
```

---

### Post by nothingspecial on 2011-07-18
See the red slashes

sed 's[COLOR="Red"]/[/COLOR]old[COLOR="Red"]/[/COLOR]new[COLOR="Red"]/[/COLOR]g'

In a sed command they are known as delimiters.

sed will replace what is between the first 2 with what is in between the last 2.

If your text has a / in it, sed will think that is the next delimiter. That is why your command is failing.

You don't have to use a / as the delimiter. You can use a :

So, do 

```
sed 's:old:new:g'
```

instead

---

### Post by Keypel on 2011-07-18
@nothingspecial

Thank You for explaining this in such a way that I could understand. 

Sorry it took so many tries, but I get it now :D

EDIT

I understood nothingspecial example of

sed 's:old:new:g'

So I tried

sed 's:auth-user-pass:auth-user-pass ./pass.txt:g' *.nfo

but nothing changed

So then I tried Vaphell's

sed -i~ 's#auth-user-pass#& ./pass.txt#g' *.nfo

and it worked.

I can see Vaphell used # as the separator but also used a & sign. So thanks for that but why didn't 

sed 's:auth-user-pass:auth-user-pass ./pass.txt:g' *.nfo

work?

---

### Post by sisco311 on 2011-07-18
> **Keypel said:**
> @nothingspecial

Thank You for explaining this in such a way that I could understand. 

Sorry it took so many tries, but I get it now :D

EDIT

I understood nothingspecial example of

sed 's:old:new:g'

So I tried

sed 's:auth-user-pass:auth-user-pass ./pass.txt:g' *.nfo

but nothing changed

So then I tried Vaphell's

sed -i~ 's#auth-user-pass#& ./pass.txt#g' *.nfo

and it worked.

I can see Vaphell used # as the separator but also used a & sign. So thanks for that but why didn't 

sed 's:auth-user-pass:auth-user-pass ./pass.txt:g' *.nfo

work?

By default, sed prints its output to [stdout]("http://en.wikipedia.org/wiki/Standard_streams"); Yet another technical term, let's just say it prints its output in the terminal window or more precisely in the text terminal.

In GNU and BSD sed you can use the -i flag to edit the file in place. Well, actually "sed -i" overwrites the original file with a new one, but that's another story. :)

The syntax of sed's s command is:
```
s[color=red]c[/color]regexp[color=red]c[/color]replacement[color=red]c[/color]
```

Where:
s (substitute) - is the command. It tries to replace each portion matched by regexp with replacement.

[color=red]c[/color] - is the delimiter. It separates the command (s), regexp and replacement from each other. If the regexp or the replacement contains a delimiter character, then you have to escape it with a `\' (without the quotes) otherwise the expression becomes ambiguous. But, I think, you understand this. 

regexp - is a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression") 

replacement - is a string. Each portion matched by regexp is replaced with it. It may contain the special character `&' (without the quotes) to refer to that portion of the pattern space  which  matched. For example, if you want to replace foo with foobar you can use 's/foo/&bar/' because `&' will be replaced with foo.

So, Vaphell's command edits the file `in place' (and creates a backup of the original file called filename.nfo~ ), while the command posted by  nothingspecial will print the output of sed to stdout.

PS: I know all this technical terms may sound confusing. But you will be surprised, how fast you can find an answer to your questions (either by reading the man pages or by a quick google search) if you learn them. ;)

HTH

---

### Post by Keypel on 2011-07-19
@sisco311

Thank You for all the time and effort you put into explaining this for me.

---

### Post by sisco311 on 2011-07-19
No problem.

---

