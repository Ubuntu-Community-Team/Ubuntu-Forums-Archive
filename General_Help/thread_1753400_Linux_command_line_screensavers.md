---
title: "Linux command line screensavers?"
date: 2011-05-08
forum: General Help
---

### Post by daweefolk on 2011-05-08
I know already of asciiquarium, but I'm wondering what other 'screensavers' exist for the command line, and if there is a 'manager' such as xscreensaver.

---

### Post by Toz on 2011-05-08
How about:
```
tr -c "[:digit:]""[!@#$%^&*()_+]" " " < /dev/urandom | dd cbs=$COLUMNS conv=lcase,unblock | GREP_COLOR="1;32" grep --color "[^ ]"
```

---

### Post by zitch on 2011-05-08
> **Toz said:**
> How about:
```
tr -c "[:digit:]""[!@#$%^&*()_+]" " " < /dev/urandom | dd cbs=$COLUMNS conv=lcase,unblock | GREP_COLOR="1;32" grep --color "[^ ]"
```

Why don't you explain to the rest of us what this is supposed to do. Frankly, I see "dd" in there and the hair on the back of my neck stands up. I don't see any "sudo" commands in there, but still...

Honestly, this may actually be benign, but the original poster (and anybody else looking for an ascii-based screensaver) might want to know that this is safe before running it.

UPDATE: I don't mean to be accusatory or anything.  Just don't want to see someone to lose data because of a bad joke.

---

### Post by Toz on 2011-05-09
Something a colleague showed me a few years back - basically a matrix-like screen saver. As I understand it.....

```
tr -c "[:digit:]""[!@#$%^&*()_+]" " " < /dev/urandom
```
randomizes a string of characters 

```
dd cbs=$COLUMNS conv=lcase,unblock
```
recodes the stream to the terminal such that:
     - cbs = it converts terminal_width bytes at a time
     - conv = it converts upper to lower case and replaces trailing spaces with a newline

```
GREP_COLOR="1;32" grep --color "[^ ]"
```
colours it green

---

### Post by jerome1232 on 2011-05-09
dd is just writing to standard output so there is no risk with that line, I went ahead and ran it, did about what I thought.

Kind of cool, I wonder if there's a way to get that run after x amount of inactivity. Could that be done in your bash profile?

---

### Post by AlphaLexman on 2011-05-09
Interesting, could it work with a different font?
[http://www.dafont.com/matrix-code-nfi.font](http://www.dafont.com/matrix-code-nfi.font)

---

### Post by daweefolk on 2011-05-16
> **Toz said:**
> Something a colleague showed me a few years back - basically a matrix-like screen saver. As I understand it.....

```
tr -c "[:digit:]""[!@#$%^&*()_+]" " " < /dev/urandom
```
randomizes a string of characters 

```
dd cbs=$COLUMNS conv=lcase,unblock
```
recodes the stream to the terminal such that:
     - cbs = it converts terminal_width bytes at a time
     - conv = it converts upper to lower case and replaces trailing spaces with a newline

```
GREP_COLOR="1;32" grep --color "[^ ]"
```
colours it green
I forgot to update, but I found another one- cmatrix.
And I am also interested in one starting if the terminal is inactive for x minutes, if it's possible.

---

