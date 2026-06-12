---
title: "Using variables in awk IF statements"
date: 2010-11-02
forum: General Help
---

### Post by yamahaevans on 2010-11-02
Hi all,
I'm wrestling with a tricky (for me anyway) issue:

I have a list of names *(testnames.txt)* and I have a set of log files *(testlogdata.log*).  I'm trying to search the column in my log file for each of the names in my *testnames.txt* file, and output the result to individual files, name1.txt, name2.txt, name3.txt, etc

the names in the column of my log file can appear in different formats , ie the name "Tom Smith" can appear as "tom_smith", "tom-smith", "ACME/tom.smith", "ACME/thomas.smith".  etc.

To allow for the variations, I have my names in the *testnames.txt* as expressions, ie, for tom smith, I use the expression "to.*smith", etc.

Now, to the problem:

I'm running the following command:

**for i in $(cat *testnames.txt*); do awk '{if ($9~/$i/) print $0}' *testlogdata.log* > $ioutput.log; done**


I want the command to read a value for i, insert it into the if ($9~/inserted value for i/, and dump each line from testlogdata.log into a file named <value-for-i>output.log.

So far, this isn't working.  Any suggestions?

Thanks for your help,

Yamaha

---

### Post by DaithiF on 2010-11-02
the shell variable containing the name pattern won't get expanded inside single quotes, so you need to use double quotes.

of course that would mean $9 and $0 being expanded by the shell too ... so you need to escape those so they survive intact and get through to awk.

```
while read pattern
do
awk "{ if( \$9 ~ /${pattern}/) print \$0 }" testlogdata.log > ${pattern}output.log
done < names.txt

```

---

### Post by yamahaevans on 2010-11-02
Thanks DaithiF, this was a big help.......:)

I modified my command following your suggestions.  The separate output logs are now created, though they are not populated.  Also, I get a "runaway regular expression /name1 pri...", "runaway regular expression /name2 pri ...", etc error.

Any other suggestions?

Yamaha

---

### Post by DaithiF on 2010-11-02
typo in the above, omitted the second / surrounding the pattern, fixed now.

---

### Post by yamahaevans on 2010-11-02
SUCCESS!

Thank you DaithiF, I added a / after /${pattern}, and everything worked as I hoped!

Yamaha

---

