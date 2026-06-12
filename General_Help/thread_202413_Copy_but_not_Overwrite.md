---
title: "Copy but not Overwrite"
date: 2006-06-23
forum: General Help
---

### Post by tobeon on 2006-06-23
Anyone know the command to copy but not overwrite? The best I could find was

cp -i -r

where it prompts you, but then I keep having to press N enter N enter N enter... which sucks royally there must be a better way... please?

---

### Post by tobeon on 2006-06-23
aah -u seems to do the job quite well

---

### Post by droazen on 2006-06-25
There's a really cool command called 'yes' that was made just for this purpose (automating repetitive prompts). It repeatedly outputs the string you give it, so you can pipe it into the command that's prompting you like so:

```
yes n | cp -i -r /foo
```

And every time cp pauses with a prompt it will be fed an 'n' + newline from yes :)

---

