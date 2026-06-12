---
title: "strange bash - newbie problem"
date: 2011-02-12
forum: General Help
---

### Post by stuntman on 2011-02-12
I am having a heck of a time getting a basic  for loop to work.
After opening up 'terminal' I type in bash -version and it says version 4.1.5(1)....I am running ubuntu 1.0.04 in Virtual Box.

-I have to start all my *.sh scripts with '##!/bin/bash' because'#!/bin/bash' throws bad interpreter errors????

-after 60+ minutes I have not been able to get a simple for loop to work????

Here is the command line I am running and it works:
```
for file in /etc/*;do echo {$file};done
```

BUT my test.sh script fails
```
##!/bin/bash
for file in /etc/*
do
  echo {$file}
done
```

```
##!/bin/bash
for file in /etc/*
do echo {$file}
done
```


error given: "bash: syntax error near unexpected token `do

Please help...

I seriously need some help on this....I was given some unix work and figured I could figure out a basic find/copy/sort task on the weekend....4 hours in and I am almost at square one still!


stuntman

---

### Post by Habitual on 2011-02-12
workaround it?

```
##!/bin/bash
for file in /etc/*;do echo {$file};done
```

---

### Post by stuntman on 2011-02-12
> **Habitual said:**
> workaround it?

```
##!/bin/bash
for file in /etc/*;do echo {$file};done
```

Good idea but
I tried that and it did not work and I can't do such a workaround for the amount of coding I will have to do.

I am thinking the problem might be with what is executing my script.sh file.

if I put #!/bin/bash I get
```
/bin/bash^M: bad interpreter: No such file or directory
```


still drowning :P

---

### Post by AlphaLexman on 2011-02-12
Did you create or edit the file in a windows/dos environment?
The **^M** tells me you probably did

---

### Post by stuntman on 2011-02-12
> **AlphaLexman said:**
> Did you create or edit the file in a windows/dos environment?
The **^M** tells me you probably did

Yes.
You are the MAN!

I noticed that when I left empty lines the shell would throw unknown command errors.

windows files have different linefeed characters.

So in short.....never modify a file originally created in Windows OR save in a Windows format if the file is to be used for a script.


thanks again!:D

---

### Post by AlphaLexman on 2011-02-12
There are some scripts available (google -> dos2unix) which will convert your files. Please use the thread tools at the top of the page to mark your thread as solved. Welcome to *nix!

---

### Post by asmoore82 on 2011-02-12
You can also just

dos2unix:
```
cat *filename* | tr -d '\r' > /tmp/filename
mv /tmp/filename *filename*
```

mac2unix:
```
cat *filename* | tr '\r' '\n' > /tmp/filename
mv /tmp/filename *filename*
```

I believe `tr` is already installed out-of-the-box on almost
all modern Unix's, even on Mac OS X.

---

### Post by Habitual on 2011-02-12
> **stuntman said:**
> So in short.....never modify a file originally created in Windows OR save in a Windows format if the file is to be used for a script...

Go and sin no more! :KS

---

