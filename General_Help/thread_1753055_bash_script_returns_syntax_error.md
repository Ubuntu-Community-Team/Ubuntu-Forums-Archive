---
title: "bash script returns syntax error"
date: 2011-05-08
forum: General Help
---

### Post by sporez on 2011-05-08
I'm a relative noob when it comes to bash scripting so I may have overlooked something obvious here.  I'm trying to make a basic script that removes all files except video files.

However each time I run it I get this:
```
./tv_cleanup.sh: line 10: syntax error near unexpected token `('
./tv_cleanup.sh: line 10: `rm !(*.avi|*.mp4|*.wmv|*.ogv)'
```

Here's the actual script:
```
#!/bin/bash
#Simple TV folder cleanup script
#Written by vetteracerz/sporez
#[http://sporez.info](http://sporez.info)
clear
echo "Enter media directory that you want cleaned up (eg. /media/tv/psych/season01)"
read dir
cd $dir
echo "Cleaning up $dir now, please wait."
rm -f !(*.avi|*.mp4|*.wmv|*.ogv)
echo "Cleanup ran successfully!"
```

When I run "rm -f !(*.avi|*.mp4|*.wmv|*.ogv) by itself in the terminal it works fine.  Anyone have any idea why the script isn't working?

---

### Post by DaithiF on 2011-05-08
Hi, the !(...) pattern matching relies on a shell option (extglob) being set.  Its most likely set in your interactive environment but not when running a script.  set the option explicitly in your script before you do the pattern expansion.

```
shopt -s extglob
```

---

### Post by sporez on 2011-05-08
> **DaithiF said:**
> Hi, the !(...) pattern matching relies on a shell option (extglob) being set.  Its most likely set in your interactive environment but not when running a script.  set the option explicitly in your script before you do the pattern expansion.

```
shopt -s extglob
```

That did it!  Thanks a lot. :)

---

### Post by DaithiF on 2011-05-09
Hi, just a word of warning, as it stands your script is a little dangerous.

if when running the script you mistype a directory path and input a path which does not exist, then the cd command will fail, leaving the current working directory whereever you were when running the script, or your home directory if running it from a launcher / alt-f2, etc.  so the result would be that files in that directory would be deleted.

you should probably do a couple of things:
1. check that the cd command succeeds before carrying on with the delete.  change the cd line to:
```
cd "$dir" || { echo "Could not cd to $dir, exiting..."; exit 1; }

```

2. you may want to test that the input directory begins with /media/tv or similar before carrying on with the delete.  If when prompted for the directory you just hit return, ie. thereby entering nothing as the directory, the cd command would success and place you in your home directory, where I imagine deleting everything but media files wouldn't be a good result.  so after the directory has been read a line like:
```
[[ "$dir" =~ /media/tv ]] || { echo "The directory you enter must be within /media/tv, exiting..."; exit 1; }

```

---

