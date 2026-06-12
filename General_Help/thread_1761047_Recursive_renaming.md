---
title: "Recursive renaming"
date: 2011-05-17
forum: General Help
---

### Post by glave on 2011-05-17
I've been tinkering for about 2 hours now, and I think if I'd renamed these individually I'd be done now ;)

I'm trying to recursively rename every file called 'trailer.mov' into 'movie-trailer.mov'. I've poured over tons of webpages and there are a zillion ways to accomplish it, and I have gotten very very close, but each example I've found somehow falls just short in some way.

This is the closest I've gotten:

```
rename trailer.mov movie-trailer.mov `find . -name trailer.mov`
```

The issue with this command is when find hits a directory with space in it, it passes that back to rename split up.

I also had this to a point that it *SHOULD* have worked:

```
find . -name 'trailer.mov' -printf '%p\n' | while read file; do
  oldfile=$(basename "$file")
  newfile=$(echo "$oldfile" | dirname "$file")
  if [ ! "$newfile" == "$oldfile" ]; then
    echo mv "\"$file"\" "\"$newfile/movie-trailer.mov"\"
  fi
done
```

This worked GREAT! So I removed the 'echo' fail safe, and mv give me lots of errors like this:
mv: cannot stat `"./BDRip/Coraline (2009)/trailer.mov"': No such file or directory


Can anyone help me out with this simple command?

---

### Post by TeoBigusGeekus on 2011-05-17
Try this
```
find ./ -name trailer.mov -execdir mv "{}" movie-trailer.mov \;
```

---

### Post by glave on 2011-05-17
YES! Thank you thank you. I knew I had to be very close.

The blessing and curse of linux, a million different ways to achieve the same net result.

---

