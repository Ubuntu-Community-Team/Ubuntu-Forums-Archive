---
title: "Command Line Help - output of command as input for another command"
date: 2012-07-15
forum: General Help
---

### Post by leegold on 2012-07-15
I want to grep a dir for mp3 files and then check each resulting file with another command. So I tried this:


$ mp3check -c --show-valid $(ls | grep mp3) 

or I tried,

$ mp3check -c --show-valid `ls | grep mp3`


I thought that's how you do it. But I get error :

...
can't stat file (dangling symbolic link?)
Blues.mp3:
...

What am I doing wrong?

Thanks

---

### Post by steeldriver on 2012-07-15
Try just letting the shell expand all the *.mp3 files - it's safer

```
mp3check -c --show-valid *.mp3
```FYI you are likely encountering one of the "bash pitfalls" related to word splitting:
 
 [http://mywiki.wooledge.org/BashPitfalls/#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls/#for_i_in_.24.28ls_.2A.mp3.29)
 
 (there is probably a file called "something Blues.mp3" with a space in)

---

### Post by Kirk Schnable on 2012-07-15
You might also try replacing "ls" with "ls -1" because ls shows multiple items on one line.  "ls -1" only prints one list item per line.  That might help with your separation problems.

Kirk

---

### Post by Vaphell on 2012-07-15
no, the kosher way to do that is to use builtin globbing (like steeldriver said) which avoids whitespace problems completely.
ls is only for visual feedback, not as a source of data to process.

And ls -1 or not, it will never work reliably.

---

### Post by kjohri on 2012-07-15
I think you wish to use the ouput of a command as arguments of another command. Try,

ls | grep mp3 | xargs mp3check -c --show-valid

---

### Post by Vaphell on 2012-07-15
surprise surprise, it doesn't work

this is run in dir with some space-in-names files
```
$ ./paramcount.sh *\ *
params: 11
$ ls | grep ' ' | wc -l
11
$ ls | grep ' ' | xargs ./paramcount.sh
params: 26
```
there are 11 files but xarg puts 26 to script
```
$ ls | grep ' ' | xargs -d$'\n' ./paramcount.sh
params: 11
```
Xargs splits at whitespaces so delimiter needs to be set explicitly to newline to ignore spaces - result is correct... but wait, there is more.
Newline is a legit character in file/dir names in linux and the last line will fail. Grep works on lines and 2-line filename will blow the whole command chain up.
As you can see it's a pain in the back to support whitespaces manually as long as file names are concerned, globs don't care and will just work 100% of the time.
So can we go back to straightforward *<command> *.mp3* yet?

---

