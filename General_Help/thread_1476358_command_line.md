---
title: "command line"
date: 2010-05-07
forum: General Help
---

### Post by lorenzo.lewisjr on 2010-05-07
How do i use file manipulation tools on a command line?

---

### Post by spiky001 on 2010-05-07
can you explain  bit more detail

---

### Post by dracayr on 2010-05-07
rm file &#8592; deletes file
cp file file2 &#8592; copys file to location file2. file2 can be a directory, in which case the file is placed inside the directory, or a path with file name, in which case the file is renamed also.
mv file [file2 file3...] dest &#8592; moves files to dest
cp -r dir dest &#8592; copys directory, all contents and subdirectorys to dest
rm -r dir &#8592; deletes Directory. Use with care!
ln -s Dest link_name &#8592; creates symlink
ln dest link_name &#8592; creates hard link
mkdir &#8592; creates directory
rmdir &#8592; deletes empty directory
touch file &#8592; creates file or updates timestamp if file exists

dracayr

---

