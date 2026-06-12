---
title: "Korn Shell: Syntax error on test a function with parameters"
date: 2011-01-04
forum: General Help
---

### Post by rpaskudniak on 2011-01-04
Greetings.

Some may recall I recently gave up on bash, rather than give up my programming style.  Surely I will have reason to return but that's another story.  My little issue now:

I am debugging a new [Korn] shell script.  I have a function that performs a specialized match on a string and I see that I am able to call that function with no problem, with both of it parameters.  The function does not do any print or echo command - it uses "return" for a TRUE (0) of FALSE (1), as is the shell exit code convention.  Thus, I have the following test:
```
if [[ match_except_release ${PATH_DIR[$LC]} bin ]]
then
  # some stuff
else
  # other stuff
fi
```
When I run this code, the above call gets a syntax error:
> /var/opt/ifmx/scripts/ifmx-server: line 121: syntax error at line 126: `${PATH_DIR[$LC]}' unexpectedRight now, that call is on line 126 of the script.

I have also tried sticking a simpler variable into that parameter slot, with the same error message.

Now, I do have an easy workaround:
```
IT_MATCHES=match_except_release ${PATH_DIR[$LC]} bin
if [[ $IT_MATCHES ]]
...
```
and that does work.  But I'm interested in the mechanics here: What is wrong with the test as I had wanted to code it?

Thank you, gurus.

---

### Post by Brandon Williams on 2011-01-05
If you want to test the return code from a function, you don't need the "[[". That is only used when you're performing the matching operation directly within the "[[" and "]]". Instead, just do:```
if match_except_release ${PATH_DIR[$LC]} bin
``` I'm surprised to hear you say that they other approach appears to work, because it shouldn't. The assignment that you're doing would not assign the return code from the function to the variable in question. It is certainly not a POSIX compliant approach, and ksh is a POSIX shell.

---

### Post by rpaskudniak on 2011-01-06
Thank you, Brandon, for point out my error with the double brackets.  You are correct, of course.  Even the method I had pointed out as working was similarly incorrect - it should have been
if $IT_MATCHES
rather than
if [[ $IT_MATCHES ]]

For the further edification of a lesser initiate into shell scripting, the [[ double bracket ]] operator is merely a built-in version of the ***[FONT="Courier New"]test[/FONT]*** command.  It should be used in this form:
```
if [[ -x some_file ]]
then
..
fi
```
where one could have used
```
if test -x some_file
```Again, my bad; the use of the duble-bracket in my context made no sense.  I'm surprised it took so long for someone to notice it.

Now that I have removed the double bracket from my original code and removed the "workaround" code, it looks more like this:
```
127   if match_except_release "${PATH_DIR[$LC]}" bin  
128   then
129     IBIN_INDEX=$LC      # Indicate where in PATH I found the INFORMIXBIN
130     continue
131   fi

```
And it works!!

Of course, now I can start debugging that shell function....  But that's another story.  I will be marking this thread as solved.

---

