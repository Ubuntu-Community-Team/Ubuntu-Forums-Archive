---
title: "ffmpeg batch converting"
date: 2012-06-10
forum: General Help
---

### Post by spiritech on 2012-06-10
i am trying to convert some .avi file to .mp4. and preserve the original file name, less the extension. i had a google around and found this link.

[http://lists.ubuntu.com/archives/kubuntu-users/2008-November/034676.html]("http://https://lists.ubuntu.com/archives/kubuntu-users/2008-November/034676.html")

i changed the command to this, to allow for the different type of file.

for f in *.avi; do ffmpeg -i $f -sameq $f.mp4

also i changed the -vn to -sameq to keep the quality the same.
when i run the code it does not work. i get.

bash: syntax error near unexpected token `do'

spiritech

---

### Post by Vaphell on 2012-06-10
that message means your for loop is messed up, are you sure you've got *for ... in ...; do ....; done* there?

---

### Post by evilsoup on 2012-06-10
As Vaphel wrote, it looks like you forgot the 'done'; it should be

for f in *.avi; do ffmpeg -i "$f" -sameq "$f".mp4; done

if you want to avoid ugly filenames, like 'filename.avi.mp4' (which is what your command will spit out), you'll want to use rename in there as well, so:

for f in *.avi; do ffmpeg -i "$f" -sameq "$f".mp4; rename 's/\.avi//' "$f".mp4; done

---

### Post by Vaphell on 2012-06-10
changing extension is trivial and can be done with bash alone
```
$ f=some_file.avi
$ echo "$f" "${f%.avi}.mp4"
some_file.avi some_file.mp4
```

---

### Post by spiritech on 2012-06-10
ok

thank you for your help

---

