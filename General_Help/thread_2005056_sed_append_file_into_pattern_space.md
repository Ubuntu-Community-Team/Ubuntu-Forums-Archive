---
title: "sed append file into pattern space"
date: 2012-06-16
forum: General Help
---

### Post by spiritech on 2012-06-16
hi, 

how can i append the contents of a file directly into the replacement pattern space.

i have tried something along these lines

sed 's/word/'sed r ~/input'/' file

and 

sed 's/word/'sed r ~/input/'e' file

it says in the 'info sed' that the "e" flag will replace the command output into the pattern space. only i do not know how to put the command.

spiritech

---

### Post by codemaniac on 2012-06-17
something like below 

```
sed -e "/word/r input" -e "/word/d" file
```

The above would replace every occurance of "word" in "file" with the contents of "input" .

---

### Post by spiritech on 2012-06-17
> **codemaniac said:**
> something like below 

```
sed -e "/word/r input" -e "/word/d" file
```The above would replace every occurance of "word" in "file" with the contents of "input" .

i was referring to the flag e not the option -e. the flag option states that you can use a command directly into the pattern space. so would prob look something like this.

sed 's/word/command/e' file

i have tried putting the command between 'command' and {command}.

i tried the way you stated and it replaced every word not just 'word' with the input file plus a blank line.

this is the print out from the info sed. that i am referring to.

`e'
     This command allows one to pipe input from a shell command into
     pattern space.  If a substitution was made, the command that is
     found in pattern space is executed and pattern space is replaced
     with its output.  A trailing newline is suppressed; results are
     undefined if the command to be executed contains a NUL character.
     This is a GNU `sed' extension.

i am not sure how to use this flag.

also how can i use a stored value into the pattern space?

---

### Post by steeldriver on 2012-06-17
I have to admit I'd never heard of the 'e' **command** - one of the dustier corners of GNU sed maybe?

The way it seems to work is if I have a file containing a valid shell command (e.g. literal 'echo $HOME') then I can search for that pattern and instead of printing or substituting or whatever I can **e**xecute it (with the result going into the output stream):

```

$ cat file
echo $HOME
$
$ sed '/\$HOME/!d' file
echo $HOME
$
$ sed '/\$HOME/e' file
/home/steeldriver

```or I can execute any *other* command when the pattern is matched (in which case obviously the pattern itself needn't be a command):

```

$ cat file
echo $HOME
foo bar
$
$ sed -n '/bar/e ls -l' file
total 4
-rw-r--r-- 1 steeldriver steeldriver 19 Jun 17 18:59 file

```Does this help? What exactly are you trying to do?

---

### Post by spiritech on 2012-06-17
> **steeldriver said:**
>  What exactly are you trying to do?

i am trying to put the contents of a file called 'input' into the second substitute space (marked input).
  
sed 's/word/input/' file

if this is not possible, how else can i replace text with the contents of a file?

---

### Post by codemaniac on 2012-06-17
> **spiritech said:**
> i am trying to put the contents of a file called 'input' into the second substitute space (marked input).
  
sed 's/word/input/' file

if this is not possible, how else can i replace text with the contents of a file?

Let me try again, I believe i got your requirements clear .
i would try searching for the "word" in filename "file" , replace it with nothing , then read the "input" file .

In a nutshell , the below would substitute "word" with the contents of "input" .

```
sed '/word/{
    s/word//g
    r input
}' file
```

---

### Post by spiritech on 2012-06-17
> **codemaniac said:**
> Let me try again, I believe i got your requirements clear .
i would try searching for the "word" in filename "file" , replace it with nothing , then read the "input" file .

In a nutshell , the below would substitute "word" with the contents of "input" .

```
sed '/word/{
    s/word//g
    r input
}' file
```

pretty sure all that will do is replace the 'word' with nothing then read and display input file.

as for the first code you posted i think it works to a certain degree.

---

### Post by codemaniac on 2012-06-17
> **spiritech said:**
> pretty sure all that will do is replace the 'word' with nothing then read and display input file.

as for the first code you posted i think it works to a certain degree.

The above posted sed has been tested on my system and working as expected.GNU sed version 4.2.1
Replaces the string "word" only in "file" , other contents in "file" remains unaltered .

Please note that in my posted sed , "word" is hardcoded , if want to replace any other string , use accordingly .


```
(arijit@codemaniac)-(0)-(09:58 PM Sun Jun 17)->
(~)-(18 files)--> cat input
arijit dutta new one
(arijit@codemaniac)-(0)-(09:58 PM Sun Jun 17)->
(~)-(18 files)--> cat file
this is a word
this is my word
(arijit@codemaniac)-(0)-(09:58 PM Sun Jun 17)->
(~)-(18 files)--> sed '/word/{
    s/word//g
    r input
}' file
this is a
arijit dutta new one
this is my
arijit dutta new one
(arijit@codemaniac)-(0)-(09:58 PM Sun Jun 17)->
(~)-(18 files)-->
```

In the above snippet we can see "word" has been replaced by contents of "input" , that is "arijit dutta new one" .

---

### Post by spiritech on 2012-06-17
ok.

no luck so far with any of the options. will keep trying though.

spiritech

---

### Post by codemaniac on 2012-06-17
Can you please tell me where exactly you have been stuck ,
I have posted above the complete snapshot of the working sedlet .Hope that helps .

You can also post your file contents for me to see .

---

### Post by spiritech on 2012-06-17
> **codemaniac said:**
> The above posted sed has been tested on my system and working as expected.GNU sed version 4.2.1
Replaces the string "word" only in "file" , other contents in "file" remains unaltered .

when i tried your code, other contents in file were removed.

---

### Post by codemaniac on 2012-06-17
> **spiritech said:**
> when i tried your code, other contents in file were removed.

The above code is supposed to look for only "**word**" string .There is no way other contents can be manipulated by the above code .

---

### Post by spiritech on 2012-06-17
> **codemaniac said:**
> The above code is supposed to look for only "**word**" string .There is no way other contents can be manipulated by the above code .

does it matter of there are other words in the line.

---

### Post by codemaniac on 2012-06-17
> **spiritech said:**
> does it matter of there are other words in the line.

NO .

You can see in my above example , there are other strings in "file" , still only "word" has been substituted .

---

### Post by spiritech on 2012-06-17
> **codemaniac said:**
> Can you please tell me where exactly you have been stuck ,
I have posted above the complete snapshot of the working sedlet .Hope that helps .

You can also post your file contents for me to see .

this is my out put i get.

spiritech@spiritech:~$ cat file
blah blah blah word blah.
spiritech@spiritech:~$ cat input
letter
spiritech@spiritech:~$ sed '/word/{
s/word//g
r input
}' file
blah blah blah  blah.
letter

---

### Post by spiritech on 2012-06-17
any way. it would be a lot easier if regex could call an input from a file or a stored value.
maybe the problem is not with sed, and is with regex instead. maybe i am asking the wrong question.

---

### Post by steeldriver on 2012-06-17
Does 'input' contain a single line or multiple lines?

If it's a single line, then I think you can fake it with a shell expansion, i.e.

```
sed -e "s/word/$(cat input)/g" file
```(note the double quotes). If the replacement text is multi-line, that's a bit more of a challenge because sed isn't really designed to work over newlines; you would need to mangle the newlines in the input text, something like (frankened together from the 'sed one liners' page):

```
sed -e "s/word/$(sed -e :a -e 'N; s/\n/\\n/; ta' input)/" file
```[Good practice dictates it should be '$!N' rather than 'N' here so  that it doesn't trip up on the EOF - but it is very hard to escape the $! from the surrounding bash shell. Maybe one of the bashistas can tell us how to do that.]

```
$ cat file
here is a word somewhere in a file
$ 
$ cat input
input line1
input line2
input line3
$ 
$ sed -e "s/word/$(sed -e :a -e 'N; s/\n/\\n/; ta' input)/" file
here is a input line1
input line2
input line3 somewhere in a file
$ 

```All the things I tried with the 'r' (read) command appended the input text after the matching line, rather than as an in-line substitution for the matching word.

---

### Post by spiritech on 2012-06-17
> **steeldriver said:**
> Does 'input' contain a single line or multiple lines?

If it's a single line, then I think you can fake it with a shell expansion, i.e.

```
sed -e "s/word/$(cat input)/g" file
```this is what i needed, the shell expansion. it does what i need. could you elaborate a little. i can see that the (cat input) is the bash command and the -e makes the bash recognized why is the $ there normally it means from end of line.

and from what i can see my original estimate might work by replacing the (cat input) with (sed r input), though would not be necessary :).

---

### Post by spiritech on 2012-06-17
removed

---

### Post by markbl on 2012-06-18
> **spiritech said:**
> ```
sed -e "s/word/$(cat input)/g" file
```
Problem with this approach is that there are a gazillion characters potentially in the "input" file which will corrupt that sed expression causing it to fail, or worse - silently give you completely erroneous output. That is a very fragile solution.

I would split the file into pieces and then rejoin it with the new content.

---

### Post by steeldriver on 2012-06-18
> **markbl said:**
> Problem with this approach is that there are a gazillion characters potentially in the "input" file which will corrupt that sed expression causing it to fail, or worse - silently give you completely erroneous output. That is a very fragile solution.

Doh! you're right of course - even innocuous 'textual' characters like '&' that have special meaning in the replacement expression... back to the drawing board I guess :(

---

### Post by spiritech on 2012-06-18
> **spiritech said:**
> ```
sed -e "s/word/$(cat input)/g" file
```

this code does what i need, as long as there is not more than one line in the input file.

spiritech

---

### Post by spiritech on 2012-06-18
> **steeldriver said:**
> Doh! you're right of course - even innocuous 'textual' characters like '&' that have special meaning in the replacement expression... back to the drawing board I guess :(

this is not a problem for me at the moment as the input file does not contain any special characters. 

i did have a play around and entered some into the input file 

111 111 111 111 111 $ * $$$ ** (brmnhb) @:_((* {0,} ( gdg  ) {}(( 0( ><

surely it will only print what goes between ( and ) as text only. maybe using a space at the beginning and end of the command would solve this issue.

$( cat input )

---

