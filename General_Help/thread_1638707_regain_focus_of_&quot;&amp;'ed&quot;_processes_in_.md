---
title: "regain focus of &quot;&amp;'ed&quot; processes in terminal"
date: 2010-12-06
forum: General Help
---

### Post by 0949er on 2010-12-06
Hey guys, how are you?

If you run the command:

```

swooshonln@power-house:~/$ mpg123 -C song.mp3 &
swooshonln@power-house:~/$ 

```

how would you go about regaining "focus" of mpg123... if mpg123 is currently awaiting keyboard input so you can control next song, volume, etc?

---

### Post by asmoore82 on 2010-12-06
```
fg
```
For "foreground"

You can also stop a foreground process with Ctrl+Z.
Then, allow it to continue as above -OR- in the background with
```
bg
```^This is the same as starting it with "&", but after-the-fact.

---

### Post by 0949er on 2010-12-06
> **asmoore82 said:**
> ```
fg
```For "foreground"

You can also stop a foreground process with Ctrl+Z.
Then, allow it to continue as above -OR- in the background with
```
bg
```^This is the same as starting it with "&", but after-the-fact.

sorry I am kinda confused by your explanation. How is this used on context? no manual entry for "fg" or "bg"

---

### Post by asmoore82 on 2010-12-06
`fg` and `bg` aren't in the manual because they are Bash shell builtins.
`cd` is this way too, but few ever try its manpage before knowing this.

```
swooshonln@power-house:~/$ mpg123 -C song.mp3 &
swooshonln@power-house:~/$ 
...
swooshonln@power-house:~/$ fg
...
```
At this point, you give `mpg123` the commands you wanted,
but `mpg123` has taken over your terminal, you can stop
`mpg123` and get a shell prompt back with Ctrl+z.

But, the music stops. You can get it started again by
throwing `mpg123` into the background:
```
swooshonln@power-house:~/$ bg
```
Now, you've gone full-circle and have `mpg123` playing
in the background just like `&` ~
enjoy the music and your all-on-one HTC Evo "remote" :p.

---

