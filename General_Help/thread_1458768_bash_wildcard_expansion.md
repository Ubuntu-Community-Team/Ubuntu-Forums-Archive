---
title: "bash wildcard expansion"
date: 2010-04-20
forum: General Help
---

### Post by hwttdz on 2010-04-20
So I'm attempting to do some file management, and I have a bunch of log and output files which are named systematically.  And I want to grab the files that are related to the log files.  Right now what I'm doing is

ls *selection*.log|sed "s/\.log/* target_dir\"/"|sed"s/^\"mv /"|xargs -n 1 bash -c

And what this does is list all the log files of interest and transform the 

filename_identifier.log 
to
mv filename_identifier* target_dir

but when I send "mv filename_identifier * target_dir" to bash -c the * isn't expanded which leads it to complain "no such file, blah, blah, blah".  How can I make bash expansion happen here?

---

### Post by sisco311 on 2010-04-20
Wow, that looks overcomplicated! :)

Try something like:
```
for file in *selection*.log; do
  cp ${file/\.log/*} target_dir
done
```

---

### Post by hwttdz on 2010-04-20
Looks much better, I settled mine by using xargs -t and then copying and pasting the command to the command line. Not elegant at all, but still got the job done.

---

