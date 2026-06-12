---
title: "Bash Scripting Question"
date: 2010-12-06
forum: General Help
---

### Post by gunit888 on 2010-12-06
Not sure if there's a more appropriate forum for this question, if so please let me know.

I'm writing a bash script to copy a list of files and do some stuff to them.  Basically, I have the code written that does what it needs to do, but I can't quite understand why it works.  I was hoping someone could clear up my understanding a bit.

```

filelist=`ls ~/gpodder-downloads/*/* | grep -v .jpg$ | awk '{print "\""$0"\""}'`

IFS=`echo -en "\n\b"`

```The first line generates a list of files. I wrap each line in quotes because they usually have spaces in the directory names.

The second line changes IFS, and I understand what IFS itself does.  What I don't quite get is what the separator becomes with that echo statement.  If I'm reading that correctly, the backspace will remove the newline and essentially the result is nothing?  I found this solution on a web page somewhere, but it was years old and there was no real explanation.

---

### Post by Brandon Williams on 2010-12-08
A backslash character is displayed on the screen by deleting the preceding character. The backslash character is still represented in the stream, though, so you're setting IFS to the two character string "\n\b". The only one of those that's actually meaningful in this context is the "\n", though, since it's unlikely that "\b" will be present in any of the file names.

---

