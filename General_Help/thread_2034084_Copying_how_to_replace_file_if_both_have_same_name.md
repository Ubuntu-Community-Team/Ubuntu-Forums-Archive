---
title: "Copying: how to replace file if both have same name but size is not the same?"
date: 2012-07-27
forum: General Help
---

### Post by jonnyboysmithy on 2012-07-27
I'm looking for a way to copy files: that will skip the ones with the same name and same size but replaces files that have the same name but a different size.

---

### Post by evilsoup on 2012-07-27
Are you actually just trying to copy files that have been modified, leaving those that haven't changed alone? I'm sure there are backup tools that can do that, but one quick & dirty solution (if you are OK with the command line)

```

for i in *; do if [ "$i" -nt /path/to/destination/"$i" ]; then cp "$i" /path/to/destination/"$i"; fi; done

```

This will copy everything in the directory that has a newer modification time than an existing file in the destination.

It won't copy over anything that doesn't have a same-named counterpart, but a simple

cp -n * destination/

will sort out anything that doesn't have a direct counterpart.

---

### Post by jonnyboysmithy on 2012-07-27
Nice! 
I was thinking I'll have to make a script or something, but I don't know enough shell script.... yet :)
Thank you!

---

### Post by papibe on 2012-07-27
Ho jonnyboysmithy.

It looks like a job for 'rsync'.

By default rsync will copy and update files based on modification time and size. However, you can specify only to check file size.

For instance:
```
rsync -av --size-only  source/  destination/
```
I hope that helps. Let us know how it goes.
Regards.

---

