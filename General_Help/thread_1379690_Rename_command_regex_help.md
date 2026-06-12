---
title: "Rename command regex help"
date: 2010-01-12
forum: General Help
---

### Post by @B6Mwu8fN9M on 2010-01-12
I've got a bunch of image files and I want to mass rename them to be 0001.JPG, 0002.JPG etc. 

I want to use the rename command specifically, so no extra software. I have never used regular expressions so I'm at a loss here.

Thanks in advance.

---

### Post by kaibob on 2010-01-12
I've never seen anyone use the rename command by itself to rename files as you want. Perhaps someone else will have a solution. If not, the following one-liner will do it without any extra software.

```
count=001 ; for file in *.JPG ; do mv "$file" ${count}.JPG ; count=$(printf "%03d" $((count+1))) ; done
```

---

### Post by @B6Mwu8fN9M on 2010-01-12
I get an error when I run that:
```
bash: 008: value too great for base (error token is "008")
count=001 ; for file in *.JPG ; do mv 007.JPG 008.JPG ; count= ; done

```

According to this thread [http://ubuntuforums.org/showthread.php?p=4206419](http://ubuntuforums.org/showthread.php?p=4206419) the problem is that it thinks it's in base 8 instead of base 10. How would I change the base in your command? I've never done this kind of thing before.

Thanks for the help

---

### Post by falconindy on 2010-01-12
A bit of a kludgy solution, but....

```
nums=({001..100});count=0;for file in *.JPG; do mv "$file" "${nums[$count]}.JPG"; let count+=1; done
```

Disclaimer: This won't work under Dash because of the brace expansion in assigning nums. You'll need to use Bash.

---

### Post by kaibob on 2010-01-12
This is beyond my knowledge level. Hopefully, a more knowledgeable forum member who better understands the issue will have a solution. 

If not, one alternative that does work is to remove the leading zero's, as in the following:

```
count=1 ; for file in *.JPG ; do mv "$file" ${count}.JPG ; count=$((count+1)) ; done
```

Another alternative is to begin counting at 100:

```
count=100 ; for file in *.JPG ; do mv "$file" "${count}.JPG" ; count=$((count+1)) ; done
```

---

### Post by @B6Mwu8fN9M on 2010-01-12
@falconindy: Thanks! That did exactly what I needed. I'm using Bash so there's no problems with wrong shell.

@kaibob: Thanks as well! Both your solutions worked. 

I will have to see if I need the leading 0's to decide which method I use.


Thanks for the help! I will look more into the rename command though so I can learn regex, but these solutions are better than that since they are more generic across distros. I don't need to worry about which version of rename is installed.

Thanks

---

