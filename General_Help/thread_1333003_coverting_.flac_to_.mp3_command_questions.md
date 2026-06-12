---
title: "coverting .flac to .mp3 command questions"
date: 2009-11-21
forum: General Help
---

### Post by Poyntz on 2009-11-21
```
for file in *.flac; do $(flac -cd "$file" | lame -h - "${file%.flac}.mp3"); done
```

This is a dumb question (prob should be in the n00b forum), still this is my understanding of the above statement. Please correct me if I'm wrong. Also I have some questions.

**file** - a variable
**for; do** - a loop
**in *.flac** - keep the loop going for all .flac files
**(flac -cd "$file"** - decode a .flac output stream and store it in the *file* variable
**| lame -h** - pipe it into ... using a high quality bitrate...
**- "${file%.flac}.mp3");** - for transfer of ALL .flac files to .mp3
**done** - terminate the loop when every .flac file has an .mp3 file? flush all the processing from memory?

- I'm guessing everything within the "( )" brackets is read as an object. 
- I'm assuming that "-" indicates that output will be sent to anything in quotation markets (i'm assuming you don't use a pipe here because you're not putting an output into a command, instead your putting an output into a variable).

now for an audio related question:
- why do you decode files before converting them into .mp3's ?
- what does decode mean?


thanks in advance!

---

### Post by lloyd_b on 2009-11-21
You're close, but missing a couple of key points.

**file** - a variable
**for file in *.flac; do** - loop through all .flac files in current directory, putting the filename into the "file" variable
**flac -cd "$file"** - "play" (decode) the file to "stdout" (standard output)
**|** - "pipe" the stdout from the preceding command to "stdin" (standard input) of the next command
**lame -h - "${file%.flac}.mp3"** - encode the file to mp3 format, taking input from stdin (the " - " tells it to read from stdin, rather than from a file).
**done** - go back to the "for file..." statement, get the next file, and repeat the loop.  If no more files, then continue to next statement.

The "$(...)" business tells it to evaluate what's between the parentheses, and then execute that as a command.  I'm not sure why the script is doing this - I think it'll work just fine without it.

The reason for the decode is simple - lame doesn't understand the .flac format.  So you use the 'flac' utility to convert the file into something that lame *does* understand (I believe it decodes to .wav format, which is a very generic type of sound file, and the default input format for lame).

Lloyd B.

---

### Post by Poyntz on 2009-11-23
very comprehensible. thank you!

just a few questions. 
- why do you need **done**, if **for file in *.flac; do** already initiates a loop?
- other than putting $file into a format that lame understands, what does decode mean?
(according to dict, "convert code into ordinary language")
(i'm guessting this means, pulling the rich formatting rubbish off the variable and making it generically comprehensible to a number of programs). because otherwise I don't see why you wouldn't just encode the .flac file straight away

(and now for another question, just while i'm on the topic)
- what's transcode? 
(according to wiktionary, "convert from one encoding to another")
this meaning leads me to assume that:
decoding + encoding = transcoding

---

### Post by lloyd_b on 2009-11-23
> **Poyntz said:**
> very comprehensible. thank you!

just a few questions. 
- why do you need **done**, if **for file in *.flac; do** already initiates a loop?
- other than putting $file into a format that lame understands, what does decode mean?
(according to dict, "convert code into ordinary language")
(i'm guessting this means, pulling the rich formatting rubbish off the variable and making it generically comprehensible to a number of programs). because otherwise I don't see why you wouldn't just encode the .flac file straight away

(and now for another question, just while i'm on the topic)
- what's transcode? 
(according to wiktionary, "convert from one encoding to another")
this meaning leads me to assume that:
decoding + encoding = transcoding

1. The "for file..." line marks the beginning of the loop.  The "done" indicates the *end* of the loop.  Depending on the script, you may wish to do certain things after all of the files are processed, For example```
for file in *.flac; do $(flac -cd "$file" | lame -h - "${file%.flac}.mp3"); done; mv *.mp3 /home/user/otherdir
``` would process all the files, and then move the transcoded files another directory after processing is complete.  

2.  "Decode", in this instance, means "convert from a file format that uses data compression to a comparable file format that does not use data compression".  While .flac and .mp3 are both compressed formats, they use completely different methods to accomplish the compression.  Thus flac can't understand mp3 encoded files, and vice versa, so an uncompressed intermediate format is required to go from one to the other.  
   Think of it like this - person A speaks English and Spanish, while person B speaks Spanish and French.  To convert a document from English to French you'd have A convert it to Spanish, and then B convert *that* to French.

3. Your understanding of "transcoding" appears correct.  In pretty much every situation, you must decode to a common format, then encode to the new format (though in some cases a single program may be able to do both parts). 

Lloyd B.

---

### Post by pedrogent on 2011-02-24
Thank you so much **lloyd_b**. I was struggling piping flac and lame together. In the end I used:

```
for file in *.flac; do $(flac -cd "$file" | lame --preset fast extreme - "${file%.flac}.mp3"); done
```

This is in OS X 10.6 using FLAC 1.2.1 and LAME 3.98.4.

Can't tell you how much this has helped. Awesome work!

---

