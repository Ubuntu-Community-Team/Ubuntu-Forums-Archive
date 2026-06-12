---
title: "help writing a script?"
date: 2010-03-08
forum: General Help
---

### Post by rebeltaz on 2010-03-08
I have a directory that has 156 subdirectories. In each of those 156 subdirectories are 10 files named 0.png through 9.png. It is taking forever to click on a directory, look at the files icons, click back and then select the next directory. 

What I would like is a script that can take one file out of each subdirectory maybe 8.png, rename it to whatever-the-directory-name-is.png and store it in a directory called preview.

Then I could just go to the preview directory and I would be able to see a sample of each directory at a glance and know which directory it came from.

Does that make since? Thanks, guys...

---

### Post by d3v1150m471c on 2010-03-08
learn how to use the mv and cp commands.

---

### Post by Kaligo on 2010-03-08
What would be even better is to set the folder icon as one of the images within the folder.

Alternatively you could install dolphin and use that to browse your directories.

---

### Post by d3v1150m471c on 2010-03-08
I think installing dolphin wouldn't be the greatest of ideas. It's probably the only thing about kubuntu that annoys me.

---

### Post by rebeltaz on 2010-03-08
> **d3v1150m471c said:**
> learn how to use the mv and cp commands.

I know how to use mv and cp. It just seems to me that manually typing cp blupl/8.png preview/blupl.png for a 156 freaking files would be a little more than time consuming - to put it mildly.

---

### Post by rebeltaz on 2010-03-08
> **Kaligo said:**
> What would be even better is to set the folder icon as one of the images within the folder.

That would be great. How do I do that. I tried setting the directory to icon view, but that only shows folder icons for the subdirectories.

---

### Post by kaibob on 2010-03-08
The following should do what you want. You need to change the source and target directories. I tested this with directories nested five deep and it worked fine. 

```
#!/bin/bash

source="/source/directory"
target="/target/directory"

find "$source" -name 8.png | while read file ; do
   dir="${file%/*}"
   dir="${dir##*/}"
   cp "$file" "${target}/${dir}.png"
done
```

---

### Post by rebeltaz on 2010-03-08
> **kaibob said:**
> The following should do what you want. You need to change the source and target directories. I tested this with directories nested five deep and it worked fine. 

```
#!/bin/bash

source="/source/directory"
target="/target/directory"

find "$source" -name 8.png | while read file ; do
   dir="${file%/*}"
   dir="${dir##*/}"
   cp "$file" "${target}/${dir}.png"
done
```

That worked PERFECTLY! THANK YOU SO MUCH! 

Now that I can see how it's done, I'll study the commands you used and next time, hopefully I'll be able to do that myself.

Thank you again!

---

### Post by Kaligo on 2010-03-08
Glad to hear you got it sorted, you can also look [here]("http://ubuntuforums.org/showthread.php?t=226199") for more info on setting custom icons for your folders.

---

### Post by rebeltaz on 2010-03-08
> **Kaligo said:**
> Glad to hear you got it sorted, you can also look [here]("http://ubuntuforums.org/showthread.php?t=226199") for more info on setting custom icons for your folders.

Wow... that looks a little more complicated than a preview folder! I'll have to sit down and read that when I'm more focused.

Thank you, though.

---

