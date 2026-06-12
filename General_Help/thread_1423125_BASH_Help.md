---
title: "BASH Help :\"
date: 2010-03-06
forum: General Help
---

### Post by Elfo33 on 2010-03-06
I'm having a bit of trouble Googling the appropriate command for this.  I'm attempting to write a simple script which changes the name of each child directory in a parent direcotry (i.e. "Folder Two" to "2"), perform an action, and then rename the folder to it's original name.  Any gurus out there with a quick fix?

---

### Post by cogier on 2010-03-06
Not sure of the way to do this with BASH but there is a program in the repository called GPRename that claims it can change file and directory names in a batch.

---

### Post by Eraemaajaervi on 2010-03-06
you mean like


```

ls -d */ | while read dir; do 
  new="folder 2";  
  mv "$dir" "$new"; 
  echo "something happens here"; 
  mv "$new" "$dir"; 
done;

```

?

---

### Post by cong06 on 2010-03-06
> **Eraemaajaervi said:**
> ```
ls -d */ | while read dir; do 
new="folder 2";  
mv $dir "$new"; 
echo "something happens here"; 
mv "$new" "$dir"; 
done;
```
Be very careful with that script. That should rename all folders to the same name, effectively deleting them.


Depending on how you wanted to rename them, you could look into the "rename" command.
It actually handles regular expressions. Check out the man page.

---

### Post by Elfo33 on 2010-03-06
Thank you Eraemaajaervi, I think that will do exactly what I need :D

---

### Post by Eraemaajaervi on 2010-03-06
> **cong06 said:**
> Be very careful with that script. That should rename all folders to the same name, effectively deleting them.


Depending on how you wanted to rename them, you could look into the "rename" command.
It actually handles regular expressions. Check out the man page.

yes, if you leave away the line
```
mv "$new" "$dir"; 
```

this renames the folder back to it's original name.

be very careful with special characters, like spaces, quotes, &'s and so on!

---

### Post by cong06 on 2010-03-06
> **Eraemaajaervi said:**
> yes, if you leave away the line
```
mv "$new" "$dir"; 
```

this renames the folder back to it's original name.

I should probably read the whole thing before I criticize >.<

---

### Post by geirha on 2010-03-06
> **Eraemaajaervi said:**
> be very careful with special characters, like spaces, quotes, &'s and so on!

That is only an issue because you use ls (and in addition you forgot to quote $dir). The shell can handle pathnames quite safely.

```

tmpname="some name"
if [[ -e $tmpname ]]; then
  echo >&2 "$tmpname already exists. Bailing out."
  exit 1
fi
for dir in */; do
  mv "$dir" "$tmpname"
  echo "do stuff"
  mv "$tmpname" "$dir"
done

```

---

