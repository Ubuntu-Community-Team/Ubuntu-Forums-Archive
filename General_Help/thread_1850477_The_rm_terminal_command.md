---
title: "The rm terminal command"
date: 2011-09-26
forum: General Help
---

### Post by carranty on 2011-09-26
If I have a folder containing many files and wish to delete all but a few (using the terminal), how can I use the rm command to leave the few I want to keep alone.  I found on the forum that for one file I can use

rm -f !(nameOfFile)

but I'm not sure how to do more than one file.  Any help would be appreciated, apologies if this has been asked before.

---

### Post by aerosmm on 2011-09-26
The tool for this job is 'find'. There's some examples here,  [http://www.liamdelahunty.com/tips/linux_find_exclude_multiple_directories.php](http://www.liamdelahunty.com/tips/linux_find_exclude_multiple_directories.php)  but the basic recipe is just

find /path/to/start/dir -type f -name '*.ext' -exec rm -f {} \;

Now that's for everything. You wanted to ignore specific directories and files. This is technically possible using the -prune flag and find, but I find it's a lot easier (and I'm less likely to make mistakes) to use a sed picket-fence substitution, like so

for file in `find . -type f -name '*.ext' | sed -e '/\/path\/to\/file\/I\/dont\/want\/to\/remove/ d' -e '\/you\/get\/the\/idea/ d'`; do rm -vf $file; done 

If you're worried you might make a mistake, the best thing to do is

git init && git add -A * && git commit -m "deleteme"

Then you can retrieve anything you accidentally delete with

git reset --hard

and when you're sure you got it right,

rm -rf .git
Finally, if you need more granular control, one thing I like doing is dumping everything to a text file, like so 

echo "#!/bin/bash" > somefile
echo >> somefile
find . -type f -name '*.ext' >> somefile
sed -e 's@^@rm -f @' -i somefile

Then just open it up in an editor, delete the lines you want to save, and run it with

sh somefile

---

### Post by sisco311 on 2011-09-26
If extglob is enabled, you can do something like:
```
echo !(file1|file2|file3)
```

Find also has a -regex test, see: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

@aerosmm
*for i in $(find ...)* is bad. See: BashPitfalls #1 (link in my sig).

---

### Post by carranty on 2011-09-26
Thanks for the detailed response aerosmm but that's a little beyond me, I've not even heard of a sed picket-fence -- I shall reread it when I'm a little more experienced though!

sisco311, your solution seems simpler but is there a way to pass the results of the echo command straight to rm. Something like

rm  (echo !(file1|file2|file3)[FONT=monospace])

Thanks again.
[/FONT]

---

### Post by sisco311 on 2011-09-26
echo displays a line of text. !(file1|file2) is an extended glob, see: [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

So, you don't have to (and shouldn't) pass the result of echo to rm. Simply replace the echo command with rm.

---

### Post by carranty on 2011-09-27
Oh yes, of course, I was having a senile moment : confused:. Thanks a lot! :)

---

### Post by sisco311 on 2011-09-27
You are welcome!

---

