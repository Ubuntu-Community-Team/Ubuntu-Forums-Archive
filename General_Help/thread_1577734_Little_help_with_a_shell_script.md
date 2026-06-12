---
title: "Little help with a shell script"
date: 2010-09-19
forum: General Help
---

### Post by geoffmcc on 2010-09-19
Ok, I pieced together a simple shell script to open an encrypted file. Easy enough, as i obviously don't want to script the password. Then after i close the file it will delete the decrypted file, as i will usually probably forget to

This got me thinking. Right now I only have one thing to decrypt, but I will over time have more. So finally my question.

Could someone point me in direction for coding the enter of file name. This is what i pieced together so far.

```

#!/bin/bash

openssl aes-256-cbc -d -a -in filename.txt.enc -out filename.txt

nano filename.txt

sleep 1

rm -rf filename.txt

sleep 1

exit


```

The way i picture it is when i enter filename it will expect the enc extention and also change the -out to filename entered

so if filename.txt.enc then output would be filename.txt

Any help would be appreciated, i can understand you not wanting to do my coding for me so if you could just offer up a few links if you dont wanna show me that would be cool too. I tried google searching but i don't know the proper terminology so i am not yielding any results

---

### Post by Vaphell on 2010-09-19
simply google for bash programming

parameters are rather easy, whatever you type after the command name will be delimited by spaces and available thanks to the index number of the parameter

$n substitutes nth parameter anywhere in the script so $1 = first, $2 = second... IIRC $@ = all params

command a b c -> $1=a, $2=b, $3=c
command "a b" c -> $1=a b $2=c
command a\ b c -> $1=a b $2=c (\ makes sure that following char has no logical meaning and is ignored when parsing => space preceded with \ stops being a delimiter) 


so you want something like
openssl aes-256-cbc -d -a -in "$1".enc -out "$1"
whatever you type as the parameter will be put verbatim in place of $1, in your case that parameter would replace all occurences of filename.txt

---

### Post by john newbuntu on 2010-09-19
Welcome to coding. Good to hear more people get into it.  Your pseudo-code would be something like this:
```

#!/bin/bash
while [ true ]; do
read filename

   if [ -z "$filename" ]; then
      exit 0
   fi

   --here's where you do your de/encryption
   if [ $? -eq 0 ]; then
       --you are in good shape. so delete the file.
   else
      --something bad happened bail out.
   fi
done

```This way, you keep entering files until you type nothing and hit enter.  Obviously you can code this in a variety of ways and bullet-proof it at various levels.

---

### Post by geoffmcc on 2010-09-19
Thank you. I got some reading and experimenting to do. This does point me in right direction. And am actually looking at it differently.

I was picturing me launching script and then having it ask me for a file name to decrypt, now i realise i can just use something like ./decrypt filename

---

### Post by NFblaze on 2010-09-19
Also, if those are such sensitive files you may want to look into reading the manpages of the shred command as a substitute for rf.

---

### Post by geoffmcc on 2010-09-19
You totally just read my mind. I am new to encryption really. I just thought to myself, wait if i rm -rf the .txt file, its prob still somewhere. will look into shred

---

