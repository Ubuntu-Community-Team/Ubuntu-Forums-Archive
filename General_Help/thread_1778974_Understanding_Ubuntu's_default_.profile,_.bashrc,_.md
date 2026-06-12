---
title: "Understanding Ubuntu's default .profile, .bashrc, etc"
date: 2011-06-09
forum: General Help
---

### Post by Adam's AI on 2011-06-09
I've been doing some reading on the system files associated with the terminal, and I know there are basic comments in the files themselves, but does anyone know where I can find a more in-depth line-by-line description of what these file contents (in a vanilla Natty Ubuntu installation) mean?

Thanks

---

### Post by dFlyer on 2011-06-09
> **Adam's AI said:**
> I've been doing some reading on the system files associated with the terminal, and I know there are basic comments in the files themselves, but does anyone know where I can find a more in-depth line-by-line description of what these file contents (in a vanilla Natty Ubuntu installation) mean?

Thanks

Your magic word is man, it's short for manual. Enter man and then what you want to know. Example:

man bash
man config

Etc.

---

### Post by AlphaLexman on 2011-06-09
The files you are looking for are these: (you only need ONE of the files in the bullet list.)

At login, bash reads '**/etc/profile**' and then the first file found from:
[LIST]
[*]~/.bash_profile
[*]~/.bash_login
[*]~/.profile
[/LIST]
After that, ~/.bashrc is invoked, by default in ubuntu, from '~/.bash_profile'.

---

