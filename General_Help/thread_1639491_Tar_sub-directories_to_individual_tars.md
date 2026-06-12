---
title: "Tar sub-directories to individual tars"
date: 2010-12-06
forum: General Help
---

### Post by kg87 on 2010-12-06
Just sat and watched coronation street (sorry) and had a thought

If i wanted to tar a directory into individual directories (but only one level) how would i go about it?

example would be

MainDirectory
|---dirA
|---dirB
|---dirc
|---dir....

would produce

dirA.tar
dirB.tar
dirC.tar etc


Thanks in advance

---

### Post by kg87 on 2010-12-07
Sorry, bump because i've actually found a use for this.

---

### Post by sisco311 on 2010-12-07
Try something like
```
cd path/to/dir
for file in *; do
  if [[ -d "${file}" ]]; then
    tar cvf "${file}".tar "${file}"
  fi
done
```

If you would also like to add compression to your tarballs, then use:
```
tar zcvf "${file}".tar.gz "${file}"
```

If you would like to preserve the permissions of the files:
```
tar pzcvf "${file}".tar.gz "${file}"
```

---

### Post by kg87 on 2010-12-07
Wheres the thanks button when you need it!

Im relatively baby faced when it comes to bash scripting, but not too bad with .NET

I've had a rough time learning a new language!

---

