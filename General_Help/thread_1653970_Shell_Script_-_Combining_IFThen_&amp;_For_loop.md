---
title: "Shell Script - Combining IF/Then &amp; For loop"
date: 2010-12-27
forum: General Help
---

### Post by U2XS on 2010-12-27
I've created a shell script which must check if files are present within a folder.  If they are present, it must process them as needed.  The If/Then statement works on it's own and the For loop also does.  However, when I put them together, I see the following error message:
```
./newShell: line 3: [: too many arguments
```

My script looks like this:
```
# /bin/bash

if [ -f /home/sergio/Desktop/Images/input/* ]
	then
	for file in *.jpg *.JPG; do
		echo  $file
	done
fi
```

Is there a way to combine the two?

---

### Post by noah++ on 2010-12-27
I find I get the same error as you when I don't have a *for* loop nested in there. I think the problem is that you are giving *-f* several arguments -- i.e., the expansion of ***** -- when it only expects one.

You are trying to test if any file exists in a directory. [This person]("http://kenfallon.com/?p=4") was struggling with the same problem...

---

### Post by U2XS on 2010-12-27
Thanks!  Using his system, it works perfectly.

Though, I can see very clearly, how it would fail, I'm just shocked that the bash shell wouldn't be prepared for it or compensate for it.

---

### Post by noah++ on 2010-12-27
> **U2XS said:**
> I'm just shocked that the bash shell wouldn't be prepared for it or compensate for it.
Me too -- or at least shocked that it wouldn't have a separate test for it.

---

### Post by mobilediesel on 2010-12-28
It seems you may have solved it but here's another way to do it:
```
for file in *.{jpg,JPG}; do
if [[ -f "$file" ]]; then
echo "$file"
fi
done
```

---

### Post by U2XS on 2010-12-28
Ahh!  I love the idea, but it doesn't actually suite my needs :(

I need it to first check if a file (or files) exist and if so, to run a series of commands.  *Then* within those commands I would have a for loop.

---

