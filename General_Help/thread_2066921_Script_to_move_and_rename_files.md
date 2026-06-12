---
title: "Script to move and rename files"
date: 2012-10-05
forum: General Help
---

### Post by publicjo on 2012-10-05
Hi,
I have got files that I would like to move and rename.

In the directory ~/ab100/fMRI
I have got the files dti_ab100_ac2.nii and bold_ab100_ac6.nii

In the directory ~/ed124/fMRI
I have got the files dti_ed124_ac1.nii and bold_ed124_ac8.nii

etc...

I would like to have
In the directory ~/ab100
the files dti_ab100.nii and bold_ab100.nii

In the directory ~/ed124
I have got the files dti_ed124.nii and bold_ed124.nii


Any idea of a script for doing this ?
many thanks !!
publicjo

---

### Post by Pletched on 2012-10-05
Something like this?

```

cp -r firstDirectory ~/ab100
cp -r secondDirecory ~/ed124 

```

---

### Post by publicjo on 2012-10-05
Thanks for your quick reply.
The thing is that I do not have only 2 directories like this but >100 so I am looking for a script using something like "for...." to do this automatically
thanks!

---

### Post by cmont899 on 2012-10-05
This should do it (untested):

```
#!/bin/bash

for dir in ab100/fMRI ed124/fMRI; do
        cd ~/$dir
        for i in $(ls); do
                mv $i $(echo i | sed 's/_ac[[:digit:]]//')
done

```

---

### Post by Pletched on 2012-10-05
I think it should be. 

```

#!/bin/bash

for dir in .*/fMRI; do
        cd ~/$dir
        for i in $(ls); do
                mv $i $(echo i | sed 's/\/fMRI//')
done
```

---

