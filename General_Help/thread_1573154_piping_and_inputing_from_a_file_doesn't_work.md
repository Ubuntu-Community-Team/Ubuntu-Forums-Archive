---
title: "piping and inputing from a file doesn't work"
date: 2010-09-12
forum: General Help
---

### Post by neoargon on 2010-09-12
I wrote the download link of a file in a file named test and typed the command ```
wget < test
```but the output was```
 wget < test
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
```But outputing to a file works  fine

The same problem happens when piping too .

Please help

---

### Post by Lukas666 on 2010-09-12
"test" is a system command!

either try 

wget < ./test 

or come up with a better file name!

---

### Post by neoargon on 2010-09-12
> **Lukas666 said:**
> "test" is a system command!

either try 

wget < ./test 

or come up with a better file name!
I changed the file name to many different ones including todownload,  ggggggggggggggggggg  etc . But still the same problem . I tried using "./" too

---

### Post by llamabr on 2010-09-12
You're not piping, you're sending stout.  and if ~/.test just contains a url, all you'll get is an error if you try to run it.

What you want is:

```
cat testfile.txt | xargs wget
```

Where you put some url in testfile.txt

Note, the next person who comes along will remind you that that's way more typing, and twice as many system calls, as just running wget from the cli.  But don't pay any attention to them -- they're your system calls, you can run them as redundantly as you want.  it's your box, right?

---

### Post by neoargon on 2010-09-12
> **llamabr said:**
> You're not piping, you're sending stout.  and if ~/.test just contains a url, all you'll get is an error if you try to run it.

What you want is:

```
cat testfile.txt | xargs wget
```Where you put some url in testfile.txt

Note, the next person who comes along will remind you that that's way more typing, and twice as many system calls, as just running wget from the cli.  But don't pay any attention to them -- they're your system calls, you can run them as redundantly as you want.  it's your box, right?
Thanks for the help , but shouldn't ```
wget <downloadfile.txt
``` work? Please explain what's wrong

---

### Post by neoargon on 2010-09-12
Actually it was this command I wished to execute.  ```
youtube-dl -g http://www.youtube.com/watch?v=7czFOFQD_6A |wget
```
Youtube-dl will find the video url. Wget will download . That didn't work. But thanks to Llamabr the following command worked 
```
youtube-dl -g http://www.youtube.com/watch?v=7czFOFQD_6A |xargs wget
```

Iam still confused why the former command didn't work

---

