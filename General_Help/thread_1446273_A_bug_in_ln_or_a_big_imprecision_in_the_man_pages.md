---
title: "A bug in ln or a big imprecision in the man pages?"
date: 2010-04-03
forum: General Help
---

### Post by HotForLinux on 2010-04-03
1. 

If I want to make a soft link (or symbolic link) called file_a (in directory dir_A) to an existing file called file_b (in directory dir_B), using relative paths, with the command:

```
**$ln -s *path_to_file_b*  *path_to_file_a***
```

then, I have to write the path_to_file_a relative to my present working directory ($PWD) but the path to file_b must be relative not to the same $PWD but to Dir_A

Is that a bug or just a strange thing and an big imprecision in the ***man pages***?


----------
2. 
Also, the man page for "ln" says:

"SEE ALSO
       link(2), symlink(2)"

What/where is the "symlink" command or man page??

---

### Post by gmargo on 2010-04-03
The symlink(2) man page is in the **manpages-dev** package.

The ln(1) form you are using ("1st form" in the man page) is 
```

ln -s TARGET LINK_NAME

```The LINK_NAME is the thing you are going to create.  It is a name entry in a particular directory. The ln command has to know where to create the LINK_NAME so you must give a path either absolute or relative to the directory in which you execute the ln command ($PWD.)  Then **ln** can go to the directory of the LINK_NAME to create the name entry.

The TARGET is the thing that the symbolic link will point to, so the path to the TARGET must be absolute or relative to the directory in which the symbolic link exists.

Clear as mud now?

---

### Post by The Cog on 2010-04-04
I wouldn't regard this as a bug in ln. Just a slight misunderstanding on your part as to how ln works. The first argument is the content of the link, and gets inserted into the link file (the second argument). The fact that you can optionally use a path relative to your current working directory to say where the link should be placed doesn't change what you asked to be put in the link.

The man page is (as with many man pages) cryptic to the point of being useless. It serves as a reminder as to the syntax once you know what the command does, not as a tutorial. I sometimes think it is a point of pride to be able to write technically accurate but practically useless man pages.

---

### Post by HotForLinux on 2010-04-04
> **The Cog said:**
> I wouldn't regard this as a bug in ln. Just a slight misunderstanding on your part as to how ln works. The first argument is the content of the link, and gets inserted into the link file (the second argument). The fact that you can optionally use a path relative to your current working directory to say where the link should be placed doesn't change what you asked to be put in the link.
Yes, I understand how the command works.
Even if it inserts the relative path to the target in the context of the new link, what I cannot guess, nor deduce from the man page, is relative to whom must that relative path be given in the command, as a parameter. There are two possibilities that seem most logical. But none of them more than the other. I doubt that any tutorial explains this and its place should be in the man page specification. Only trial and error can tell you which is the correct one.


> **The Cog said:**
>  The man page is (as with many man pages) cryptic to the point of being useless. It serves as a reminder as to the syntax once you know what the command does, not as a tutorial. I sometimes think it is a point of pride to be able to write technically accurate but practically useless man pages.

I share that opinion: many man pages are intended to be so technically perfect that become useless and that, at the same time, they are not supposed to be tutorials. But very often they have important holes, which make them imperfect from the technical as well as from the common user point of view. I think this is one. 

Let's try to make them better.

---

### Post by HotForLinux on 2010-04-04
> **gmargo said:**
> ....The ln command has to know where to create the LINK_NAME... 

Yes... And the USER _has to know_ relative to whom must he write the relative paths in each parameter.

---

