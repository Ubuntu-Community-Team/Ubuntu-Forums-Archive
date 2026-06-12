---
title: "mv dir and files without moving the container dir"
date: 2010-06-27
forum: General Help
---

### Post by camrant on 2010-06-27
I would like to know how to make a move of a dir and its contained dir´s and files without moving the containing dir itself.

IE: I would like to mv the contents of say /cam/movies1 into /cam/movies

without creating the following /cam/movies/movies1

I know that I could simply rename /movies1 to /movies. But in my case /movies already exists so I do not want to overwrite it I just want to move everything into the dir minus the old dir itself.

Is that clearly explained? Thanks

---

### Post by stderr on 2010-06-27
```
mv /cam/movies1/* /cam/movies
```

should work.

edit: And if you're ever worried about what a mv command might end up doing, use the -i flag to use interactive mode (prompts before moving something). Additionally, you might like to add the -u (update) flag - this way you won't end up overwriting files of the same name unless the file you're moving is newer than the old one.

---

### Post by camrant on 2010-06-27
thanks for some reason I had thought that it wouldn´t pick up the dir only the files. But it worked.

This makes me wonder though what if I only wanted the directories and not any of the individual files in the immediate subdir I am moving from

---

### Post by dragos240 on 2010-06-27
> **camrant said:**
> thanks for some reason I had thought that it wouldn´t pick up the dir only the files. But it worked.

This makes me wonder though what if I only wanted the directories and not any of the individual files in the immediate subdir I am moving from

Try adding -r for the directories.

---

