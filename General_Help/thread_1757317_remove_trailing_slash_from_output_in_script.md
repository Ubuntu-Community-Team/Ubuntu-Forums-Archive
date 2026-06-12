---
title: "remove trailing slash from output in script"
date: 2011-05-13
forum: General Help
---

### Post by rountrey on 2011-05-13
I didn't really know where to ask this whether in programming or multimedia, so, I'm sorry if this isn't the place.

I am having a little trouble with a small script for HandBrakeCLI. I have a directory of various movies, some are avi, some are mkv, some are iso, but most are directories of DVD structures. I want to encode the DVD directories using the directory name as the file name putting it in the originating directory but not encoding any of the other files. Here is what I have so far:
```
#!/bin/bash

for FILE in */; do nice -n 3 HandBrakeCLI -i "$FILE" \
-e ffmpeg -b 1500 \
-E lame -B 160 -R 44.1 \
-s 1 --subtitle-burn \
-v -o "$FILE".mkv ; \
done
```

I would change it to for FILE in *; do nice -n 3 HandBrakeCLI -i "$FILE"/ but as I said I don't want to encode the other files. As you can see it will create a mkv file but it makes it like this /enc_dir/DVD_movie/.mkv and what I want is /enc_dir/DVD_movie.mkv

I have tried piping sed through it between "$FILE" and .mkv and  also after .mkv and both will stop the encoding process entirely (it will scan and read the files in the directory but stop after that). 

Thanks in advance.

---

### Post by Vaphell on 2011-05-13
try
```
"${FILE%/}"
```
% trims given pattern at the end, # does the same at the start, wildcards like * are supported, there are also greedy versions (%% and ##) removing as much as they can as opposed to non greedy (% and #)

example
```
$ FILE='/some/stuff/'; echo "${FILE%/}"
/some/stuff

$ x='a:b:c'; echo ${x%:*} ${x%%:*} ${x#*:} ${x##*:}
a:b a b:c c

```

---

### Post by rountrey on 2011-05-13
Thank you Vaphell, it worked exactly like I wanted it to. But real quick, does this mean that sed is out dated or just doesn't work in scripts? because that was the only solution i could find.

---

### Post by Vaphell on 2011-05-13
it does work in scripts but not necessarily the way you'd want it. Sed normally reads from file or from pipe
```
sed 's:/$::' input_file(s)
some_command | sed 's:/$::'
```

I don't know what you tried but you simply need to echo the variable and pipe to sed.

```
$ FILE='/some/stuff/'; TRIMMED=$( echo "$FILE" | sed 's:/$::' ); echo 1-2-3 "$TRIMMED" 1-2-3
1-2-3 /some/stuff 1-2-3

$ FILE='/some/stuff/'; echo 1-2-3 $( echo "$FILE" | sed 's:/$::' ) 1-2-3
1-2-3 /some/stuff 1-2-3

```

for simple stuff use built-in bash toys like the ones i described above, they don't have to spawn child process (like in case of sed) to calculate intermediate value

---

