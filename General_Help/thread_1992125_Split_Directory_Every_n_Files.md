---
title: "Split Directory Every n Files"
date: 2012-05-31
forum: General Help
---

### Post by amhainen on 2012-05-31
I have an SD card with ~10,000 pictures on it from a timelapse camera. I'm having trouble opening a directory with this many files. I've ran into this with CSV files that are too many lines for Excel, but the split command in Bash was able to split the file every n lines.

Is there a way that I can split the directory into sub directories with n files? I'd like to make a bash script that could break this into 10 folders with 1,000 pictures each. So I think I'm looking for a mv loop through the pics.

Let me know if this isn't clear. Thanks for the help!

---

### Post by amhainen on 2012-05-31
To be clearer, it's the opposite of this:

[http://stackoverflow.com/questions/8705757/moving-multiple-files-in-subdirectories-and-or-splitting-strings-by-multichar-d](http://stackoverflow.com/questions/8705757/moving-multiple-files-in-subdirectories-and-or-splitting-strings-by-multichar-d)

I want to split the directory into multiple directories.

---

### Post by steeldriver on 2012-05-31
well I guess you could pipe the output of ls through head to keep selecting the 'next' 1000 files, something like

## NOT REALLY TESTED - USE AT YOUR OWN RISK ##
```
for ((i=1; i<=10;i++)); do mv `ls *.jpg | head -1000` mysubdir$i/; done
```

... it's kinda ugly, I know 

(NB doesn't create the subdirs for you, you could add that quite easily though)

---

