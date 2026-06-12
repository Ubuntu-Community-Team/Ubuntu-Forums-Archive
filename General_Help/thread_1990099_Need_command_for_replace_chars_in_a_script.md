---
title: "Need command for replace chars in a script"
date: 2012-05-29
forum: General Help
---

### Post by Thetri on 2012-05-29
need the command to replace the character '\' with '/' in a script file. The command also should output the result to a new file. Thanks.

---

### Post by dcstar on 2012-05-29
> **Thetri said:**
> need the command to replace the character '\' with '/' in a script file. The command also should output the result to a new file. Thanks.

```
man sed
```

---

### Post by Thetri on 2012-05-29
> **dcstar said:**
> ```
man sed
```

I have no idea what this is.....I put this in and it opened some stream editor....not what i was looking for..thanks anyway.lol

---

### Post by zero2xiii on 2012-05-29
> **Thetri said:**
> I have no idea what this is.....I put this in and it opened some stream editor....not what i was looking for..thanks anyway.lol

That is exactly what you need. SED is a stream editor. Read the manual, or use google, on how to use it.

"man sed" should open the manual.

---

### Post by nothingspecial on 2012-05-29
A stream editor is exactly what you need.

Something like this

```
sed 's|\\|\/|g' original_file >new_file
```

should do the trick.

---

### Post by David Andersson on 2012-05-29
> **Thetri said:**
> I have no idea what this is.....I put this in and it opened some stream editor....not what i was looking for..thanks anyway.lol

1) The **man** is the manual command. Like in **man firefox** or **man ls** to see the manual for firefox and ls. Dcstar just want you to learn about the **sed** command, but is a little bit shy for a full explanation.

2) With man you read the manual using the **less** pager. You jump forward with *space* and *return*, backward with b, search with /, and quit with q. See **man less**. :)

3) For the original question, may I also suggest
```
man tr
```

4) About the "output to a new file". This is unix. The mechanisms to chance chars and output result are separate. One idiom is
```
command_that_changes_something <infile  >outfile
```
where the command_that_changes_something reads from stdin and writes to stdout. (This is what **sed** and **tr** do.) Maybe you can tell us a little bit more about the problem?

---

### Post by Habitual on 2012-05-29
sed IS that command to replace characters, a stream editor.
[http://unixhelp.ed.ac.uk/CGI/man-cgi?sed](http://unixhelp.ed.ac.uk/CGI/man-cgi?sed)

```
sed -e 's/\\/\//g' infile
```

This better not be homework!

HTH.

---

### Post by dcstar on 2012-05-29
> **Habitual said:**
> 
.......
This better not be homework!


Why?, people continually post here finding suckers to do their assignments etc. and are usually trampled in the rush by "helpful" people.

How do you find those who throw out the bait?

One good way is to look at their post count.

---

### Post by nothingspecial on 2012-05-29
> **dcstar said:**
> 
One good way is to look at their post count.

Looking at posting history tells you a lot more ;)

---

