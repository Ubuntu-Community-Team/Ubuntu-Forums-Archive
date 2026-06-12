---
title: "cat | grep (perl?) question"
date: 2011-02-02
forum: General Help
---

### Post by HilliBilly on 2011-02-02
i would like to search one or more files for a line which contains a match to a pattern. if found i would like to print all lines of trailing context AND all lines of leading context until a blank line comes each time.

i know how to use cat and grep but i think these two commands won't do the job, right?

the grep context line control works only for a fixed number of lines but that does not work for me because the number of trailing and leading lines are always different. only thing sure is that each block starts and ends with a blank line.

---

### Post by Vaphell on 2011-02-02
in other words you need something that prints out the whole block if any line in it matches the expression?

---

### Post by HilliBilly on 2011-02-02
yes, exactly.

each file contains hundreds of these blocks, separated with one blank line each, and the length of each block is variable.

---

### Post by pl@yer on 2011-02-02
if you change the "$/" input record seperator to "" then blank lines will be the seperator.
This basically searches testfile.txt for blocks that have cat in there and prints the block if found. This wouldn't work if your blank lines have spaces.

```

#!/usr/bin/perl
#read file into array split by blank lines
my $inputfile="@ARGV[0]";
$/=undef;
$/="";
open FH,"<$inputfile" or die;
@data=<FH>;
close (FH);
foreach my $block (@data){
if ($block=~ /cat/) {
print $block,"\n",;
}
}
close (FH);


```

```

root@steve-HP-Compaq-dc7100-CMT-PJ075UA:~# cat testfile.txt 
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird

thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird

thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf

jjthisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf

thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf

```

result of running script
```

root@steve-HP-Compaq-dc7100-CMT-PJ075UA:~# ./perlspacetest.pl testfile.txt
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird


thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird


thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf



```

---

### Post by bodhi.zazen on 2011-02-02
> **HilliBilly said:**
> i would like to search one or more files for a line which contains a match to a pattern. if found i would like to print all lines of trailing context AND all lines of leading context until a blank line comes each time.

i know how to use cat and grep but i think these two commands won't do the job, right?

the grep context line control works only for a fixed number of lines but that does not work for me because the number of trailing and leading lines are always different. only thing sure is that each block starts and ends with a blank line.

Somewhat off topic, but there is no need to use a pipe with cat | grep

Just grep

Wrong : cat file | grep foo
Correct : grep foo file

I am sure there is probably an exception to the rule, but in general use grep without the cat.

You can probably also use awk as well (depends on if you are more familiar with perl or awk).

---

### Post by Vaphell on 2011-02-02
my attempt - not too pretty nor efficient and sometimes fails at more elaborate sets of parameters, but it tries hard to use native grep params (recursion, flavors of regexps, ignore case, etc) to do its stuff
```
#!/bin/bash

set -e # end script on error 

param=()
files=()
paramlast=true
while [ "$1" ]
do
  if [[ $1 =~ -.* ]]
  then
    param[${#param[@]}]="$1"
    paramlast=true
#    echo $1 '-> param (switch)'
  elif $paramlast
  then
    param[${#param[@]}]="$1"
    paramlast=false
#    echo $1 '-> param (pattern/integer)'
  else
    files[${#files[@]}]="$1"
#    echo $1 '-> file/dir'
  fi
  shift
done

grep -l --binary-files=without-match ${param[@]} "${files[@]}" | while read file
do
#  echo $file
  x=( $(grep -nE '^\s*$' "./$file" | sed 's/://') $( cat "$file" | wc -l ) )
#  echo ${x[@]}
  for (( i=0; i<${#x[@]}; i++ ))
  do
    if (( $i == 0 ))
    then
      from=1
    else
      from=$((${x[$((i-1))]}+1))  # x[i-1]-1
    fi
    to=${x[i]}
    block=$( awk -v from=$from -v to=$to 'NR>=from && NR<=to { print $0 }' "./$file" )
    pos=( $( echo "$block" | grep $1 -n ${param[@]} | sed 's/:.*//' ) )
    p1=${pos[0]}
    if [ "${p1}" != "" ]
    then
      for z in "${!pos[@]}"; do pos[z]=$((${pos[z]}+from-1)); done
      echo ./$file:${pos[@]}
      echo "$block" | grep --color -B $((p1-1)) -A $((to-p1)) ${param[@]}
      echo -----------------------------------------------
    fi
  done
done

```

example output:
```
$ ./textblocks.sh -RiP 'o.*n.*[sz]|wtf' *
./textblocks2.txt:5 6 7
something
**oh noes**
**oh noes**
omg**wtf**
-----------------------------------------------
./textblocks2.txt:9 11 12
**oh noes**
something
**oh noes**
omg **wtf**
-----------------------------------------------
./textblocks.txt:17 18 19
**onoz**
**ONoZ**
OmG**wTf**BbQ
-----------------------------------------------
./bash/incoming2.sh:3
inc**oming='/home/vaphell/tes**t/inc'
def_dest='/home/vaphell/test/movies'
interval=5
-----------------------------------------------
```

there are few issues i need to trace and fix (eg match in the first line is borked currently) but in simple scenarios it works good enough, maybe i'll do some cleanup and optimization

---

### Post by pl@yer on 2011-02-02
Very nice script Vaphell. I can see myself spending some time trying to understand it.

---

### Post by Vaphell on 2011-02-03
it's rather simple
first part (while loop) makes a guess what is a parameter and what is file/dir. I need that split later. -* -> switch, non-switch after switch -> most likely a pattern, the rest -> files/dirs. Files/dirs are used only in the first step, greps further down skip them because their input is fed to them via pipe.
That parameter sorting is not so fancy, if you give nonsense parameters like -B 1 -A 3 the script will pass them to the actual grep commands, i don't check if they make any sense.

i run a first grep with -l switch added to get only the names with matches and pipe it to another while loop.
This main while loop works on files one at a time. I grep -n for ^\s*$ (any empty/whitespace only line) and create array (x[]) of line numbers.
then i iterate the array and check blocks of text from x[i-1] to x[i]
i grep -n the block for matches inside to get relative line numbers (pos[]). If the result is not empty, i print filename: pos[@]+start_of_the_block to get true position in file.
the only thing left to do is to grep the whole block with color. I calculate how many lines before -B and after -A (relative to first match) i need to print out the whole block. If the 1st match is in line 4 of 6 then i need -B 3 -A 2

i got some off by one issue or something, for example search for 'bash' fails to print a shebang line of scripts. I think i don't analyze the very first block, i need to add 0 to the array of empty line numbers. Also i think that perl would be more suited for the task of hardcore text manipulation or at least for the parts of it but i don't know anything about it, so i hacked with the tools i know.

**EDIT**: i think i fixed the problem with the first text block (updated the code in #6)
for some reason something like this:
```
./textblocks.sh -RiP 'omg[^w]|o.*[sz]' *
```
goes down in flames with the message:
```
./textblocks.sh: line 46: 1&#65533;&#65533;&#65533;&#65533;wExifII*
                                       +from-1: syntax error: wrong arithmetic operator (error token is "&#65533;&#65533;&#65533;&#65533;wExifII*
                                                                                                                                 +from-1")

```
EXIF? does it read jpg file? o.O i guess it doesn't work too well on binary files :)

---

### Post by HilliBilly on 2011-02-03
you guys are great. thank you so much!!!

unfortunately i am a total newbie to perl (also my programming skills are a bit rusty, assembler, fortran, cobol ... after that i did stop programming).

i tried pl@yer's script and it works, but with some difficulties.

one problem is if the search pattern contains one or more blanks.

if ($block=~ /cat/) {
if ($block=~ /is this right/) {

also this

$/="";

did not work. changed it to

$/="***";

because each block starts with asterisks in the 2nd line.

#Game No : 10104501670 
***** Hand History for Game 10104501670 *****

(i was not sure i could use a '#' in the search pattern)

vaphell's script looks amazing and i will try it tonight. to tell the truth ... i am not sure i will understand it. :)

---

### Post by pl@yer on 2011-02-03
> **HilliBilly said:**
> you guys are great. thank you so much!!!

unfortunately i am a total newbie to perl (also my programming skills are a bit rusty, assembler, fortran, cobol ... after that i did stop programming).

i tried pl@yer's script and it works, but with some difficulties.

one problem is if the search pattern contains one or more blanks.

if ($block=~ /cat/) {
if ($block=~ /is this right/) {

you always need to escape a space or special character with backslashes like so.
```

if ($block=~ /is\ this\ right/) {

```
> 
(i was not sure i could use a '#' in the search pattern)

sure you can just escape it like above 
```

/\#/

```

@vaphell thanks for the explanation I think I understand it all now. It is just that you bash script-fu is very strong :)

---

### Post by pl@yer on 2011-02-03
I changed the script so you can pass the search string as the first argument and the filename as the second argument.
```

#!/usr/bin/perl
#read file into array split by blank lines
my $inputfile="@ARGV[1]";
my $srchptrn="@ARGV[0]";
if ($inputfile eq "" or $srchptrn eq ""){die};
$/=undef;
$/="***";
open FH,"<$inputfile" or die;
@data=<FH>;
close (FH);
foreach my $block (@data){
if ($block=~ /$srchptrn/) { 
print $block,"\n",;
}
}
close (FH);

```
Here it is in use.
```

root@steve-HP-Compaq-dc7100-CMT-PJ075UA:~# ./perlspacetest.pl "cat\ dog" testfile.txt 

thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
thisasdfasdfa dasdfa sdfasdfasdf cat dog bird
***
root@steve-HP-Compaq-dc7100-CMT-PJ075UA:~# ./perlspacetest.pl \# testfile.txt 
jjthisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
jjthisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
#thisasdfasdfa dasdfa sdfasdfasdf asdfasdfsdf
***

```

---

### Post by Vaphell on 2011-02-03
> **pl@yer said:**
> 

@vaphell thanks for the explanation I think I understand it all now. It is just that you bash script-fu is very strong :)

lmao, it's not that strong but thanks :)
things like parameter shifting or arrays are a matter of last few days in my case, i simply spent lately too much time on scripts inspired by people with some unusual itch to scratch and googled A LOT in the process.
I wish i could be so eager to learn more marketable skills like 'real' programming languages... oh well :)

i think i need to look at perl too, it looks elegant and efficient at what it does.

---

### Post by HilliBilly on 2011-02-03
xyz@centurion3:~/textblox$ ls -ltr
total 76
-rwxr--r-- 1 xyz xyz  1179 2011-02-03 19:23 textblocks.sh
-rw-r--r-- 1 xyz xyz 68527 2011-02-03 19:23 MMSQStxt.txt
xyz@centurion3:~/textblox$   ./textblocks.sh -RiP 'finished' *
+1")syntax error: invalid arithmetic operator (error token is "
xyz@centurion3:~/textblox$ 


what am i doing wrong ???

---

### Post by pl@yer on 2011-02-03
@vaphell I'm just learning perl. I read "beginning perl" it's a good **and** free pdf book.
[http://www.perl.org/books/beginning-perl/](http://www.perl.org/books/beginning-perl/)

---

### Post by Vaphell on 2011-02-03
> what am i doing wrong ???

i'd say nothing - for some reason it happens, i'll have to look into it and try to understand that rather mysterious problem.
can you activate the **echo $file** line (remove #) at the beginning of the **grep -l | while read file** loop and rerun that crashing combination again? it will print the file that was analyzed when the crash happened so it may give me some clue.
In my case the script tries to analyze jpg file which won't happen as it is a binary gibberish.

**EDIT:** i may have located the problem. It appears that while 'normal' grep completely ignores binary files and scans only human readable ones, grep with -l (get filenames only) counts them in and you need to convince it to change its mind with ```
--binary-files=without-match
``` switch. I'll update the code in my earlier post, try it.


if you look for normal words, not for regular expressions you may skip E,P,e or whatever kind of regular expression there is available in grep, if you don't have to search recursively in subdirectories, you may skip R. In the most basic form script can be executed with
```
script 'pattern' <file(s)>
```
eg *, *.txt, file1 file2 file3

read ```
grep --help
``` to see available switches, but don't try too hard to fool the script :-) -i -R -e/E/P/G/F etc are enough. In case you need fancier patterns, get familiar with regular expressions - they rock.

btw, if you want to make the script easily accessible, create bin folder in your home and put the script there, with some nice catchy name of your choice. After the restart of terminal it should be available in any location without typing the path in (./ or whatever)

---

### Post by HilliBilly on 2011-02-03
xyz@centurion3:~/textblox$ ./textblocks.sh -RiP 'finished' *
-RiP -> param (switch)
finished -> param (pattern/integer)
MMSQStxt.txt -> file/dir
textblocks.sh -> file/dir
textblocks.sh~ -> file/dir
MMSQStxt.txt
 2230
+1")syntax error: invalid arithmetic operator (error token is "
xyz@centurion3:~/textblox$

xyz@centurion3:~/textblox$ ./textblocks.sh  'a' *
a -> param (pattern/integer)
MMSQStxt.txt -> file/dir
textblocks.sh -> file/dir
textblocks.sh~ -> file/dir
MMSQStxt.txt
 2230
./MMSQStxt.txt:1
")syntax error: invalid arithmetic operator (error token is "

xyz@centurion3:~/textblox$ ./textblocks.sh  'finished' *
finished -> param (pattern/integer)
MMSQStxt.txt -> file/dir
textblocks.sh -> file/dir
textblocks.sh~ -> file/dir
MMSQStxt.txt
 2230
+1")syntax error: invalid arithmetic operator (error token is "
xyz@centurion3:~/textblox$

---

### Post by sisco311 on 2011-02-03
Hmmm, how about:
```
awk 'BEGIN  { RS="" } /**PATTERN**/{ print $0 }' file
```
?

---

### Post by sisco311 on 2011-02-03
> **bodhi.zazen said:**
> Somewhat off topic, but there is no need to use a pipe with cat | grep

Just grep

Wrong : cat file | grep foo
Correct : grep foo file

I am sure there is probably an exception to the rule, but in general use grep without the cat.



+1

In general, there is no need to pipe the output of cat to any command or block of commands.  

Wrong: cat file | tr '\t' '\n'
Correct: tr '\t' '\n' < file

---

### Post by HilliBilly on 2011-02-04
@Vaphell

have sent you a pm

---

### Post by pl@yer on 2011-02-04
> **sisco311 said:**
> Hmmm, how about:
```
awk 'BEGIN  { RS="" } /**PATTERN**/{ print $0 }' file
```
?

I have to become more familiar with awk! That works swell :)

---

### Post by bodhi.zazen on 2011-02-04
> **pl@yer said:**
> I have to become more familiar with awk! That works swell :)

awk is awesome =)

---

