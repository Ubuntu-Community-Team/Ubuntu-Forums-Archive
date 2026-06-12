---
title: "Simple way of copying a bunch of files"
date: 2012-05-27
forum: General Help
---

### Post by Ptallqvist on 2012-05-27
Sorry about the non-descriptive thread title, couldn't come up with a better one. Here's my situation: I have two folders, call them ~/small and ~/big. The ~/small folder has a bunch of pictures. The ~/big folder has the same pictures, but in a bigger resolution, plus a lot of other pictures. What I want to do: I want to copy a bigger version of the pictures to the ~/small folder, overwriting the smaller ones.  After that I could batch resize the pictures in ~/big to save hard disk space. I can do this by picking the files one by one, but there are 3000+ files to pick, and I was wondering if there was maybe an easier way to do this, perhaps by somehow listing all the filenames I want and then using that list with cp somehow.

---

### Post by steeldriver on 2012-05-27
something like

```
for file in `ls small`; do if [ -f big/$file ]; then cp big/$file small/$file; fi; done
```maybe?

---

### Post by Ptallqvist on 2012-06-03
Worked perfectly, thank you very much ):P

---

### Post by sisco311 on 2012-06-03
Please check out BashPitfalls 1, 2, 3, 4 ... (link in my signature).

In an interactive shell:
```

shopt -s nullglob
cd ~/small
for file in *
do
    if [[ -f ~"/big/$file" ]]
    then
        cp -- ~"/big/$file" ./
    fi
done
```

In a script, instead of ~ you should use $HOME and exit if the cd command fails (cd "$HOME/small" || exit 1).

---

