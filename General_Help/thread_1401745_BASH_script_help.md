---
title: "BASH script help"
date: 2010-02-08
forum: General Help
---

### Post by kibstah on 2010-02-08
Hi
I have a file which contains 12 rows of incomplete quotes.

I want to make a script that echo one line at a time and make the user to complete the whole quote and stores the answer in a another file.

I was thinking of a for loop but don't know how to...

Any help would be appreciated.

---

### Post by DaithiF on 2010-02-09
Hello,
something like this script:

```
#!/bin/bash

IFS=
> quoteanswers                  # truncate any previous answers file

exec 3<> quotelist              # open quotes file for reading as filehandle 3
while read partial <&3
do
        read -p "$partial ... " answer
        echo "$partial $answer" >> quoteanswers
done
echo "ANSWERS..."
cat quoteanswers

```

so, for a given list of partial quotes, eg.:
```
$ cat quotelist
To be or not to be
But words are words, I never yet did hear
I will arise and go now

```

```
$ ./doquotes
To be or not to be ... that is the question
But words are words, I never yet did hear ... the bruised heart is pierced by the ear
I will arise and go now ... and go to Inisfree
ANSWERS...
To be or not to be that is the question
But words are words, I never yet did hear the bruised heart is pierced by the ear
I will arise and go now and go to Inisfree

```

---

