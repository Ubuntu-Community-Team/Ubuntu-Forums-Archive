---
title: "Help with Bash script that edits file"
date: 2011-04-24
forum: General Help
---

### Post by trewsdan on 2011-04-24
Hi,

I'm looking for help with a bash script that edits a file.

There's a file with lines in this format:

Name1 [Tab] Eyes1 [Tab] Ears1
Name2 [Tab] Eyes2 [Tab] Ears2
Name3 [Tab] Eyes3 [Tab] Ears3
...

I'm trying to make a bash script that accepts two args - ALL_EYES and ALL_EARS - and sets all the 'Eyes' in the file to $ALL_EYES and all the 'Ears' in the file to all ALL_EARS.

Something like:

#!/bin/bash

ALL_EYES="$1"
ALL_EARS="$2"

# commands here that update the file.


Ideas?  Thanks.

:)

---

### Post by trewsdan on 2011-04-24
For each line, I want to replace whatever is between the tabs with ALL_EYES, and replace everything after the second tab with ALL_EARS.

Would appreciate your help.  Thanks.

---

### Post by Telengard C64 on 2011-04-24
[3.5.3 Shell Parameter Expansion - Bash Reference Manual](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion)

```
foo$ cat file_name
Name1 [Tab] Eyes1 [Tab] Ears1
Name2 [Tab] Eyes2 [Tab] Ears2
Name3 [Tab] Eyes3 [Tab] Ears3
foo$ cat eyesnears
#!/bin/bash

ALL_EYES="$1"
ALL_EARS="$2"

while read -r
do
  line="${REPLY//Eyes/$ALL_EYES}"
  echo "${line//Ears/$ALL_EARS}"
done < file_name
foo$ ./eyesnears heads toes
Name1 [Tab] heads1 [Tab] toes1
Name2 [Tab] heads2 [Tab] toes2
Name3 [Tab] heads3 [Tab] toes3
foo$
```

**_Edit_**
It might be better to generalize this just a little bit so that the input file name is not hard coded into the script.

```
foo$ cat eyesnears
#!/bin/bash

ALL_EYES="$1"
ALL_EARS="$2"

while read -r
do
  line="${REPLY//Eyes/$ALL_EYES}"
  echo "${line//Ears/$ALL_EARS}"
done
foo$ ./eyesnears oranges apples <file_name >new_file
foo$ cat new_file
Name1 [Tab] oranges1 [Tab] apples1
Name2 [Tab] oranges2 [Tab] apples2
Name3 [Tab] oranges3 [Tab] apples3
foo$
```

---

### Post by Telengard C64 on 2011-04-24
> **trewsdan said:**
> For each line, I want to replace whatever is between the tabs with ALL_EYES, and replace everything after the second tab with ALL_EARS.

How about you show us your real input data and an example of your expected output? Try this with your input file.

```
head input_file | od -A n -a
```

Replace **input_file** with the name of your real file. Post the output of the command into a code block. This will provide an unambiguous representation of your real input data.

Then show us what you would expect the output of the script to be given any particular value for **$1** and **$2**.

HTH

---

### Post by trewsdan on 2011-04-24
Thanks C64.  I can use a lot of that.  I'd like to match based on the tabs though because it's kinda random what can be between them.  Good idea on the example input and output.  The whitespace between the columns is tabs.


```
[wim@wimdb2 test]$ cat input
John:   Blue    Large
Jim:    Green   Small
Kathy:  Grey    Medium

[wim@wimdb2 test]$ ./eyesnears "Brown" "Large earlobes" <input >output

[wim@wimdb2 test]$ cat output
John:   Brown   Large earlobes
Jim:    Brown   Large earlobes
Kathy:  Brown   Large earlobes
```

---

### Post by Telengard C64 on 2011-04-24
Usually when performing complex manipulations it is better to turn to a specialized language such as AWK. In this case though, Bash has everything needed, so I don't see any reason not to use it.

Here's the new script. I believe it does all that you ask.

```
foo$ cat ./eyesnears
#!/bin/bash

ALL_EYES="$1"
ALL_EARS="$2"

while read -r
do
    echo "${REPLY/$'\t'*$'\t'*/$'\t'$ALL_EYES$'\t'$ALL_EARS}"
done
```

Here's an example run using the input data file [you specified](http://ubuntuforums.org/showpost.php?p=10714790&postcount=5).

```
foo$ ./eyesnears "Brown" "Large earlobes" <input_file >output_file
foo$ cat output_file
John:   Brown   Large earlobes
Jim:    Brown   Large earlobes
Kathy:  Brown   Large earlobes
```

Here's the disambiguated contents of the **output_file**.

```
foo$ od -A n -a output_file
   J   o   h   n   :  ht   B   r   o   w   n  ht   L   a   r   g
   e  sp   e   a   r   l   o   b   e   s  nl   J   i   m   :  ht
   B   r   o   w   n  ht   L   a   r   g   e  sp   e   a   r   l
   o   b   e   s  nl   K   a   t   h   y   :  ht   B   r   o   w
   n  ht   L   a   r   g   e  sp   e   a   r   l   o   b   e   s
  nl
```

HTH

**_Edit_**
Here's a list of links to the relevant sections of the [Bash Reference Manual](http://www.gnu.org/software/bash/manual/html_node/index.html) for everything I just did.

[list]
[*]**#!/bin/bash** - [3.8 Shell Scripts](http://www.gnu.org/software/bash/manual/html_node/Shell-Scripts.html#Shell-Scripts)
[*]**ALL_EYES="$1"** - [3.4 Shell Parameters](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameters.html#index-shell-variable-68), [3.4.1 Positional Parameters](http://www.gnu.org/software/bash/manual/html_node/Positional-Parameters.html#Positional-Parameters), [3.1.2.3 Double Quotes](http://www.gnu.org/software/bash/manual/html_node/Double-Quotes.html#Double-Quotes)
[*]**while ... do ... done** - [3.2.4.1 Looping Constructs](http://www.gnu.org/software/bash/manual/html_node/Looping-Constructs.html#Looping-Constructs)
[*]**read -r** - [4.2 Bash Builtin Commands](http://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html#Bash-Builtins)
[*]**echo "${REPLY/$'\t'*$'\t'*/$'\t'$ALL_EYES$'\t'$ALL_EARS}"** - [4.2 Bash Builtin Commands](http://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html#Bash-Builtins), [3.5.3 Shell Parameter Expansion](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html#Shell-Parameter-Expansion), [3.1.2.4 ANSI-C Quoting](http://www.gnu.org/software/bash/manual/html_node/ANSI_002dC-Quoting.html#ANSI_002dC-Quoting), [3.5.8.1 Pattern Matching](http://www.gnu.org/software/bash/manual/html_node/Pattern-Matching.html#Pattern-Matching)
[*]**eyesnears "Brown" "Large earlobes" <input_file >output_file** - [3.6 Redirections](http://www.gnu.org/software/bash/manual/html_node/Redirections.html#Redirections)
[*]**od -A n -a output_file** - [3.4 od: Write files in octal or other formats](http://www.gnu.org/software/coreutils/manual/html_node/od-invocation.html#od-invocation)
[/list]
HTH

---

### Post by trewsdan on 2011-04-24
Wow! I am thoroughly impressed.  That's a great solution.  Thank you so much for it, and the references.  I really appreciate the help, and sharing the details on bash.  

:)

---

### Post by Telengard C64 on 2011-04-24
> **trewsdan said:**
> Wow! I am thoroughly impressed.  That's a great solution.  Thank you so much for it, and the references.

np, it was fun.

rock on, Bash!

:guitar:

---

