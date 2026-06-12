---
title: "Copy a small sample set of pictures (cp, ls, tail)"
date: 2011-07-06
forum: General Help
---

### Post by amhainen on 2011-07-06
I'm trying to copy a sample set of files/pictures to a directory on my desktop. For my sample from /home/user/pics containing 7,000+ pictures, I have a desired list of:

```
user@computer:/home/user/pics$ ls | tail
```

I use that to generate a list of a few files that I'd like to move to my desktop. I tried:

```
user@computer:/home/user/pics$ ls | tail | cp /home/user/Desktop
```

I thought that might dump the tail list of files for an argument in the cp command, but no luck. I then tried:

```
user@computer:/home/user/pics$ ls | tail | cp . /home/user/Desktop
```

I thought the . might help guide my "ls | tail" output, but no luck.

Thanks for the help!

---

### Post by nothingspecial on 2011-07-06
There's probably a simpler way, but to expand on what you've already got...


```
ls | tail | xargs -I '{}' cp '{}' /home/$USER/Desktop
```

---

### Post by sisco311 on 2011-07-06
Hi and welcome to the forums!

Read the file names in an array, then use a loop to copy the ones you want.

Something like:
```
shopt -s nullglob
FILES=( * )
if (( ${#FILES[@] == 0 ))
then
  echo "empty directory. nothing to do."
elif (( ${#FILES[@] < 10 ))
  echo "less than 10 files. copy all of them."
  cp * /new/dir
else
  echo "more than 10 files. copy the last 10."
  for i in {1..10}
  do
    cp -- "${FILES[${#FILES[@]} - i]}" /new/dir
  done
fi
```

---

### Post by amhainen on 2011-07-06
> **nothingspecial said:**
> There's probably a simpler way, but to expand on what you've already got...


```
ls | tail | xargs -I '{}' cp '{}' /home/$USER/Desktop
```

Thanks so much!

Sisco311, is your code a bash script? I'll try that as well when I have some time to break it down and understand.

---

### Post by nothingspecial on 2011-07-06
> **amhainen said:**
> Thanks so much!

No problem

---

### Post by sisco311 on 2011-07-06
> **amhainen said:**
> 
Sisco311, is your code a bash script? I'll try that as well when I have some time to break it down and understand.

Yep, it's bash. If you need a good reference, check out [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/)

If you have any question, please feel free to ask it here on the forums or at freenode's #bash channel.

---

