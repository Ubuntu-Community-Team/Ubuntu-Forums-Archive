---
title: "Renaming a file via terminal"
date: 2010-10-15
forum: General Help
---

### Post by John A on 2010-10-15
Bit of a silly mistake here...

I was on Inkscape, made a *.SVG and went to save it. Now, I went to overwrite a *.GIF file and I saved it as a *.GIF file. So now I have a SVG saved as a GIF in the folder with all my photography.

I'm assuming the file is being read wrong and/or it can't generate a thumbnail. But I open it, go to rename it and then it freezes. Sometimes the whole pc freezes, but not always.

Any help would be appreciated, John. :)

---

### Post by nothingspecial on 2010-10-15
You rename a file
```

mv file.ext new_name.ext
```

Don`t type mv *.GIF *.SVG or you will rename every GIF to a SVG

---

### Post by John A on 2010-10-15
> **nothingspecial said:**
> You rename a file
```

mv file.ext new_name.ext
```

Don`t type mv *.GIF *.SVG or you will rename every GIF to a SVG

Tried this. Came up with both:

```
john@john-desktop:~$ mv vilkija_COA.gif vilkija_COA.svg
mv: cannot stat `vilkija_COA.gif': No such file or directory
```
and
```
john@john-desktop:~$ mv vilkija COA.gif vilkija_COA.svg
mv: target `vilkija_COA.svg' is not a directory
```

---

### Post by WorMzy on 2010-10-15
You need to cd to the directory containing the images first, or else use the full path.

e.g.
```
cd Pictures
mv vilkija_COA.gif vilkija_COA.svg
```

OR

```
mv /home/[COLOR="Red"]username[/COLOR]/Pictures/vilkija_COA.gif /home/[COLOR="Red"]username[/COLOR]/Pictures/vilkija_COA.svg

```

(replace [COLOR="Red"]username[/COLOR] with your username, obviously)

Oh, and if the filename has a space in it, then use a backslash to escape the space. e.g. ```
mv vilkija\ COA.gif vilkija\ COA.svg
```

---

### Post by nothingspecial on 2010-10-15
Does the file have a space in it?

If so you need to escape the space

```
mv vilkija\ COA.gif vilkija_COA.svg 
```Do you already have a file 
vilkija_COA.svg  
mv will rename a file or directory unless the target directory exists in which case it will move it inti oi.

---

### Post by John A on 2010-10-15
> **WorMzy said:**
> 
```
cd Pictures
mv vilkija_COA.gif vilkija_COA.svg
```
```
mv /home/[COLOR="Red"]username[/COLOR]/Pictures/vilkija_COA.gif /home/[COLOR="Red"]username[/COLOR]/Pictures/vilkija_COA.svg

```
```
mv vilkija\ COA.gif vilkija\ COA.svg
```

> **nothingspecial said:**
> 
```
mv vilkija\ COA.gif vilkija_COA.svg 
```
 I tried all these and none worked. Though I said my photography, I din't mean my "Pictures" folder. I mean a folder called "Wiki Images" on my "Desktop". Probably why I ended up doing one of them wrong. :D

---

### Post by nothingspecial on 2010-10-15
```
cd ~/Desktop/Wiki
```

or open a terminal and drop the Wiki folder into it. It won`t eat it, it will just take the terminal there.

---

### Post by AlphaLexman on 2010-10-15
You can 'rename' a .svg file to a .gif ... but the file is still a .svg file.
```
file vilkija_COA.gif
```

---

### Post by John A on 2010-10-15
> **nothingspecial said:**
> ```
cd ~/Desktop/Wiki
```

or open a terminal and drop the Wiki folder into it. It won`t eat it, it will just take the terminal there.

> **AlphaLexman said:**
> You can 'rename' a .svg file to a .gif ... but the file is still a .svg file.
```
file vilkija_COA.gif
```

@nothingspecial I tried your code, and it didn't work (see output below)
Also, I can't drag the folder as my Desktop has literally just froze. It's becoming more unstable by the second.

@AlphaLexman And yet it's killing my PC... :/

```
john@john-desktop:~$ cd ~/Desktop/Wiki Images
bash: cd: /home/john/Desktop/Wiki: No such file or directory
```

---

### Post by AlphaLexman on 2010-10-15
If a directory has a 'space' in it, you will need to put a backslash \ in front of the space.
> john@john-desktop:~$ cd ~/Desktop/Wiki Images should be:
```
john@john-desktop:~$ cd ~/Desktop/Wiki\ Images 
```

---

### Post by John A on 2010-10-16
> **AlphaLexman said:**
> If a directory has a 'space' in it, you will need to put a backslash \ in front of the space.
should be:
```
john@john-desktop:~$ cd ~/Desktop/Wiki\ Images 
```

Sorry for the long response wait. Something came up...

Tried that code and it put me in the folder. Now what?

```
john@john-desktop:~/Desktop/Wiki Images$
```

---

### Post by nothingspecial on 2010-10-16
Now do the mv command, not forgetting to escape the spaces with a \

```
files\ and\ directories\ with\ spaces\ need\ these
```

```
"or quotes around them"
```

---

### Post by The Cog on 2010-10-16
It might be easier to use quotes than backspaces for filenames with spaces, though either approach is valid:
mv filename\ with\ spaces.svg filename\ with\ spaces.jpg
mv 'filename with spaces.svg' 'filename with spaces.jpg'

---

### Post by John A on 2010-10-16
> **The Cog said:**
> It might be easier to use quotes than backspaces for filenames with spaces, though either approach is valid:
mv filename\ with\ spaces.svg filename\ with\ spaces.jpg
mv 'filename with spaces.svg' 'filename with spaces.jpg'

Tried with slashes and it didn't work.
Tried it with quotes and it worked perfectly. Now it's all working fine.

One thing to note was that after trying all these things, or maybe from the overall instability the problem cause, the folder /dev/null (I think) could not be found at start-up. The computer still loaded, but it did cause some concern.

I know this is off the post's topic, but I'd love some help/re-assurance that my PC isn't gonna have a worse problem.

Thanks for the help, John.

---

### Post by junapp on 2010-10-16
Had almost the exact same problem awhile back - don't feel bad. Seems at least 3 people have done this. If I remember correctly, I had inserted a jpg, then saved the new svg file with the embedded jpg as the same name as the jpg file by mistake (slip of the mouse). Caused major freeze ups.
[http://ubuntuforums.org/showthread.php?t=1380964](http://ubuntuforums.org/showthread.php?t=1380964)

---

### Post by John A on 2010-10-16
> **junapp said:**
> Had almost the exact same problem awhile back - don't feel bad. Seems at least 3 people have done this. If I remember correctly, I had inserted a jpg, then saved the new svg file with the embedded jpg as the same name as the jpg file by mistake (slip of the mouse). Caused major freeze ups.
[http://ubuntuforums.org/showthread.php?t=1380964](http://ubuntuforums.org/showthread.php?t=1380964)

Did you get the error at start-up?

---

### Post by junapp on 2010-10-16
I don't believe so. I'd think that would be a separate issue.

---

