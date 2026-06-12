---
title: "Directory List Script Help!"
date: 2011-05-16
forum: General Help
---

### Post by ubila on 2011-05-16
Hello,
Im wanting to make a sh script to output the directory listing of a specific directory to a file index.html each line of the output formatted like this:

<a href="filename1">filename1</a><br />
<a href="filename2">filename2</a><br />

Any ideas how i would do this?

Thanks!

---

### Post by nemilar on 2011-05-16
Try something like this, on the command line:
```
for eachFile in *; do echo "<your HTML>${eachFile}</your HTML>" ; done 
```

Then use redirection to direct the output to a file.

---

### Post by wannabegeek on 2011-05-16
I'm a scripting newbie too, but here what I think is close...for BASH
```

for i in ls /path/to/dir/*
do
echo "<a href="$i">$i</a><br />"  >> filename
end

```check my use of >> or >   for append to file...

---

### Post by ubila on 2011-05-16
Thanks guys, perfect :)

---

### Post by matt_symes on 2011-05-16
Hi
[FONT=monospace]
[/FONT]```
for i in ls /path/to/dir/* 
do 
echo "<a href="$i">$i</a><br />"  >> filename 
end
```

This is good, but use globs. The ls command is unnecessary here.

```
for i in /path/to/dir/* 
do 
echo "<a href="$i">$i</a><br />"  >> filename 
done
```

This will explain why.

[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)

Kind regards

---

