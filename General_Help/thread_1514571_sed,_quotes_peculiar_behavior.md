---
title: "sed, quotes peculiar behavior"
date: 2010-06-21
forum: General Help
---

### Post by satyanash on 2010-06-21
Hi, i was just using sed for something that i needed to do..and noticed this peculiar behavior which resulted in different outputs when the single quotes were used and when they were not used..though my problem is solved without using the quotes i just wanted to ask why is this happening.

i have enclosed a .png of the problem. The last command has been run with the quotes and the second from last has been run without the quotes. According to the documented sed behavior it should give the output regardless of the quotes, and those are useful only if there are meta-characters present in the filenames. The command that is second from last is the output that i wanted. And thus gets my work done but i am asking this question just out of curiosity.

---

### Post by roncrump on 2010-06-21
> **sattu94@gmail.com said:**
> Hi, i was just using sed for something that i needed to do..and noticed this peculiar behavior which resulted in different outputs when the single quotes were used and when they were not used..though my problem is solved without using the quotes i just wanted to ask why is this happening.

i have enclosed a .png of the problem. The last command has been run with the quotes and the second from last has been run without the quotes. According to the documented sed behavior it should give the output regardless of the quotes, and those are useful only if there are meta-characters present in the filenames. The command that is second from last is the output that i wanted. And thus gets my work done but i am asking this question just out of curiosity.

Not 100% sure, as I don't sed much, but my guess would be that when you don't have the quotes $hst is being expanded, whereas in the quoted case it isn't (ie it is being treated as a string $hst rather than the value stored in the variable hst).

Ron.

---

### Post by Smart Viking on 2010-06-21
I do know that quoting with 'this' behaves differently than quoting with "this", try per example and see the differences by these commands:

```
smartviking@smartviking-desktop:~$ echo "$RANDOM"
13519
smartviking@smartviking-desktop:~$ echo '$RANDOM'
$RANDOM
```

Maybe you already knew this, and maybe it has nothing to do with this case, but i thought i should put it in here. :)

---

### Post by satyanash on 2010-06-21
hmmm.. ok the double quotes as stated above by Smart Viking seem to work like without the quotes..then maybe the place where i read it mentioned it incorrectly..heres the link where i read it..

[http://www.grymoire.com/Unix/Sed.html#uh-5](http://www.grymoire.com/Unix/Sed.html#uh-5)

It's just given there under the s as a substitute command.. anyway thanx for the info..andi dint know double quotes worked..

---

### Post by Smart Viking on 2010-06-21
np. :)

"this" is called a "weak" quote, which means variables and such will live its life in it.

While 'this' is called a 'strong' quote, because per example in the 'echo' command, it is made to display exactly what you enter inside it. :)

---

### Post by apmcd47 on 2010-06-21
> **sattu94@gmail.com said:**
> hmmm.. ok the double quotes as stated above by Smart Viking seem to work like without the quotes..then maybe the place where i read it mentioned it incorrectly..heres the link where i read it..

[http://www.grymoire.com/Unix/Sed.html#uh-5](http://www.grymoire.com/Unix/Sed.html#uh-5)

It's just given there under the s as a substitute command.. anyway thanx for the info..andi dint know double quotes worked..

The problem is that characters like * and $ mean something to the shell and they also mean something to sed. The dollar sign, for instance, is an anchor for end of text in sed, while it tells the shell to expand the following $variable, ${variable} or $(command). The asterisk is a wildcard sign in the shell (so a* could expand to the names of all files in the current directory starting with a in shell) but also a repeat any symbol in sed (so a* will match with a string of one or more as, eg a, aa, aaaa, ...). 
Hence in the above link they quote all sed commands with single quotes.
As mentioned by others, single quotes turn off the meaning of special characters to shell allowing them to be interpreted properly by sed or whatever other command they are arguments to. If you want to pass for instance variables into the likes of sed you cannot use strings quoted by single quotes (although it is probably sensible to use double quotes, especially if spaces are involved), but if you are using characters special to both shell and sed you should quote them using the backslash, e.g.```
echo $mystring | sed s/a\*b/$new/
```will replace ab, aab, etc with the contents of $new, but without the backslash as an escape character, the shell may have expanded a* in a different way.

You have to be aware of special characters when using commands like sed, awk, tr and find in shell-scripts and think about whether you need single-quotes, double-quotes or backslash escapes.

Andrew

---

### Post by DaithiF on 2010-06-21
and just to clarify, the quoting here isn't anything to do with sed -- it is the shell that either expands the $hst variable or not, and this is before sed gets to read the command.   

Single quotes mean that shell variables are not expanded, double quotes or no quotes mean that they are.  But sed is oblivious to the existence of shell variables, it just operates on whatever command it gets, and that command is whatever is left after the shell has done its variable expansion.

---

### Post by satyanash on 2010-06-21
Very good, the above two replies, very clearly, indicate what is happening..
Thanks to everybody..i think i should mark this thread as solved then..

---

