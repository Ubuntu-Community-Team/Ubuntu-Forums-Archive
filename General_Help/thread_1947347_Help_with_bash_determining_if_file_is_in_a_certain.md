---
title: "Help with bash determining if file is in a certain folder"
date: 2012-03-26
forum: General Help
---

### Post by mmonkeh on 2012-03-26
I'm making a script to check if a video file is under a certain folder and then use a certain media player if it is, I dont know how to do the part the checks if its in under a that folder though.
I want /home/me/anime/file.mkv, /home/me/anime/title/file.mkv, /home/me/anime/title/othertitle/file.mkv, etc to all be run under smplayer and everything else under vlc.

Any and all help is greatly appreciated!

this is what I have so far
```

#! /bin/bash
if $1; then
	smplayer $1
else
	vlc $1
fi

```

---

### Post by matt_symes on 2012-03-26
Hi

Does this get you nearer ?

[http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html)

Kind regards

---

### Post by SeijiSensei on 2012-03-26
Bash provides a variety of logical tests that are described on the bash man page (type "man bash" at a prompt and look for the section called "CONDITIONAL EXPRESSIONS").  Here's how I would test if a file exists:

```

if [ -s "$1" ] 
then
    do stuff
else
    do other stuff
fi

```

The -s test is true if the file exists and has a length greater than zero.  That's probably what you want.  You can include zero-length files in the existence test by using -f instead of -s.

All the spaces in the test are mandatory; bash uses space as a delimiter between operators.  So "[-s" will throw an error.

---

### Post by Nimless on 2012-03-26
I think you should try something like this, supposing you are launching the script from the folder containing the video.

```



#!/bin/bash

dir1="/home/blabla"
dir2="/home/blablabla"
dir3="/home/blablablablabla"

if [ $(pwd) == "$dir1" ] || [ $(pwd) == "$dir2" ] || [ $(pwd) =="$dir3" ];then
smplayer $1
else vlc $1
fi





```

---

### Post by TeoBigusGeekus on 2012-03-26
Something like this?
```
#!/bin/bash
folder=$(dirname $1|grep anime| wc -l)
if (( folder >= 1 )); then
    smplayer $1
else vlc $1
fi
```
If the parent directory of the file contains the word anime, then it will be played with smplayer, otherwise with vlc.

---

### Post by VCoolio on 2012-03-26
Try with "${1%/*}", which gives the full path until the filename
```

if [[ "${1%/*}" = "/your/vlcfolder" ]]; then
    vlc "$1"
else
    mplayer "$1"
fi
```

Edit: so here you go ```

if [[ "${1%/*/*/*}" = "$HOME/anime" ]]; then
    smplayer "$1"
else
    vlc "$1"
fi
```
means: if the first three folders of the path to the file you feed the script = /home/you/anime, then open with smplayer, else with vlc.

---

### Post by SeijiSensei on 2012-03-26
Why are any of these alternatives preferable to the simple -s/-f tests?  From his description, he's passing the entire file name to the script in the $1 positional parameter.

---

### Post by Nimless on 2012-03-26
> **VCoolio said:**
> Try with "${1%/*}", which gives the full path until the filename
```

if [[ "${1%/*}" = "/your/vlcfolder" ]]; then
    vlc "$1"
else
    mplayer "$1"
fi
```

Black magic ! :-P

Nice one

---

### Post by Nimless on 2012-03-26
> **SeijiSensei said:**
> Why are any of these alternatives preferable to the simple -s/-f tests?  From his description, he's passing the entire file name to the script in the $1 positional parameter.

From what I can understand the OP wants to know if a filename is in a certain folder, not if it exists.

---

### Post by VCoolio on 2012-03-26
> **SeijiSensei said:**
> Why are any of these alternatives preferable to the simple -s/-f tests?  From his description, he's passing the entire file name to the script in the $1 positional parameter.

the point isn't if a file exists, but if it is in a specific folder or subfolder thereof. But indeed, the way I proposed it needs the full filename, either ~/path/to/file or /home/him/path/to/file, so, you could make it ```
if [[ "${1%/*}" = *anime* ]]; then
   smplayer "$1"
else
   vlc "$1"
fi
```

Edit: and since I like oneliners:```
[[ "${1%/*}" = *anime* ]] && smplayer "$1" || vlc "$1"
```

---

### Post by Nimless on 2012-03-26
> **VCoolio said:**
> the point isn't if a file exists, but if it is in a specific folder or subfolder thereof. But indeed, the way I proposed it needs the full filename, either ~/path/to/file or /home/him/path/to/file, so, you could make it ```
if [[ "${1%/*}" = *anime* ]]; then
   smplayer "$1"
else
   vlc "$1"
fi
```

Edit: and since I like oneliners:```
[[ "${1%/*}" = *anime* ]] && smplayer "$1" || vlc "$1"
```

The oneliner doesn't work, I don't think you can use *anime*

Also from what I can see ""${1%/*}" expands to "filename" to me, not folder.

Edit : it expands correctly only if you type full path like ./script /home/user/video

---

### Post by VCoolio on 2012-03-26
> **Nimless said:**
> The oneliner doesn't work, I don't think you can use *anime*

Also from what I can see ""${1%/*}" expands to "filename" to me, not folder.

Edit : it expands correctly only if you type full path like ./script /home/user/video
Ah, so if you feed it only the filename is doesn't work. Right. Well, that means you're inside $HOME/anime or a subfolder, so you can do elif [[ "$PWD" = *anime* ]] open with smplayer.

Edit: example script 0.6: ```
if [[ "${1%/*}" = *anime* ]]; then
   smplayer "$1"
elif [[ "$PWD" = *anime* ]]; then
   smplayer "$1"
else
   vlc "$1"
fi
```

---

### Post by Nimless on 2012-03-26
> **VCoolio said:**
> Ah, so if you feed it only the filename is doesn't work. Right. Well, that means you're inside $HOME/anime or a subfolder, so you can do elif [[ "$PWD" = *anime* ]] open with smplayer.

Edit: example script 0.6: ```
if [[ "${1%/*}" = *anime* ]]; then
   smplayer "$1"
elif [[ "$PWD" = *anime* ]]; then
   smplayer "$1"
else
   vlc "$1"
fi
```

That works :) always nice to refresh some bash ...

---

### Post by SeijiSensei on 2012-03-26
Well if the test is whether filename.ext is in /path/anime/morepath, you can use:

```

WHERE=$(locate $1)
if [ grep anime "$WHERE" ]
then
   do stuff
else 
   do other stuff
fi

```

I encased $WHERE in double-quotes to handle cases where the path or filename includes embedded spaces.

> The oneliner doesn't work, I don't think you can use *anime*

The string "*anime*" is commonly called a "glob" where the asterisks represent arbitrary characters.  They can be used in the shell like "ls *anime*", but the equivalent in regular expressions is ".*" which represents zero or more characters.  To represent at least one other character you use ".+". If you wish to restrict the test to cases where a subdirectory is named "anime", you can use '/anime/' instead in the sample code above.

---

### Post by VCoolio on 2012-03-26
> **SeijiSensei said:**
> Well if the test is whether filename.ext is in /path/anime/morepath, you can use:

```

WHERE=$(locate $1)
if [ grep anime $WHERE ]
then
   do stuff
else 
   do other stuff
fi

```

I hadn't thought of locate, but you can 't grep a path, it will say 
grep: /path/you/fed: Is a directory
Also, why use locate and grep if bash can do it all?

---

### Post by Nimless on 2012-03-26
Yeah! I think Bash way is faster also.

---

### Post by SeijiSensei on 2012-03-26
> **VCoolio said:**
> you can 't grep a path, it will say grep: /path/you/fed: Is a directory


Try "ls -l path | grep anime".  I happen to have an anime subdirectory on my machine:

```

seiji@host:/media/storage$ ls -l | grep anime
drwxr-xr-x 120 seiji  seiji        12288 Mar 25 13:57 anime

```

You can't "grep a path" because grep applies to text strings.  You can use appropriate commands like ls or pwd to generate the text string then pipe it to grep.

---

### Post by Vaphell on 2012-03-26
and what happens if you type myplay ../something.mkv that happens to be in proper spot? :-)

my more general approach
```
#!/bin/bash

app=smplayer
defapp=vlc

appdirs=( "$HOME/test/" "$HOME/test/play/" )

if [ ! -f "$1" ]
then
  echo "error: file '$1' does not exist"
  exit 1
fi 

echo "Default app: $defapp"
echo "Exceptions ($app):"
for d in "${appdirs[@]}"
do
  echo -e "\t${d/$HOME/~}"
done

case $1 in
  */*) # some kind of path -> cd and save pwd as fdir
    fdir=$( cd ${1%/*}; pwd )
    ;;
  *) # only filename -> fdir=$PWD
    fdir="$PWD"
    ;;
esac

runapp=$defapp
for d in "${appdirs[@]}"
do
  if [ "${d%/}" = "$fdir" ]
  then
    runapp=$app
  fi
done

echo $runapp "${1/$HOME/~}    (absolute path: '${fdir/$HOME/~}')"
#uncomment the line below to run actual program
#$runapp "$1"
```
test output:
```
~/test/play$ ./play.sh test.txt
Default app: vlc
Exceptions (smplayer):
	~/test/
	~/test/play/
smplayer test.txt    (absolute path: '~/test/play')

~/test/play$ ./play.sh ~/clip.txt
Default app: vlc
Exceptions (smplayer):
	~/test/
	~/test/play/
vlc ~/clip.txt    (absolute path: '~')

~/test/play$ ./play.sh ../int.txt
Default app: vlc
Exceptions (smplayer):
	~/test/
	~/test/play/
smplayer ../int.txt    (absolute path: '~/test')

~/test/play$ ./play.sh dir/test.txt
Default app: vlc
Exceptions (smplayer):
	~/test/
	~/test/play/
vlc dir/test.txt    (absolute path: '~/test/play/dir')
```
doesn't do patterns though (yet)

---

### Post by VCoolio on 2012-03-26
> **Vaphell said:**
> and what happens if you type myplay ../something.mkv that happens to be in proper spot? :-)


oh boy. Indeed, another bug, lol. While inside anime, you can't feed it a file outside anime or it will still use smplayer. Let me think.

Edit: got it, I think ```

if [[ "${1%/*}" = *anime* ]]; then
   smplayer "$1"
elif [[ "$PWD" = *anime* ]]; then
# if path starts with alphanumerical character, meaning it's inside anime (else it would start with /, ~ or ../ ), use smplayer
   if [[ "$1" = [[:alnum:]]* ]]; then
      smplayer "$1"
# what if inside anime user points to file using ./ ?
   elif [[ "$1" = ./* ]]; then
      smplayer "$1"
   else
      vlc "$1"
   fi
else
   vlc "$1"
fi

```
Edit 2: not accounted for: using ../ inside a subfolder of anime, and pointing to hidden files without preceding path from inside anime (they start with a dot, so are opened with vlc now). The op now has the tools to write his own if loops, so I bail.

---

