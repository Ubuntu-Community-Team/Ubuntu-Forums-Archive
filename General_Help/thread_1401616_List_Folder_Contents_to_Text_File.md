---
title: "List Folder Contents to Text File"
date: 2010-02-08
forum: General Help
---

### Post by joeknoodle on 2010-02-08
For the life of me I can't remember how to list the contents of a folder to a text file.

I'm trying to list all my music, including all subfolders, etc. to a text file, but I can't remember the command.

Please help.

---

### Post by t4thfavor on 2010-02-08
> **joeknoodle said:**
> For the life of me I can't remember how to list the contents of a folder to a text file.

I'm trying to list all my music, including all subfolders, etc. to a text file, but I can't remember the command.

Please help.

```

ls -R ./ > list.txt

```

should do it, if you install tree it will look a bit more manageable.

---

### Post by gmargo on 2010-02-08
> list the contents of a folder to a text file.
```

ls > file.txt

```> I'm trying to list all my music, including all subfolders, etc. to a  text file```

find $HOME -type f -iname '*.mp3' -print > music.txt

```

---

### Post by joeknoodle on 2010-02-08
Thanks y'all. I kept forgetting the >.

I feel so stupid.

---

