---
title: "text files detected as binary?"
date: 2009-11-12
forum: General Help
---

### Post by hwttdz on 2009-11-12
A few log files for some programs I'm working on are detected as binary by grep and when attempting to view them using gedit I get a couldn't detect encoding error.  Any ideas on why this might be going on? / how can I "force" them into text files?

clearly grep -a works for grep, so it's principally the gedit thing I'm annoyed with.  less works fine, but I'd prefer something graphical.

---

### Post by hwttdz on 2009-11-24
It's because there are bad characters in the log file, namely the output of uninitialized variables. It would be nice if gedit displayed ??? characters instead of not opening the file, but that's neither here nor there.

---

### Post by dcstar on 2009-11-24
> **hwttdz said:**
> It's because there are bad characters in the log file, namely the output of uninitialized variables. It would be nice if gedit displayed ??? characters instead of not opening the file, but that's neither here nor there.

```
cat filename > whatever.txt
```

---

### Post by hwttdz on 2009-11-24
> **dcstar said:**
> ```
cat filename > whatever.txt
```

No effect.

---

### Post by wojox on 2009-11-24
Is this a C program you wrote?

---

### Post by hwttdz on 2009-11-24
I think it's mostly if not all fortran.  There may be a little bit of c and python.  Really I understand why gedit can't successfully open the files at this point.  One option would be to comment out the lines which are producing the crazy output, but I think I'd better do some more digging and figure out why the crazy output is happening in the first place.

---

### Post by dcstar on 2009-11-24
> **hwttdz said:**
> No effect.

```
cat -v filename > output.txt
```

---

### Post by hwttdz on 2009-11-25
Success.  Thanks, that's convenient, but I should probably figure out the source of the error anyways.

---

### Post by hwttdz on 2009-12-02
This can be added to one's .bashrc as a sort of fix.

```
function gedit()
{
	for f in "$@"
	do
		if [ -f "$f" ]
		then
			cat -v "$f" > "$f.bak"
			chmod --reference="$f" "$f.bak"
			mv "$f.bak" "$f"
		fi
	done
	/usr/bin/gedit $@
}

```

---

### Post by hwttdz on 2009-12-02
Updated to preserve permissions of file.  I suppose it now changes the modification time even if you don't change the file, this is not an issue to me so I will not fix.  I suppose it's just adding a flag to preserve the update time or using touch in much the same way I used chmod.

---

