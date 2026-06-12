---
title: "How can I mass-create files with titles from another file?"
date: 2012-05-30
forum: General Help
---

### Post by J-E-N-O-V-A on 2012-05-30
I have one file containing a vertical list of poem titles and I want to transform them into files, I thought it would be fairly simple for you guys so I'm asking rather than trying to figure it out.

---

### Post by papibe on 2012-05-30
Hi J-E-N-O-V-A.

Could you post a little example? Something like a few lines of your file, and the desired result.

Regards.

---

### Post by J-E-N-O-V-A on 2012-05-30
> **papibe said:**
> Hi J-E-N-O-V-A.

Could you post a little example? Something like a few lines of your file, and the desired result.

Regards.
Suppose list.txt contains the information:

title1.txt
title2.txt
title3.txt
title4.txt

and ls returns 

list.txt
directory1

I would like to run a command that results in title1, title2 and title3 being created as files withing directory1 so that if I cd into directory1 and run ls I get:

title1.txt
title2.txt
title3.txt
title4.txt

---

### Post by papibe on 2012-05-30
Thanks.

You can accomplish that with a little script.

To run through all the names:
```
while read -r file; do
    echo "$file"
done < list.txt
```
That will read every line on list.txt, put it in the variable file, and print it.

To create an empty file with an specific filename you can use the command 'touch':
```
$ ls

$ touch this_file
$ ls
this_file

```
Combining both ideas:
```
while read -r file; do
    touch "$file"
done < list.txt
```
I hope that helps, and tell us how it goes.
Regards.

---

