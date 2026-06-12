---
title: "Shell help - Recursive batch symbolic linking"
date: 2011-09-21
forum: General Help
---

### Post by TheMono on 2011-09-21
Hi there - 

What I'm trying to do is a command which will go through a bunch of folders, find anything named (filename).mkv and create a symbolic link next to it named (filename).mkp

I know this is a weird use case, please bear with me!

So far I've gotten to this point:

```
find -name '*.mkv' | sed 's/\(.*\)\.mkv/ln -s "\1.mkv" "\1.mkp"/' |sh
```

This works for the first layer, that is to say ./bar.mkv will get a ./bar.mkp link placed next to it. The moment we get further down the directory tree though, it stops working. It'll create the link, but incorrectly.

For example, I have ./foo/bar.mkv
This command would then create a link at ./foo/bar.mkp but the link will point to ./foo/bar.mkv RELATIVE TO THE ORIGINAL FILE - that is to say the net result is the link at ./foo/bar.mkp points to ./foo/foo/bar.mkv

I hope I've explained this well enough!

Any help would be very much appreciated.

---

### Post by staticd on 2011-09-21
```

find -name '*.mkv' -execdir sh -c  'ln -s "{}" "$(echo {}|sed '\''s/mkv$/mkp/'\'')"' \;

```

the funny **'\''** is to insert a single quote into a single quoted string. it evaluates as **'**break string **'\**concatenate a single quote **'**resume string.
see the man page for find for the execdir param.

Thats the first time I've seen output piped to shell to run a command. Cool! . Guess there is always another way.

---

### Post by TheMono on 2011-09-21
> **staticd said:**
> ```

find -name '*.mkv' -execdir sh -c  'ln -s "{}" "$(echo {}|sed '\''s/mkv$/mkp/'\'')"' \;

```

the funny **'\''** is to insert a single quote into a single quoted string. it evaluates as **'**break string **'\**concatenate a single quote **'**resume string.
see the man page for find for the execdir param.

Thats the first time I've seen output piped to shell to run a command. Cool! . Guess there is always another way.

You sir are a gentleman and a scholar. I appreciate you taking the time to help, and it works a treat.

---

