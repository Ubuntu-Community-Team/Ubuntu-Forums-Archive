---
title: "BASH: Spaces in argument filename"
date: 2010-08-31
forum: General Help
---

### Post by m6a2x6 on 2010-08-31
Hi!

I'm new to bash scripting and have some difficulties with a script I'm working on. Basically, it's just a shortcut to give arista-transcode the right parameters. So instead of doing:

```
$ arista-transcode -dps3 movie.wmv movie.avi
```

I want to just do

```
$ my-script movie.wmv
```

I finally got to some solution that looks like that

```
#!/bin/bash
FILE=$1
EXT=".avi"

LEN=`expr length "$1"`
LEN=($LEN-4)
echo "LEN="$LEN
FILE=${FILE:0:${LEN}}
FILE=${FILE}${EXT}
echo $1"=>"$FILE

eval "arista-transcode -dps3 \"$1\" \"$FILE\""
```

It seems to be working now, but I need some explanations on why it does :-p I was despaired and trying randoms things when I remarked LEN=($LEN-4) does work in the substring but if echoed it returns (for example a 24 char name) "24-4" instead of "20"

Why is that strange behavior? I must admit I don't fully understand what I am doing right now ;-)

EDIT:Sorry for the misleading title I cant seem to modify it.

---

### Post by Ginsu543 on 2010-08-31
The reason LEN=($LEN-4) gives 24-4 instead of 20 is that you've defined LEN to be a text string, not an integer value string. To get 20 (i.e., the result of the mathematical operation), you need to define LEN=$(($LEN-4)).

---

### Post by amauk on 2010-08-31
Something like this may be better
(doesn't rely on hard-coded length of extension)

This erases the last dot (and everything after) from the filename, and adds the new extension

also added a quick check to make sure the orig file exists

```
#!/bin/bash

if [ -z "$1" ] || [ ! -f "$1" ]; then
	# file not found
	exit 1
fi

FILE=$1
EXT=".avi"

ORIG_EXT=${FILE##*.}
FILE="$(echo "$FILE" | sed "s|\.${ORIG_EXT}$||")${EXT}"

echo "$1=>$FILE"
eval "arista-transcode -dps3 \"$1\" \"$FILE\""
```

---

### Post by m6a2x6 on 2010-08-31
Thank you!

Just some things for me to understand:
```
LEN=$(($LEN-4))
```
($LEN-4): the string "24-4"
$(($LEN-4)) = $("24-4") : the integer 20

So the $() works a little like eval?

```
${FILE##*.}
```

How the ##*. works to keep the extension?

```
FILE="$(echo "$FILE" | sed "s|\.${ORIG_EXT}$||")${EXT}"
```

If I understand:
Passes the filename and uses sed to replace the original extension by nothing and concatenate the new extension.

Would this work?
```
FILE="$(echo "$FILE" | sed "s|\.${ORIG_EXT}$|${EXT}|")"
```

---

### Post by amauk on 2010-08-31
> **m6a2x6 said:**
> So the $() works a little like eval?Kind of
It's called command substitution
it's used to capture the output of commands/expressions and pass them back in to further commands

Eval just evaluates a string as a command

> **m6a2x6 said:**
> ```
${FILE##*.}
```

How the ##*. works to keep the extension?This one's a little difficult to explain (although it's purpose becomes obvious with use)

It's one of Bash's parameter expansions
Before the ## is our FILE variable, after the ## is our deletion expression

The value of FILE is expanded, then the deletion expression is run over the value

The ## means "match the largest possible sequence
(meaning it matches everything up to the final dot, as opposed to a single #, which would be the smallest possible sequence, and match up to the first dot)

Anything matched is deleted
(hence it returns the file extension)

> **m6a2x6 said:**
> ```
FILE="$(echo "$FILE" | sed "s|\.${ORIG_EXT}$||")${EXT}"
```

If I understand:
Passes the filename and uses sed to replace the original extension by nothing and concatenate the new extension.

Would this work?
```
FILE="$(echo "$FILE" | sed "s|\.${ORIG_EXT}$|${EXT}|")"
```
Yes, although I thought it best to append the new extension even if no original extension was present (to guarantee that the orig & new filenames were different)

---

### Post by gmargo on 2010-08-31
I don't see why you're using **eval**.  You can run the command directly:
```

arista-transcode -dps3 "$1" "$FILE"

```

---

### Post by m6a2x6 on 2010-09-03
Thank you very much!

I'm gonna get the hang of it ;-)

> I don't see why you're using eval. You can run the command directly:

True, that must be one thing I tried when it did not work

---

