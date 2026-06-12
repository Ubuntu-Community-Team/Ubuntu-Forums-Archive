---
title: "bash script"
date: 2010-11-11
forum: General Help
---

### Post by gmoran on 2010-11-11
I was playing around with swfextract the other day, and noticed that i could only extract one file at a time with it. So i decided to try my hand at writing a bash script to help me out. It has been a while since I last wrote one, and i'm very, [COLOR=Red]VERY[/COLOR] rusty. 

This is the script I have so far:
```

if [[ $# != 2 ]]; then
    echo
    echo "Usage: $0 <sourcefile> <pictureName>"
    echo
    exit 1
fi

[COLOR=Blue]swfextract $1 > testoutput.txt[/COLOR]
for i in $(eval echo {1.."$([COLOR=Blue]grep JPEGs testoutput.txt | cut -d ' ' -f 3[/COLOR])"})

do
    ID="$(grep JPEGs testoutput.txt | cut -d ' ' -f $(($i+5)))"
      swfextract -o "$2""$i".jpg -j "${ID/,/}" $1
done

rm testoutput.txt
```I was trying to eliminate the need to make a temporary text file while parsing the information. I have  tried a couple of variations, but cant seem to get it right. 

What i'd like to shorten is:
```

[COLOR=Blue]swfextract $1 > testoutput.txt
[/COLOR] [COLOR=Blue]grep JPEGs testoutput.txt | cut -d ' ' -f 3[/COLOR]
...
[COLOR=Blue]rm testoutput.txt
[/COLOR]
```I just don't think that it is necessary to have that temporary, I just cant seem to work it out. Any ideas?

---

### Post by DaithiF on 2010-11-11
Hi, you could do something like:

```
jpegs=$(swfextract "$1" | grep JPEGs)
jpegs=${jpegs#*ID(s) }    # strip unwanted verbiage from start, leaving just ids
IFS=", "                            # ids are separated by <comma><space>, set IFS accordingly
for jpeg in $jpegs
do
    swfextract -o "$2"$jpeg.jpg j "$jpeg" "$1"
done
```

---

