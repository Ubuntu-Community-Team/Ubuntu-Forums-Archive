---
title: "&quot;Error creating directory: permission denied&quot;"
date: 2012-07-25
forum: General Help
---

### Post by edjski on 2012-07-25
In ubuntu 11.10, when trying to import pictures using gThumb, I get the error:
"Error creating directory: Permission denied"
-I recently moved the picture directory to a different partition and now it seems gThumb is unable to create new directories (I have it set to organize imported photos by date) for the imported photos.

Do I need to give gThumb permission to create new directories? Or is it based on user (I'm able to create new directories in the partition with my normal user...)?
Do I change permissions at the partition?

Thanks,
ed

---

### Post by galvatron408 on 2012-07-28
you could always create a soft link to it.

i.e.
cd /location/of/where/directory/used/to/be
sudo ln -s /location/to/where/directory/is name_of_softlink

Make sure the name of the softlink is what your software is looking for.

---

### Post by Irihapeti on 2012-07-28
I don't think that creating a soft link will fix the problem.

You need to change the permissions.

With the partition mounted

```
cd /where/partition/is/mounted
sudo chown user:group .
```

Make sure you include the final dot

"user" and "group" are your own username and groupname. On a machine with only one user, they are likely to be the same.

---

### Post by galvatron408 on 2012-07-28
of course, creating a softlink will solve the problem but if you want to create a new directory, thats fine too.

---

