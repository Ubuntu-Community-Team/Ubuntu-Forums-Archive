---
title: "editing the PATH environment"
date: 2009-12-13
forum: General Help
---

### Post by zeelog on 2009-12-13
I can not figure out how to edit the PATH environment variable
 in Ubuntu. There's no PATH defined in /etc/profile and I can't
 find it anywhere else either. I can see what the PATH is with
 the env command and I can add to a variable with the export command,
 but I'd like to remove stuff, and then add stuff.  This used to
 be no problem when the PATH was defined in /etc/profile. I'd just
 use a text editor, but now I can't even find where the PATH is defined.
 Any help would be appreciated.

---

### Post by diesch on 2009-12-13
The default $PATH is set in */etc/environment*, but you can always modify it in /etc/profile or your user's *.bashrc*

---

### Post by slakkie on 2009-12-13
export PATH=$PATH:/path/to/somedir

You can do this in your terminal, for one session or add it to your .bashrc and/or .zshrc depending on the shell you use (bash or zsh in my example).

---

### Post by spiderbatdad on 2009-12-13
In Karmic, if you look at .profile in your home directory, I believe you will see how /home/user/bin is added to $PATH. You can use as an example, or create the directory bin inside /home and you can put executables in there.

---

