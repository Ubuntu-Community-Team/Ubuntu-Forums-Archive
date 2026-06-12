---
title: "Multiple &quot;for x do&quot; - commands in one script?"
date: 2012-04-21
forum: General Help
---

### Post by AlexOnVinyl on 2012-04-21
I'm trying to make a script that will combine 2 stereo channels together but I want it to be so that I can right click and have it passthru the same input file name and same extension when I have it output.

Here's what I've got so far:

```
#!/bin/bash

for fl in * for f in .* ; do sox "$fl" "$f" -c1 "${fl%.*.f}.$f"; done
```

> fl in the command is supposed to represent "filename" and > f is supposed to represent the format after the > . example: > .mp3, .flac, .ogg

As I should've stated this is just a more efficient way for me to combine poorly formatted audio files where only you can only hear certain parts through 1 speaker in a massive amount.

Again, script has yet to work exactly. can't figure out where I'm going wrong.

---

### Post by hakermania on 2012-04-21
It isn't very clear to me what you're trying to do!

Do you try having every filename in the directory with every single format?
Example of directory:
```

file1.mp3
file2.ogg

```
You expect to get:
```

file1 mp3 ogg
file2 mp3 ogg

```
or something like this?

Please clarify (english is not my native language and I maybe didn't get it, it doesn't mean that you weren't clear)

---

### Post by SeijiSensei on 2012-04-21
If you want to nest for loops you need to include do/done constructs as well:

```
for f in *
do
    for x in y
    do
       stuff
    done
done
```

---

### Post by Vaphell on 2012-04-21
you should provide some real life example what you want to achieve
'i got files X.xxx and Y.yyy and Z.zzz and for each of them i want to ... etc.'

---

### Post by hakermania on 2012-04-21
> **Vaphell said:**
> you should provide some real life example what you want to achieve
'i got files X.xxx and Y.yyy and Z.zzz and for each of them i want to ... etc.'

I agree, what he is trying to do is unclear.

---

### Post by AlexOnVinyl on 2012-04-22
> **Vaphell said:**
> you should provide some real life example what you want to achieve
'i got files X.xxx and Y.yyy and Z.zzz and for each of them i want to ... etc.'

Here's what I'm converting:

This whole directory of music: [IMG]http://i.imgur.com/kVuiB.png[/IMG]

Okay, here's the issue - all the audio files' stereo channels have been split - so instead of the same sounds coming from both speakers, I'm only getting different sounds on 1 channel than I am of the other channel.  - This is due to poor rips, so instead of a 2 channel stereo mp3 - I've got a 2 channel - 1 stereo, 1 contains all the song, so it only plays out one side.

Picture below: [IMG]http://i.imgur.com/c7gti.png[/IMG] 

- Here's what your standard 2 channel stereo mp3 looks like:
[IMG]http://i.imgur.com/s0o2X.png[/IMG]

- Do you see how both channels are exactly the same and have the same sound as compared to the previous photo? 

Take another look at the first one: [IMG]http://i.imgur.com/c7gti.png[/IMG]

How its supposed to look:
[IMG]http://i.imgur.com/s0o2X.png[/IMG]

**SO TL;DR**

I'm making a script that will combine the channels of those mp3s in that directory, which in turn makes it Mono - which then I will convert to Stereo - by adding the second channel properly - then Normalizing.

---

### Post by Vaphell on 2012-04-22
> - Do you see how both channels are exactly the same and have the same sound as compared to the previous photo?

minor nitpick: stereo is not supposed to have exactly the same channels, that goes against the very idea of stereo. That's mono in stereo's jacket. Of course having everything on 1 channel and pretty much nothing on the second is worse than that so what you try to do is understandable.

now

```
#create subdir for output to keep things tidy
mkdir -p mono

# iterate over audio files
for file in *.{mp3,flac,ogg}
do
  name=${file%.*}
  ext=${file##*.}
  echo file: "$file"
  echo name: "$name"
  echo type: "$ext"
  echo executing sox "'$file'" "'$ext'" -c1 "'mono/$file'"
  sox "$file" "$ext" -c1 mono/"$file"
  echo
done
```

can't test it, sox i have is not compiled with mp3 support and i can't be bothered to fix that

---

### Post by AlexOnVinyl on 2012-04-23
> **Vaphell said:**
> minor nitpick: stereo is not supposed to have exactly the same channels, that goes against the very idea of stereo. That's mono in stereo's jacket. Of course having everything on 1 channel and pretty much nothing on the second is worse than that so what you try to do is understandable.

now

```
#create subdir for output to keep things tidy
mkdir -p mono

# iterate over audio files
for file in *.{mp3,flac,ogg}
do
  name=${file%.*}
  ext=${file##*.}
  echo file: "$file"
  echo name: "$name"
  echo type: "$ext"
  echo executing sox "'$file'" "'$ext'" -c1 "'mono/$file'"
  sox "$file" "$ext" -c1 mono/"$file"
  echo
done
```

can't test it, sox i have is not compiled with mp3 support and i can't be bothered to fix that

Do you want me to run this from bash? and also the '**#**' is to comment out anything right?


Update:

Ran from nautilus-scripts on single and multiple audio files - only operation that was preformed was the > mkdir 'mono' the rest didnt seem to follow suit.

---

### Post by Vaphell on 2012-04-23
crap, you should mention that you want to run it from nautilus-scripts, i assumed running the script from the directory in question.
Imho you have approached the problem from the wrong side, you need to have a script that works in terminal first and then figure out what needs to be done to plug it in nautilus-actions.

how is the nautilus-entry set up? What is in the 'parameters' field?
If you want to run the script from n-a you can throw any *for file in *.mp3* out the window, you want *for file in "$@"*
$@ = script parameters while *.mp3 means 'in current dir find me files matching this' which ignores script params completely.

can you print the filenames passed to the script via n-a to some file?
something like *for f in "$@"; echo "$f"; done > files.txt*
i recall that n-a doesn't necessarily produces 'ordinary' names, but can spit names in uri format
file:///home/me/some%20dir/some%20file.mp3 or something like that and that would change a lot
print out names to some garbage file and see what you are dealing with exactly
I'd check that myself, but i helped once a guy with n-a and his much newer version had different %X placeholders and worked differently.

edit: that's what virtualbox is for :) i see that you can choose either uris and normal formats in nautilus-actions with no problem.



On a sidenote - this is a good example why insisting on gui is wrong very often. Script executed manually from command line would have done the job already, while here you need to take additional steps to pass the parameters and interpret them correctly while dealing with lack of visual feedback which makes debugging so much more annoying.

---

### Post by AlexOnVinyl on 2012-04-23
> **Vaphell said:**
> crap, you should mention that you want to run it from nautilus-scripts, i assumed running the script from the directory in question.
Imho you have approached the problem from the wrong side, you need to have a script that works in terminal first and then figure out what needs to be done to plug it in nautilus-actions.

how is the nautilus-entry set up? What is in the 'parameters' field?
If you want to run the script from n-a you can throw any *for file in *.mp3* out the window, you want *for file in "$@"*
$@ = script parameters while *.mp3 means 'in current dir find me files matching this' which ignores script params completely.

can you print the filenames passed to the script via n-a to some file?
something like *for f in "$@"; echo "$f"; done > files.txt*
i recall that n-a doesn't necessarily produces 'ordinary' names, but can spit names in uri format
file:///home/me/some%20dir/some%20file.mp3 or something like that and that would change a lot
print out names to some garbage file and see what you are dealing with exactly
I'd check that myself, but i helped once a guy with n-a and his much newer version had different %X placeholders and worked differently.

edit: that's what virtualbox is for :) i see that you can choose either uris and normal formats in nautilus-actions with no problem.



On a sidenote - this is a good example why insisting on gui is wrong very often. Script executed manually from command line would have done the job already, while here you need to take additional steps to pass the parameters and interpret them correctly while dealing with lack of visual feedback which makes debugging so much more annoying.

well, I mean if it makes any more sense, it would've worked very much similar because I had entered the directory from Nautilus.  sure Command line is good, but the scripts make it feel like I can memorize the commands without having to rewrite them each time.

---

### Post by Vaphell on 2012-04-23
> sure Command line is good, but the scripts make it feel like I can memorize the commands without having to rewrite them each time.
i am not sure i get the distinction, you can run premade scripts from command line just fine and make them as universal as you please. The only difference between running them from terminal and from n-a is the additional requirement of making them compatible with n-a or else they fail completely.

so what do you pass to the script: files you select or dir/current dir because that is still not clear to me.

---

### Post by AlexOnVinyl on 2012-04-23
> **Vaphell said:**
> i am not sure i get the distinction, you can run premade scripts from command line just fine and make them as universal as you please. The only difference between running them from terminal and from n-a is the additional requirement of making them compatible with n-a or else they fail completely.

so what do you pass to the script: files you select or dir/current dir because that is still not clear to me.

Well if the files I select can be MULTIPLE files, and the script can process as many of the files I select, then lets go with that option for the script.

If it can only handle 1 file at a time, then lets go with the dir/current half of the script.

---

### Post by Vaphell on 2012-04-24
as i said script can do whatever you want, it's you who is the bawss here, not the script ;-)

still i haven't found out what your current config is -_-
how is your nautilus-action entry set up? what did you put in command/parameters/working dir fields? %d? %F? i won't mind if you tell me what the descriptions of these placeholders are (legend window)

in your current script put that line:
```
for f in "$@"; do echo "$f"; done > /home/yourname/debug.txt
``` and after triggering your action from nautilus on few files open that debug.txt, because i really want to know what the script gets from n-a. Without it we will be going in circles unproductively and my patience will run out.
In my virtualboxed 11.04 files dumped to debug text file get %20 in place of spaces and that requires additional line of code or two. Is that the case on your system too?

---

### Post by AlexOnVinyl on 2012-04-27
> **Vaphell said:**
> as i said script can do whatever you want, it's you who is the bawss here, not the script ;-)

still i haven't found out what your current config is -_-
how is your nautilus-action entry set up? what did you put in command/parameters/working dir fields? %d? %F? i won't mind if you tell me what the descriptions of these placeholders are (legend window)

in your current script put that line:
```
for f in "$@"; do echo "$f"; done > /home/yourname/debug.txt
``` and after triggering your action from nautilus on few files open that debug.txt, because i really want to know what the script gets from n-a. Without it we will be going in circles unproductively and my patience will run out.
In my virtualboxed 11.04 files dumped to debug text file get %20 in place of spaces and that requires additional line of code or two. Is that the case on your system too?

how do I test out what my nautilus actions are - all I do is go:

```
cp scriptnamehere.sh ~/.gnome2/nautilus-scripts/
```

then I cd into the directory and apply
```
chmod +x scriptnamehere.sh
```

---

