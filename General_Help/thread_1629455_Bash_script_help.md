---
title: "Bash script help"
date: 2010-11-23
forum: General Help
---

### Post by inameiname on 2010-11-23
I'm trying to make a script that will convert phone numbers to letters just for fun. Currently, I have made one that sort of works, (using parts of a few others), but it outputs one possibility at a time. I would like it to output all of the possible choices, ideally in alphabetical order so one can see and find their favorite easily. Here is my script, so far:

```

#!/bin/bash

array2=(
A B C
)
MODNUM2=${#array2
[*]}
index2=$(($RANDOM%$MODNUM2))
array3=(
D E F
)
MODNUM3=${#array3
[*]}
index3=$(($RANDOM%$MODNUM3))
array4=(
G H I
)
MODNUM4=${#array4
[*]}
index4=$(($RANDOM%$MODNUM4))
array5=(
J K L
)
MODNUM5=${#array5
[*]}
index5=$(($RANDOM%$MODNUM5))
array6=(
M N O
)
MODNUM6=${#array6
[*]}
index6=$(($RANDOM%$MODNUM6))
array7=(
P Q R S
)
MODNUM7=${#array7
[*]}
index7=$(($RANDOM%$MODNUM7))
array8=(
T U V
)
MODNUM8=${#array8
[*]}
index8=$(($RANDOM%$MODNUM8))
array9=(
W X Y Z
)
MODNUM9=${#array9
[*]}
index9=$(($RANDOM%$MODNUM9))

echo -n "Enter number : "
read n

len=$(echo $n | wc -c)
len=$(( $len - 1 ))

echo "Your number $n in words : "
for (( i=1; i<=$len; i++ ))
do
   # get one digit at a time
    digit=$(echo $n | cut -c $i)
   # use case control structure to find phone number in letters/words
    case $digit in
        0) echo -n "0" ;;
        1) echo -n "1" ;;
        2) echo -n "${array2[$index2]}" ;;
        3) echo -n "${array3[$index3]}" ;;
        4) echo -n "${array4[$index4]}" ;;
        5) echo -n "${array5[$index5]}" ;;
        6) echo -n "${array6[$index6]}" ;;
        7) echo -n "${array7[$index7]}" ;;
        8) echo -n "${array8[$index8]}" ;;
        9) echo -n "${array9[$index9]}" ;;
    esac
done

# just print new line
echo ""

```Also, it would be great to be able to add the ability to have it look in a dictionary, such as '/usr/share/words' and find actual words, but that's asking for a lot. This might also mean adding an extra letter or something so as to make an actual word, which would mean adding an 8th number in a US number, which wouldn't really matter.

Thanks in advance. Of course, if someone has a better script, I'd love to have a look as I'm not very good with scripting and I know this is a bit rough of one.

---

### Post by inameiname on 2010-11-24
Bump

---

### Post by asmoore82 on 2010-11-24
Not too shabby.

Here's my stab at it:
```
[COLOR="Blue"]#!/bin/bash
#This file is in the Public Domain.[/COLOR]

echo -n "Enter number: "
read num

[COLOR="Blue"]#Create a list of possibilites for expansion by the shell
# the "\}" is an ugly hack to get "}" into the replacment string -
# this is not a clean escape sequence - the litteral "\" is left behind![/COLOR]
num="${num//2/{a,b,c\}}"
num="${num//3/{d,e,f\}}"
num="${num//4/{g,h,i\}}"
num="${num//5/{j,k,l\}}"
num="${num//6/{m,n,o\}}"
num="${num//7/{p,q,r,s\}}"
num="${num//8/{t,u,v\}}"
num="${num//9/{w,x,y,z\}}"

[COLOR="Blue"]#cleaup from the hack - remove all litteral \'s[/COLOR]
num="${num//\\/}"

echo ""
echo "Possible words are:"
for word in $( eval echo "$num" )
do
    echo '>' "$word"
done

[COLOR="Blue"]#End of File[/COLOR]
```

Of course that dictionary feature is where the real fun is. My first thought on this whole concept was that it would be a perfect opportunity to use my Go To Guy, the `tr` command. I was able to squeak through the above script without using it. But I'm convinced that the answer to the dictionary feature lies in starting with the answer and working backwards.

`tr` makes translating the words to numbers trivially easy:
```
tr 'a-z' '2223334445556667777888999'
```

Since the mapping of letters to numbers is a many to one relationship, it's much easier to work from this side. Given a list of valid words, it's much easier to generate a list of lucky number combinations than it is to brute force valid word combinations from numbers.

My current words file is 98569 lines:```
cat /usr/share/dict/words | wc
```

Take out words with apostrophes, we're down to 74059: ```
cat /usr/share/dict/words | grep --invert-match \' | wc
```

Force them to lowercase, map them to numbers, filter them down to near telephone legnth, sort and unique them: ```
cat /usr/share/dict/words | tr 'A-Z' 'a-z' |
tr 'a-z' '22233344455566677778889999' |
egrep '^[[:digit:]]{3,8}$' | sort -n | uniq | wc
```^Whew! We're down to only 36045 lucky numbers that can actually fit into words.

That's as far as I've gotten, the next problem is that the smaller lucky numbers can easily be substrings of a larger telephone number. And I don't actually have a map of the valid words.

---

### Post by inameiname on 2010-11-24
Oh wow, thank you for the script, [asmoore82]("http://ubuntuforums.org/member.php?u=341737"). Definitely much more cleaner than mine. Plus it both gives all possible outputs and sorts them as well. Awesome.

The dictionary thing would certainly be a great addition. Even as I mentioned above, adding the ability to have it search through the dictionary and find words that might be a digit or two longer too would be great, so a number that say generates 'carligh' can automatically generate 'carlight'. I also thought about implementing /usr/share/words into it, as I have a few other scripts that do that very thing. Here is one of them. Although it's a python script, it uses the dictionary quite well in searching for anagrams for whatever word I input:

```

#!/usr/bin/python
infile = open ("/usr/share/dict/words", "r")
## "dict" is a reserved word
words_in = infile.readlines()
scrambled = raw_input("Enter the scrambled word: ")
scrambled = scrambled.lower()
scrambled_list = list(scrambled)
scrambled_list.sort()
for word in words_in:
    word_list = list(word.strip().lower())
    word_list.sort()
    ## you don't really have to compare lengths when using lists as the
    ## extra compare takes about as long as finding the first difference
    if word_list == scrambled_list:
        print word, scrambled

```

I doubt it'd help...

Anyway, it'd be interesting to know what sort of codes those online phone numbers-to-words sites use. It'd be one great thing to include here.

Thanks for the help. I'm still amazed I haven't run across a script that has already been made for this.

---

