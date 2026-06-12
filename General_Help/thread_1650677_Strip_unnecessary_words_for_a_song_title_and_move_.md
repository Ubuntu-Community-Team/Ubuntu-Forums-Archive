---
title: "Strip unnecessary words for a song title and move it to new name"
date: 2010-12-22
forum: General Help
---

### Post by Silvernail on 2010-12-22
Every resource I can find points to Tillies Garrels TLDP reference. Do I want to create my own variable to hold the string or do I want to place the string in memory?

Is that my problem? Or is something different causing the 'bad substitution' error.

> dave@dave:~/name-code$ bash --version
GNU bash, version 4.1.5(1)-release (i486-pc-linux-gnu)
Copyright (C) 2009 Free Software Foundation, Inc.
  


> dave@dave:~/name-code$ ./strip-name.sh PeopleWhoMust-TheSleepofReason-29-
PeopleWhoMust-TheSleepofReason-29-----
PeopleWhoMust-TheSleepofReason-01-RainyDayParades.mp3+++
34
./strip-name.sh: line 22: ${"filename":text_size}: bad substitution
dave@dave:~/name-code$ 



```
#!/bin/bash
## strip  unnecerssary parts of song titles.
## check if command line argument is missing.
if [ $# -eq 0 ]
then
echo "You forgot to enter a string to remove!"
echo "Usage :: TARGET"
exit
fi

first_name=$1;
echo "$first_name----"; ## debug

for filename in *.mp3;  ##list all song names in directory by extension

  do
  if [ -f "$filename" ]
echo "$filename+++"; ## debug
    then
	text_size=("$first_name");
echo ${#text_size}; ## debug
	out_file_name=${"filename":text_size}; ## bad substitution
			
		echo "$out_file_name___"; 
		## mv "$filename" "$out_file_name"
    else
	:
    fi
    done
exit
```

---

### Post by colobix on 2010-12-22
As in unnecessary words, do you mean you want to censor the words?
Why can't you just search the words in your music folder and replace them with something else? I assume you are doing this because your kid is using the pc. If so, then you should just talk to him/her about these words instead, and that these words can be used to hurt people and therefor shouldn't be used. This is way better than trying to keep everything censored for your child. Children aren't stupid, and one day he/she will learn that these words are "cool" and then it's too late.
As for me, I am totally against censorship. But yea, that's the way you should go with this.

---

### Post by Silvernail on 2010-12-22
My apologies for being unclear.
I agree with the young children part, but I am single, 74, kids are over 50, no grand kids. But thanks for the concern.

When I buy an album of music as a digital download and unzip it, a lot of the song titles are looking something like this.
> PeopleWhoMust-TheSleepofReason-15-YesterdayAndDays.mp3
When I try to import them into a playlist for say 'rhythmbox', I will not get them sorted over the playlist according to the name of the song, but according to the first 34 letters. A straight run of 10 to 20 songs by the same group is not what I want.

---

### Post by JKyleOKC on 2010-12-22
In the script, at the point of the error, you show "filename" in double quotes. I believe it should be "$filename" because what you now have simply puts the literal string filename into the operation and what you want to have there is the string contained in the variable named filename.

Does that make a difference? If it does, did you type the script in from a web listing, or simply download or copy-and-paste it? If the latter, and my suggestion works, it would be nice to let the original author know about the correction!

BTW, I'm a bit more than 5 years older than you. Who said Linux is for those young whipper-snappers?

---

### Post by Silvernail on 2010-12-22
Were you referring to this line?  > out_file_name=${filename:text_size}; ## bad substitution

Changing it to:
> out_file_name={"$filename":text_size}; ## bad substitution


Prints all 29 files in this format:
> PeopleWhoMust-TheSleepofReason-23-Mispoken.mp3+++
34

PeopleWhoMust-TheSleepofReason-24-OmniJam.mp3+++
34

PeopleWhoMust-TheSleepofReason-25-StopThinking.mp3+++
34


Hooray for us old peoples.

---

### Post by JKyleOKC on 2010-12-22
Try the $ in front of "text_size" instead of in front of "filename" so that the line reads ```
out_file_name=${"filename":$text_size}; ## bad substitution
```and see if that does better. I've not used this particular feature of bash although I've read about it; the intent is to drop the first text_size letters from the filename string, and keep the rest. 

I'll look this up in my copy of "Learning the Bash Shell" but it'll be tomorrow before I do...

Also, you might be able to replace this line with a call to the sed stream editor to delete the first $text_size characters and get the same effect.

---

### Post by JKyleOKC on 2010-12-23
This problem got under my skin so I wrote a little test script to try various ways of removing a leading or trailing substring. Most of what I tried came up with that same "bad substitution" error, but here's the one that worked (including its output for three trial runs):

```
#! /bin/bash
# test of prefix-stripping - jk - 12/23/2010

echo ${2:$1}

exit 0

# results of running above:
# $ ./xtst 2 abcdef
# cdef
# $ ./xtst -3 abcdef
# def
# $ ./xtst 1 abcdef
# bcdef

```The leading "$" is required following the ":" but not any place else in the expression...

You might try leaving the quotes around "filename" off, also; I didn't try with them present. EDIT: I did try with them around the "2" and got the "bad substitution" error, so that's apparently the cause of the problem!

---

