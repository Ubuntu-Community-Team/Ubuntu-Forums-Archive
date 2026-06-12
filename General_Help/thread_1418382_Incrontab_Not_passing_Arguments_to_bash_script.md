---
title: "Incrontab Not passing Arguments to bash script"
date: 2010-02-28
forum: General Help
---

### Post by mattnewham on 2010-02-28
Hello

Just for clarification. It seems incrontab wont see spaces properly at all. I setup a script to echo the arguments passed to it by incrontab to a file, and no matter what I put around the arguments on the incrontab file it will count a space as the next argument. Anyone got any idea whats going on?


I have written a script to automatically retrieve imdb artwork for a given filename. Here is the script:
```

#!/bin/bash

input=$1
#echo "$1" > /home/mattnewham/Desktop/log.txt

location=$2

#echo "$input" > /home/mattnewham/Desktop/log.txt
#echo "$location" >> /home/mattnewham/Desktop/log.txt

search_term=$(echo "${input##*/}"| sed -e 's/ /+/' -e 's/\.[^\.]*$//')

#echo "$search_term" > /home/mattnewham/Desktop/log.txt

movie_cover=$(wget -U firefox -qO - "http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+${search_term}&btnI=I%27m+Feeling+Lucky&meta=" | grep -A1 -i '<div class="photo">' | sed -n "2 p" | sed "s|.*src=||" | cut -d\" -f2)

#echo "$movie_cover" > /tmp/movie_cover

big_pic=$(sed -e 's/SX[0-9]*/SX600/g' -e 's/SY[0-9]*/SY600/g' /tmp/movie_cover)

#echo "$big_pic"

image_name=$(echo "$input" | sed -e 's/\.[^\.]*$//')

#echo "$image_name"

wget -U firefox -q "$big_pic" -O "/home/mattnewham/Desktop/Imagedrop/$image_name.jpg"
#echo $big_pic
```

You can ignore all the commented "echo" commands that was just me testing. Anyway, the script work fine, however I am trying to use incrontab to monitor a folder, when a new (video) file is moved into the folder, it should execute the script and retrieve the artwork. My problem is, when incrontab passes the $# argument to my script, the script wont work because the spaces aren't escaped. Here is some more detail:

Incrontab

```
/home/<my username>/Desktop/Imagedrop IN_MOVED_TO /home/<my username>/.GetArtwork.sh $# $@
```

Syslog output

```
CMD (/home/<my username>/.GetArtwork.sh Bangcock Dangerous.avi /home/<my username>/Desktop/Imagedrop)
```

The problem is, the script GetArtwork, doesn't see "Bangcock Dangerous" it just sees "Bangcock"

I have tried putting quotes around the $# in the incrontab - this just makes the script see "Bangcock (notice the single quote character) - Im getting majorly fed up now I've been at this for hours!

Please help!

---

### Post by dcstar on 2010-02-28
> **mattnewham said:**
> 
..........
You can ignore all the commented "echo" commands that was just me testing. Anyway, the script work fine, however I am trying to use incrontab to monitor a folder, when a new (video) file is moved into the folder, it should execute the script and retrieve the artwork. My problem is, when incrontab passes the $# argument to my script, the script wont work because the spaces aren't escaped. Here is some more detail:

Incrontab

```
/home/<my username>/Desktop/Imagedrop IN_MOVED_TO /home/<my username>/.GetArtwork.sh $# $@
```

Syslog output

```
CMD (/home/<my username>/.GetArtwork.sh Bangcock Dangerous.avi /home/<my username>/Desktop/Imagedrop)
```

The problem is, the script GetArtwork, doesn't see "Bangcock Dangerous" it just sees "Bangcock"

I have tried putting quotes around the $# in the incrontab - this just makes the script see "Bangcock (notice the single quote character) - Im getting majorly fed up now I've been at this for hours!

Please help!

**$#** is the number of command line arguments:

[http://www.shelldorado.com/goodcoding/cmdargs.html](http://www.shelldorado.com/goodcoding/cmdargs.html)

---

### Post by mightybs on 2011-03-21
@dcstar - while you would be correct if you were talking about a Bash script, the $# is the "event-related file name" for incron.

@mattnewham - I've discovered this trouble as well, and I believe it is an incron bug that is improperly escaping the argument when it contains spaces.  I'll be investigating further to report my findings to the authors, and possibly provide a patch.

  As this post is rather old I realize you may have a solution already, but I'll add this for anyone finding this page in the future.  I used the $# as the last argument to my Bash script so that I could take all of the input as a single variable.

Sample incrontab line:

```
/watched_dir   IN_CLOSE_WRITE,IN_MOVED_TO /script_to_run $% $@ $#

```

Knowing that $% doesn't have spaces in it, and in my case I know the watched directory does not have any spaces in it I can do this:

```
event=$1
event_dir=$2
shift ; shift
event_file="$*"

```

This way you take any arguments after the first 2 (which I know don't have spaces) and use them as the file name.

---

