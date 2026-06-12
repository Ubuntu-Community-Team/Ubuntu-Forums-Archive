---
title: "Simple file management question"
date: 2010-07-07
forum: General Help
---

### Post by fiddler616 on 2010-07-07
Hello,

I have two questions:

How do I remove files from Directory A if their name appears in Directory B?

How do I move foo.jpg and bar.jpg from Directory C to Directory D if and only if foo.png and bar.png appear in Directory D?

I suspect there's probably a bash one-liner for this, but...I can't come up with it.

Thanks in advance.

---

### Post by amauk on 2010-07-07
untested, but

> **fiddler616 said:**
> Hello,

I have two questions:

How do I remove files from Directory A if their name appears in Directory B?

```
DIR_A="/path/to/dir_a"
DIR_B="/path/to/dir_b"

IFS=$'\n'

for FILE in $DIR_A/*; do
	if [ -f "$DIR_B/$(basename "$FILE")" ]; then
		rm -f "$FILE"
	fi
done
```

> **fiddler616 said:**
> How do I move foo.jpg and bar.jpg from Directory C to Directory D if and only if foo.png and bar.png appear in Directory D?

I suspect there's probably a bash one-liner for this, but...I can't come up with it.

Thanks in advance.

```
DIR_C="/path/to/dir_c"
DIR_D="/path/to/dir_d"

FILES=("foo.jpg", "bar.jpg")

for FILE in $FILES; do
	if [ -f "$DIR_D/$FILE" ]; then
		mv "$DIR_C/$FILE" "$DIR_D/$FILE"
	fi
done
```

---

### Post by geirha on 2010-07-07
Slightly bit shorter:
```

cd /path/to/dir_b &&
for f in *; do
  [[ -f /path/to/dir_a/$f ]] && echo rm -vf "/path/to/dir_a/$f"
done

```
If you want the above to also cover hidden files, run ```
shopt -s dotglob
``` first

```
cd /path/to/dir_d &&
for f in foo.png bar.png; do
  [[ -f $f ]] && echo cp /path/to/dir_c/$f .
done

```
Added an echo in front of rm and cp so you can do a dry-run first, and if it looks right, remove the echo.

@amauk
You separate array elements with whitespace, not comma, and $FILES only expand to the first element (${FILES[0]}), you want "${FILES[@]}" (including the "" quotes). Also, the convention is to use lowercase variable names; uppercase for internal shell variables and environment variables.

---

### Post by fiddler616 on 2010-07-07
Thanks to both of you. I'm about to try the first one.

Unfortunately I miscommunicated. What I meant for the second one is that Directory C has a whole bunch of files: foo.jpg, bar.jpg, ... , spam.jpg, eggs.jpg. Instead of doing the process for just foo and bar, how do I do it for every jpg (and jpg only, please) in the directory?

---

### Post by energybeing on 2010-07-07
If you want to move all .jpg files in a folder, specify *.jpg for the filename.

---

### Post by fiddler616 on 2010-07-07
> **energybeing said:**
> If you want to move all .jpg files in a folder, specify *.jpg for the filename.

Good call...why couldn't I think of that?

---

