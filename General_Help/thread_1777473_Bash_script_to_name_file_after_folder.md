---
title: "Bash script to name file after folder?"
date: 2011-06-07
forum: General Help
---

### Post by Mega_Mike on 2011-06-07
Question for people good with Bash scripts.

In a script, how do you name a file after a folder?

For example:  

I want to rename the mkv in this folder
```
/home/user/Movies/Terminator/title01.mkv
```

to 

```
/home/user/Movies/Terminator/Terminator.mkv
```

So the pattern is 
```
/home/user/Movies/${MOVIE_NAME}/title[0-9]*.mkv
```

and end up with

```
/home/user/Movies/${MOVIE_NAME}/${MOVIE_NAME}.mkv
```

Any idea how to do this?

---

### Post by sisco311 on 2011-06-07
Sorry, I'm not sure if I understand this correctly. There is a single .mkv file in each ${MOVIE_NAME} directory or you want to join multiple title*.mkv into one .mkv file named after the directory?

---

### Post by nothingspecial on 2011-06-07
While I am loath to follow sisco with any advice .......


....... perhaps look at basename

---

### Post by sisco311 on 2011-06-07
> **nothingspecial said:**
> 
....... perhaps look at basename

(In bash) there is no need for *basename* and *filename*, [parameter expansion]("http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion") should do the trick.

Something like:
```

#!/bin/bash

shopt -s nullglob

cd ~/Movies
for path in */*.mkv
do 
  dir="${path%/*}"
  file="${path##*/}"

  echo "directory: ${dir}"
  echo "file: ${file}"
  echo
done

```

---

### Post by nothingspecial on 2011-06-08
**@Mega_Mike sorry I hijacked this thread a little, however the instruction from sisco311 due to the hijack is useful and (vaguely) relevant. I hope you don't mind :)**


Ok then, Mr Ubuntu Member (congratulations btw :P)

Improve this one. I used it to copy one (didn't matter which) album cover from an album directory, into the artist directory of my music folder so that nautilus cover thumnailer would show a picture when browsing my Music directory.

```
IFS=$'\n'; for f in $(find -L Music -type f -name 'cover.jpg'); do t=$(dirname "$f"); cp -nv "$f" $(dirname "$t"); done
```

Music is organised ~/Music/Artist/Album/cover.jpg and I wanted one cover.jpg to be copied to ~/Music/Artist

What should I have done?

Thanks

---

### Post by sisco311 on 2011-06-08
> **nothingspecial said:**
> Ok then, Mr Ubuntu Member (congratulations btw :P)



Thanks! :)

> **nothingspecial said:**
> 
What should I have done?


I don't even know where to start. :)

The
```
for file in $(find PATH OPTIONS); do ...
```
syntax is WRONG! See: [BashPitfalls #1]("http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29")


If you reset IFS, you have to restore it:
```
oIFS="$IFS"; IFS=$'\n'; command; IFS="$oIFS"
```
Especially if you are working in an interactive shell.


Of course, find is a very powerful command. If you really have to use it, you must do something like:
```

while IFS= read -r -d '' file
do
  echo "$file"
done< <(find PATH OPTIONS -print0)
```

All cover.jpg files are at the same level in the directory hierarchy so there is no need for a recursive search:
```

#!/bin/bash
shopt -s nullglob

cd ~/Music
for path in */*/cover.jpg
do
  artist="${path%%/*}"
  cp -- "$path" "$artist"
done

```

But, as I said before, find is very powerful.

We want to find each cover.jpg file from the *album* directories:
```
find ~/Music -mindepth 3 -maxdepth 3 -iname 'cover.jpg' -type f
```

*NOTE: The -name test comes before the -type test in  order  to  avoid having to call [noparse]stat(2)[/noparse] on every file. We only want to know if cover.jpg is a file or not, we don't care about the rest.*

and copy them in their parent directory:
```
find ~/Music -mindepth 3 -maxdepth 3 \
-iname 'cover.jpg' -type f \
-execdir cp -- '{}' ../ \;
```

---

### Post by nothingspecial on 2011-06-08
> I don't even know where to start.
:lolflag:

> syntax is WRONG! See: BashPitfalls #1

I know that, but I also know _**for a fact**_ that all the files are called cover.jpg

> If you reset IFS, you have to restore it:

I also know that, but it was an 'open a terminal, execute, close' job.

> find is a very powerful command

I know that, it is the reason why I have the quote I have in my sig due to a monumental cockup a while back. Of course I always follow the advice in my sig when using find.

> for path in */*/cover.jpg

that's the bit that got me, =D> . I  think I was using ../../cover.jpg I can't remember for sure and I only have my history set to 1000, but I know I didn't try that.

> NOTE: The -name test comes before the -type test in order to avoid having to call stat(2) on every file. We only want to know if cover.jpg is a file or not, we don't care about the rest.

noted, thankyou very much :) (obvious really, but easily over looked)

I really did try with paramater expansion etc, but failed due to the mistake above. In the end I managed it with what I posted above, which, truth be told, worked even if it was entirely the wrong way of doing it............

........... but then there's no point knowing a Ubuntu member if you can't take advantage is there. :P

Cheers.

I'd like to point out that I have my wife and kids music here too :-\"

[ATTACH]194556[/ATTACH]

---

### Post by Mega_Mike on 2011-06-08
> **sisco311 said:**
> Sorry, I'm not sure if I understand this correctly. There is a single .mkv file in each ${MOVIE_NAME} directory or you want to join multiple title*.mkv into one .mkv file named after the directory?

Sorry, the regex got a little weird.  Exactly ONE mkv in the folder.  No file joining.

---

### Post by Mega_Mike on 2011-06-08
Awesome help Sisco.  You gave me what I needed to put it all together. The finished script to move the MKV files made from MakeMKV (minus the test data part) is:


```

#!/bin/bash

echo Creating test folder and file...to delete later
mkdir ~/Videos/Terminator
touch ~/Videos/Terminator/title01.mkv

shopt -s nullglob

cd ~/Videos
for path in */*.mkv
do 
  dir="${path%/*}"
  file="${path##*/}"

  if [ "${dir}" != "Movies" ]; then
    echo "Moving ${file} to ${dir}.mkv in Movies directory"
    mv ~/Videos/${dir}/${file} ~/Videos/Movies/${dir}.mkv
    echo "Deleting ${dir} directory created by MakeMKV"
    rmdir ~/Videos/${dir}
  fi
done
```

---

### Post by sisco311 on 2011-06-08
Cool! I'm glad you figured it out!

---

### Post by seanbw on 2011-06-10
> **sisco311 said:**
> Sorry, I'm not sure if I understand this correctly. There is a single .mkv file in each ${MOVIE_NAME} directory or you want to join multiple title*.mkv into one .mkv file named after the directory?

Please forgive me but I have a similar problem but the complexity of mine is that I have several 'mkv files I want to join afterwards the problems are the same i.e. after joining, I would like to copy (or move) the cover.jpg (which in certain cases may be more than 1) to the same folder where the joined up files are.

Between all of you are you able to amend mega_mikes' final script to do the joining, renaming (.mkv and .jpg),moving etc. The only difference I think is the joining of several .mkv files into 1 and renaming multiple .jpg files to the folder_name-1....folder_name-n.

PS: Since I started using Ubuntu 2 years ago, I have prided myself in learning titbits of Linux but can I just say, quite simply that I do not have one iota of understanding of what your scripts (all of you) mean. For the second time I come across a script that looks like Greek to me. Either this is a very complicated script or you are all from another planet and I am coming down gently to the latter opinion. quite simply.;)

---

