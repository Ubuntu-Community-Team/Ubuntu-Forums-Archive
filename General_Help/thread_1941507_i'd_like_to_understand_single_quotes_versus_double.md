---
title: "i'd like to understand single quotes versus double quotes in shell script"
date: 2012-03-15
forum: General Help
---

### Post by Cs0hu on 2012-03-15
i've been experimenting with shell script to make my life a little lazier and its pretty overwhelming. Last one is a script to put in $HOME/.gnome2/nautilus-scripts so it can be accessed from the menu
it's very simple and it does what i need it to do but i'd like to understand something
transcript :
```
#!/bin/bash

filelist=$NAUTILUS_SCRIPT_SELECTED_URIS

[COLOR=Green]#script needed editing because it didn't decode all special characters
[/COLOR][COLOR=Green]#replace % with \x so echo -e decodes [/COLOR]
[COLOR=Green]filelistt=$(echo $filelistt | sed 's/file:\/\/// ' | sed 's/\%/\\x/g') 
filelistt=$(echo -e $filelistt)
[/COLOR]

#single quotes needed here?
#gnome-terminal --command="shred -vfu '$filelist'"

#double quotes needed here ???!?
shred -fu "$filelist"

```when i use the shred command via gnome-terminal i need to enclose the variable in single quotes (in case the filename contains a whitespace, otherwise shred reads it as two different filenames)

when i use it as is however nothing seems to happen if i use single quotes but it works when i use double quotes. All is fine and it works, but if someone could explain to me why it might save me a little frustration later on

much obliged

---

### Post by cortman on 2012-03-15
As I recall in bash single quotes quote out all metacharacters within the quotes, whereas double quotes quote out all except a few- in other words, a few metacharacters retain their special meaning even when within double quotes.
Have you tried the last command with no quotes at all?

---

### Post by Vaphell on 2012-03-15
general idea is that single quotes are as literal as it gets, while double quotes perform expansion of variables if there are any. In terms of whitespaces in literal strings they work in the same way (as in don't allow for splitting).

```
$ x="a b c"; echo '$x' [COLOR="Blue"]"$x"[/COLOR] [COLOR="Green"]"xyz '$x'"[/COLOR] '"$x"' **"xyz \"$x\""**
$x [COLOR="Blue"]a b c[/COLOR] [COLOR="Green"]xyz 'a b c'[/COLOR] "$x" **xyz "a b c"**
```

your example:
[COLOR="Green"]first line[/COLOR] is about having 2 pairs of quotes, because each time you want to pass a string of command to execute to another program you need to remember that parameter evaluation will strip outer ones. This happens with every passing through a program, so you need to use as many layers of quotes as required which requires tons of fugly escaping if you do this hardcore.
Terminal sees outer double quotes (inner single quotes are treated as ordinary chars), expands $filelist with its actual value -> inside terminal you get [COLOR="Green"]shred 'actual file name'[/COLOR]. Double or single quotes in the inner layer - no difference here in terms of whitespace preservation, but single quotes don't require escaping so are cleaner/more convenient (double quotes would require escaping not to be misinterpreted to be on the outer layer - as shown in last example).
[COLOR="Blue"]Second line[/COLOR] is straightforward double quote with parameter substitution.

---

### Post by Cs0hu on 2012-03-18
> **cortman said:**
> As I recall in bash single quotes quote out all metacharacters within the quotes, whereas double quotes quote out all except a few- in other words, a few metacharacters retain their special meaning even when within double quotes.
Have you tried the last command with no quotes at all?
Yes, the last command works only with double quotes, but only needed when white space is present in the filename it seems

---

### Post by SeijiSensei on 2012-03-18
No, it isn't because of the whitespace, but because "$filelist" replaces the variable $filelist with its contents.  The syntax '$filelist' returns the literal string $filelist, not its contents.

```

$test='This is a test'
echo "$test"
echo '$test'

```

The first echo command prints "This is a test" to the screen; the second prints "$test".

However if the filenames have embedded spaces you either need to "escape" them with the backslash or put the filename in quotes.  If you have a file named "my file.txt" then all of these are equivalent:

```

cp my\ file.txt anotherfile.txt
cp 'my file.txt' anotherfile.txt
cp "my file.txt" anotherfile.txt

```

---

