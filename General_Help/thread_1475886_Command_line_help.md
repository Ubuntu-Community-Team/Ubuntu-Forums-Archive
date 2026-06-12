---
title: "Command line help"
date: 2010-05-07
forum: General Help
---

### Post by hiding on 2010-05-07
Hi, I have a naive query about commands.

I'm reripping hundreds of CDs to mp3, replacing files with very low bit rates with much higher bit rates. However, I have already been through a long and laborious process of editing the id3 tags of the existing poor quality files to my preferred style. 

I don't fancy repeating this process (we're talking 10s of thousands of tracks), so I've been looking for a way of copying the tags from the older files into the tags of the new files.

After some googling, the only way I could find of doing this was using id3 mass tagger...

[http://home.wanadoo.nl/squell/id3.html](http://home.wanadoo.nl/squell/id3.html)

... using the commands of the form...

id3 -D source.mp3 -1 -2 dest.mp3 

So I've been copying the old folder into the new folder and copying the tags like this...

~/music/Oxes - Oxxxes$ id3 -D Oxes\ -\ Oxxxes/01* -1 -2 01*

However, at the moment this is absurdly labour-intensive as it involves me changing 01* to 02*, then to 03*, etc.

So basically, I can't work out how to make the id3 tags from the old files copy to the tags from the new files, en masse, rather than manually doing it one-by-one. 

I feel like there is probably a simple solution to this, but I'm not yet sufficiently familiar with using commands to work it out.

Any help much appreciated.

---

### Post by StuartN on 2010-05-07
> **hiding said:**
> However, at the moment this is absurdly labour-intensive

It is amazing how our definitions of labour-intensive have changed... but I hate being slave to the machine.

If your new files are in /home/me/new and your old files are in /home/me/old and you are sure that there is an old file, with the same filename, for every new file, you could use something like:

```

cd /home/me/new
for file in $(ls) ; do
  id3 -D /home/me/old/$file -1 -2 /home/me/new/$file
done
```
(up to you to be sure of the syntax, especially which is source and which destination)

I guess you could do something similar with find, which would be recursive.

---

### Post by oaxacamatt1 on 2010-05-07
Dude,
You should consider 'Sound Converter' for one.  It is a prog that allows you to re-code flacs to mp3 (or whatever) or it can be setup to lower bit rates, too.
M

---

### Post by hiding on 2010-05-07
> **oaxacamatt1 said:**
> Dude,
You should consider 'Sound Converter' for one.  It is a prog that allows you to re-code flacs to mp3 (or whatever) or it can be setup to lower bit rates, too.
M

I'm familiar with Sound Converter: surely no good for my purposes though - I want to end up with files with *higher* bit rates.

---

### Post by hiding on 2010-05-07
> **StuartN said:**
> 
If your new files are in /home/me/new and your old files are in /home/me/old and you are sure that there is an old file, with the same filename, for every new file, you could use something like:
```

cd /home/me/new
for file in $(ls) ; do
  id3 -D /home/me/old/$file -1 -2 /home/me/new/$file
done
```
(up to you to be sure of the syntax, especially which is source and which destination)


Thanks for that.

At the risk of turning this into a basic command line tutorial, would it be possible to briefly explain what is going on in this code.

---

### Post by StuartN on 2010-05-07
> **hiding said:**
> At the risk of turning this into a basic command line tutorial, would it be possible to briefly explain what is going on in this code.

The for loop (for variable in list ; do some commands ; done) will run all the commands inside the loop for each value in the list.

The list needs to contain all the mp3 filenames, and I am assuming that this will be all the files in /home/me/new, so ls would list them and $(ls) returns the list as a parameter to the for command. (You might want to use $(ls *.mp3) or $(ls *.mp3 *.MP3) to exclude other files).

For simplicity I used cd /home/me/new before the loop so that ls returns filenames without a path. The command basename $file could be used to strip off the path if this was not the case.

And I do not know the syntax for id3...

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) is useful, and there are many more guides to bash scripting.

---

### Post by hiding on 2010-05-07
Okay, I understand all that now - thanks a lot!

One more thing though...

When I use the above commands I get results like the one below:

> 
~/music/Oxes - Oxxxes$ for file in $(ls); do id3 -D old/$file -1 -2 $file; done

id3: note: could not read tags from old/02
id3: no files matching 02
id3: note: could not read tags from old/Half
id3: no files matching Half
id3: note: could not read tags from old/Half
id3: no files matching Half
id3: note: could not read tags from old/&
id3: no files matching &
id3: note: could not read tags from old/Half.mp3


I take it that this is because my mp3 files names all have spaces in them.

How do I get around this?

---

### Post by WorMzy on 2010-05-07
Use quotes, so ```
for file in "$(ls)"; do id3 -D "old/$file" -1 -2 "$file"; done
``` should work.

---

### Post by hiding on 2010-05-07
Are you sure? This gives me...

```
~/music/Oxes - Oxxxes$ for file in "$(ls *mp3)"; do  
id3 -D "old/$file" -1 -2 "$file"; done
id3: note: could not read tags from old/01 Boss Kitty.mp3
02 Half Half & Half.mp3
03 Kaz Hayashi '01.mp3
04 Chyna, Chyna, Chyna.mp3
05 Tony Baines.mp3
06 Take & Free Miami.mp3
07 Bees Won.mp3
08 Russia is Here.mp3
id3: no files matching 01 Boss Kitty.mp3
02 Half Half & Half.mp3
03 Kaz Hayashi '01.mp3
04 Chyna, Chyna, Chyna.mp3
05 Tony Baines.mp3
06 Take & Free Miami.mp3
07 Bees Won.mp3
08 Russia is Here.mp3
```

... whereas...

```
for a in $(ls *mp3); do id3 -D old/$a -1 -2 $a; done
```

...in a folder where the file names don't contain any spaces works fine.

Hmmm...

---

### Post by WorMzy on 2010-05-07
Sorry, remove the quotes from the first part ```
"$(ls *mp3)"
``` I don't know why I put them around there, ls always returns full file names anyway.

---

### Post by hiding on 2010-05-07
That takes me back to... ```
~/music/Jandek - Six and Six$ for file in $(ls); do 
id3 -D "old/$file" -1 -2 "$file"; done
id3: note: could not read tags from old/01
id3: no files matching 01
id3: note: could not read tags from old/Feathered
id3: no files matching Feathered
id3: note: could not read tags from old/Drums.mp3
id3: no files matching Drums.mp3
id3: note: could not read tags from old/02
id3: no files matching 02
id3: note: could not read tags from old/Point
id3: no files matching Point
id3: note: could not read tags from old/Judith.mp3
id3: no files matching Judith.mp3

```

...again

---

### Post by StuartN on 2010-05-07
> **hiding said:**
> That takes me back to...

The problem is that $(ls) is returning one line per filename, but the for command defaults to using a space as delimiter. You need to specify a newline character ($'\n') as separator:

```
IFS=$'\n'
for file in $(ls); do 
  id3 -D "old/$file" -1 -2 "$file"
done
```
(You could stick it all on one line using ; to separate commands)

---

### Post by WorMzy on 2010-05-07
You're right. It seems the problem lies in how the output ls is assigned to the file variable. No quotes makes it break off at whitespace, whereas with quotes, it takes the entire output of ls and only runs the loop once.

I think the answer must lie in dealing with the whitespace, returned by ls, but I have no idea how to do that in a way that variable assignment will honour. For example ls -b will append an escape character before the space, which most applications will honour, but for some reason variable assignment doesn't.

Here is a link to someone that had a similar problem: [http://www.linuxquestions.org/questions/programming-9/bash-ls-for-loops-and-whitespaces-in-directories-126388/](http://www.linuxquestions.org/questions/programming-9/bash-ls-for-loops-and-whitespaces-in-directories-126388/)

---

### Post by hiding on 2010-05-07
> **StuartN said:**
> The problem is that $(ls) is returning one line per filename, but the for command defaults to using a space as delimiter. You need to specify a newline character ($'\n') as separator:

```
IFS=$'\n'
for file in $(ls); do 
  id3 -D "old/$file" -1 -2 "$file"
done
```


Great, again you've sorted the problem.

For fear of sounding as if there's an ever-shifting set of goalposts - if someone could help me work out how to copy from a file that just matches the beginning of the file name, not the whole thing, I'd be totally sorted.

So, I'm looking to copy from the tag of...

old/05 Wild Strawberries.mp3

... to the tag of...

05.mp3

I understand the rudiments of wildcards, but once this for loop and the quoting enters the equation by head starts to spin.

Anyone?

---

### Post by StuartN on 2010-05-07
> **hiding said:**
> So, I'm looking to copy from the tag of...

old/05 Wild Strawberries.mp3

... to the tag of...

05.mp3

Within the loop, if $file is the string you are searching, then $dest_file could be found with bash search, looking for space followed by anything (\ *):

```
for ... ; do
  dest_file=${file%%\ *}
  id3 .. $dest_file
done
```

{var%%pattern} finds the shortest match (i.e. first space), {var%pattern} finds the longest (i.e. last space).

(Here is an explanation of bash trim [http://tldp.org/LDP/LGNET/18/bash.html](http://tldp.org/LDP/LGNET/18/bash.html))

---

### Post by dracayr on 2010-05-07
well, firstly, I'm quite sure that that $(ls) was unnecessary anyway (please correct me if you know better!). 'for i in *.mp3' would have worked.

now, to change the filename into only the track number (assuming there are always 2 digits at the beginning of the filename):
we'll use sed. The command ```
echo 01\ These\ Woods\ Breathe\ Evil.mp3 |sed -e "s/.*\([0123456789]\{2\}\).*\.mp3/\1/"
```
filters the Track name, and returns simply 01 in this case.
so, your for loop:```
for file in old/*.mp3; do 
  id3 '$file' -1 -2 `echo $file|sed -e "s/.*\([0123456789]\{2\}\).*\.mp3/\1/"`.mp3
done
```

dracayr

---

### Post by StuartN on 2010-05-07
> **dracayr said:**
> well, firstly, I'm quite sure that that $(ls) was unnecessary anyway (please correct me if you know better!).

That was my fault - I had in mind that the mp3 collection may be vast and structured, so feeding the loop off $(...) would allow a hierarchical find, but was not thinking of spaces in filenames...

Incidentally, **ls *.mp3 | while read file ; do ... "$file" ; done** might have been simpler.

---

### Post by hiding on 2010-05-07
Thanks for the responses. It's going to take me a little while to get my head around all that but it looks promising.

---

### Post by hiding on 2010-05-08
Okay, so I haven't got my head around StuartN's solution yet. I'll keep trying to fathom that one.

After a small amount of fiddling with dracayr's solution I ended up with...```
IFS=$'\n'
for file in old/*.mp3; do 
  id3 -D $file -1 -2 `echo $file|sed -e "s/.*\([0123456789]\{2\}\).*\.mp3/\1/"`*.mp3
done
```
...which works.

However, I figured by analogy that... ```
for file in old/*.mp3; do 
    mv `echo $file|sed -e "s/.*\([0123456789]\{2\}\).*\.mp3/\1/"`* $file
done
```
... would rename the new files with the old file names, but it doesn't. 

I think this is because it is moving the new files to /old

So (brace yourselves for a dumb question) how do I get it to write to folder the new files are in, the directory above /old (and thus rename the files rather than move them).

---

### Post by StuartN on 2010-05-08
> **hiding said:**
> After a small amount of fiddling with dracayr's solution I ended up with...
So (brace yourselves for a dumb question) how do I get it to write to folder the new files are in, the directory above /old (and thus rename the files rather than move them).

If you add a few lines to set old and new filename variables (and print them out for debugging), this should work:

```
IFS=$'\n'
for file in old/*.mp3; do
  new=$(echo $file | sed -e "s/.*\/\([0-9]*\) .*/\1/").mp3
  old=$(basename "$file")
  echo "old=$old, new=$new"
  id3 -D "$file" -1 -2 "$new"
  mv "$new" "$old"
done
```

---

