---
title: "Command line syntax"
date: 2012-01-15
forum: General Help
---

### Post by inhumangeek on 2012-01-15
Hi,

I'm sure there is a very simple answer for this. I use quick bash/ksh "for" loops at work (Centos) for doing little jobs, a simple example (NOT what I am actually doing, obviously!):
```
for file in `ls *.avi`
do
echo $file
done
```
Would produce (I think)
```
01 Episode 1.avi
02 Episode 2.avi
```
However the behaviour at home (Ubuntu) is slightly different when it is handling files with spaces in them. Here, it keeps breaking the filenames at the spaces... for example:
```
01
Episode 
1.avi
02
Episode 
2.avi
```
What escape characters / quotes etc do I need to use, and where, in order to get the output line joined? For info, examples of an actual loop I want to use is:
```
for file in `ls -R *.avi` 
do 
HandBrakeCLI -i $file -o ${file%.avi}.mkv
done

or 

for file in `find . -name "*.avi"`
do
HandBrakeCLI -i $file -o ${file%.avi}.mkv
done
```
And I know I can use [FONT="Courier New"]find -exec[/FONT] but there are more complicated scripts I want to write, for which I cannot use [FONT="Courier New"]find -exec[/FONT]. (E.g.  In the HandBrake example above, if I used [FONT="Courier New"]find -exec[/FONT], I don't believe I can change the output file extension in the same way with [FONT="Courier New"]{}[/FONT]).

Thanks.

---

### Post by Vaphell on 2012-01-15
you are doing it very wrong
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)

shell has a native support for filename patterns so you don't have to parse output of ls or find to get the file list

```
for f in *.avi
do
  some_command "$f" # double quotes prevent breaking into pieces at spaces
done
```

if you want to go recursive
```
shopt -s globstar # enables recursive matching with **

for f in **/*.avi
do
  some_command "$f"
done
```

and if you can't use that, pipe \0-delimited list from 'find' to 'while read'
```
find . -name '*.avi' -print0 | while read -d $'\0' f
do
  some_command "$f"
done
```

---

### Post by inhumangeek on 2012-01-16
That's great thanks. I knew it would be something like that.

---

