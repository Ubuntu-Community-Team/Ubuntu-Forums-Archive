---
title: "Bash Scripting"
date: 2010-01-22
forum: General Help
---

### Post by magevideogames on 2010-01-22
I have a simple bash script I want to write that would get the width and height of an image then decide if it should be moved to a high resolution folder.  However, for some reason whenever i try to output the results of the command to a variable it doesn't execute the command.  I know the command works because I tested it without the variable.  Here is the script so far.  I finished up the script here so I may have errored since I originally stopped at the width :P  Thanks in advance.

for f in $(ls /myImagesFoler/); 
 do 
  width=$(identify -format '%w' "/myImagesFolder/$f") 
  height=$(identify -format '%h' "/myImagesFolder/$f") 
  if [($width * $height) >= 1920000] 
    then mv "/myImagesFolder/$f" /myHighResFolder
  fi
  ; 
done

---

### Post by doas777 on 2010-01-22
try moving $f outside the quotes. if that fails try parens. usually after enough fiddeling I can get it going. obviously I;m no shell guru though.

---

### Post by magevideogames on 2010-01-22
Still blank line unfortunately, what's weird is the width gets assigned to identify instead of the result.  That's what really confuses me.

---

### Post by cenzorrll on 2010-01-22
did you make sure to shebang it?

add ```
#!/bin/bash
```

as the first line

---

### Post by magevideogames on 2010-01-22
Know I was running it directly in the terminal.  Never took the time to learn how to make a shell script file>.<

---

### Post by geekshlby on 2010-01-22
```
#!/bin/bash

for f in $(ls ~/myImagesFolder); do
        width=$(identify -format %w ~/myImagesFolder/$f)
        height=$(identify -format %h ~/myImagesFolder/$f)
        if [ $(($width*$height)) -ge 1920000 ]; then
                mv ~/myImagesFolder/$f ~/myHighResFolder
        fi
done
```

---

### Post by raffaele181188 on 2010-01-22
Does that folder contain any filename with space? (eg "My pic file.png")

---

### Post by geekshlby on 2010-01-22
Good call raffaele.

Dumping the field separator :)

Updated...

```
#!/bin/bash
IFS=""
for f in $(ls ~/myImagesFolder); do
        width=$(identify -format %w ~/myImagesFolder/$f)
        height=$(identify -format %h ~/myImagesFolder/$f)
        if [ $(($width*$height)) -ge 1920000 ]; then
                mv ~/myImagesFolder/$f ~/myHighResFolder
        fi
done
```

---

### Post by magevideogames on 2010-01-22
Hmm that seems to solve most of the problem, i put that in a .sh file and ran it.  The only thing is, it says:

mv: cannot move `/media/DRV3_VOL1/Images/Anime Images/Anime/angelwi4pl.jpg' to `/media/DRV3_VOL1/Images/Anime Images/Anime/High Res/': Not a directory

Not sure why seeing as how it list the correct paths.  Here is the code put in with the actual file paths.

#!/bin/bash

for f in $(ls /media/DRV3_VOL1/Images/Anime\ Images/Anime/); do
        width=$(identify -format %w /media/DRV3_VOL1/Images/Anime\ Images/Anime/$f)
        height=$(identify -format %h /media/DRV3_VOL1/Images/Anime\ Images/Anime/$f)
        if [ $(($width*$height)) -ge 1920000 ]; then
                mv /media/DRV3_VOL1/Images/Anime\ Images/Anime/$f /media/DRV3_VOL1/Images/Anime\ Images/Anime/High\ Res/
        fi
done

I put the \ for escaping although I usually use "" for that.  I know the paths are correct cause i copy pasted them from the terminal.

---

### Post by lswb on 2010-01-22
Try
```

#!/bin/bash

for f in ~/myImagesFolder/*; do
        width=$(identify -format %w "$f")
        height=$(identify -format %h "$f")
        if [ $(($width*$height)) -ge 1920000 ]; then
                mv "$f" ~/myHighResFolder
        fi
done

```

Note the quoting, and that the shell does its own path/filename expansion. Using  $(ls ...) is usually not necessary when all you need are file names.

---

### Post by magevideogames on 2010-01-22
That seems to have helped but now it has a problem because of the spaces in the folder and file names:/

---

### Post by lswb on 2010-01-22
If the destination folder name contains spaces put it in quotes like "my folder" also

---

### Post by magevideogames on 2010-01-25
I tired it with quotations around the folder with spaces (~/Desktop/Anime Images/ became ~/Desktop/"Anime Images"/ but still have the problem I'll post the error here.

:~/Desktop$ ./high\ res\ mover.sh 
identify: unable to open image `/home/mage/Desktop/Anime': No such file or directory @ blob.c/OpenBlob/2480.
identify: unable to open image `Images/Anime/001c2babdc693c4ad9c210393d5a2fbf.jpg': No such file or directory @ blob.c/OpenBlob/2480.
identify: unable to open image `/home/mage/Desktop/Anime': No such file or directory @ blob.c/OpenBlob/2480.
identify: unable to open image `Images/Anime/001c2babdc693c4ad9c210393d5a2fbf.jpg': No such file or directory @ blob.c/OpenBlob/2480.
./high res mover.sh: line 6: *: syntax error: operand expected (error token is "*")


Here is my current code
#!/bin/bash

for f in ~/Desktop/"Anime Images"/Anime/*; do
        width=$(identify -format %w $f)
        height=$(identify -format %h $f)
        if [ $(($width*$height)) -ge 1920000 ]; then
                mv -i $f ~/Desktop/"Anime Images"/"High Res"/
        fi
done

---

### Post by lswb on 2010-01-25
Do the quoting like this:

for f in "~/Desktop/Anime Images/Anime/"*; 

and

mv -i "$f" "~/Desktop/Anime Images/High Res"
fi

---

### Post by falconindy on 2010-01-25
The problem is the for loop declaration. Your iterator will consider white space to mean the end of an element, regardless of whether or not it really is. Instead, use a 'while read' loop:

```
#!/bin/bash

while read f; do
  dimXY=($(identify -format "%w %h" "$f"))
  test $(( ${dimXY[0]} * ${dimXY[1]} )) -ge 1920000 && mv "$f" ~/myHighResFolder
done <<(ls ~/myImagesFolder/)
```

This way, the only thing that ends an element is a newline character.

edit: rewrite for conciseness
reedit: zsh starts array counting at 1, not 0 like bash X.X

---

