---
title: "Made a boo boo with filenames in bash script"
date: 2011-01-09
forum: General Help
---

### Post by dchurch24 on 2011-01-09
Hi,

I've been writing a script that iterates through a folder (my kids videos) and strips out the first part of the filename, creates a folder of what's left, then moves the file into that folder.

...only, I haven't.

Instead, I've renamed the files like so:

Atlantis The Lost Empire.Disney Classic - 40 - Atlantis The Lost Empire.avi

from a file called:

Disney Classic - 40 - Atlantis The Lost Empire.avi

As you can see, I have missed the / from the mv command and instead of moving the files to a folder (that it created perfectly, in this case called "Atlantis The Lost Empire") it's prefixed the original file with the folder name.

I can't for the life of me work out how to reverse it.

The script I made is as such:

```

#!/bin/sh

for file in *Disney*.avi
do
  i=${file%.*}
  NEWDIR=`echo "$i" | sed 's/^.\{22\}//'`
  mkdir "$NEWDIR"  
  mv "$file" "$NEWDIR"."$file"
  echo $file
done


```

You can see what I've done, I put a . where I should have a /.

Now I need to reverse my **** up and put the files back how they were, THEN go back and run the corrected script.

I just can't work out how to remove everything back from the . in the new filename if you catch my drift.

Can anyone shed any light on this for me?

---

### Post by dchurch24 on 2011-01-09
Ok, I'm getting somewhere, I think.

I now have a script as such:

```

#!/bin/sh

for file in *Disney*.avi
do
  i=${file%.*}
  filename=`echo "cut -d'"."' -f2,3 <<< '$file'"`
  echo $filename
done



```

This outputs this to the terminal (as well as all the rest, but I used this as the example in the last post):
```

cut -d"." -f2,3 <<< "Atlantis The Lost Empire.Disney Classic - 40 - Atlantis The Lost Empire.avi"

```

If I cut and paste that, it works beautifully, but the script is only outputting it to the window, not actually executing it.

How can I make it execute each line so that my variable is filled with the 'answer' rather than the 'question'?

---

### Post by Crusty Old Fart on 2011-01-10
Something like this:
```
#!/bin/sh

for file in *Disney*.avi; do
  mv "$file" "$(echo "$file" | sed 's/.\+Disney/Disney/')"
done

exit 0

```

---

