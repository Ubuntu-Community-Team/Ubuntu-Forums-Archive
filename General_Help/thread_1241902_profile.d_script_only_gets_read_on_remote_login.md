---
title: "profile.d script only gets read on remote login"
date: 2009-08-16
forum: General Help
---

### Post by t0mm1e on 2009-08-16
I'm not sure where to look. I've made my own /etc/profile.d/partyflock.sh script with a few aliases.

Is this the right place?

What I noticed: the aliases work perfectly when doing a 'ssh localhost' (though on CTRL-D the shell hangs), but just opening terminals from within Ubuntu desktop doesn't load the scripts therein. Only what's in my homedir as .bash_rc and the like.

I'd like to set variables and aliases for all users and in the future use this on my servers so I have the same set of aliases available everywhere.

---

### Post by geirha on 2009-08-16
profile is only read for interactive login shells (which you happen to start when you connect with ssh). For interactive non-login shells, bashrc is read. In gnome-terminal there's a setting where you choose whether to start a login shell or not when you start gnome-terminal. By default it starts a non-login shell.

---

### Post by t0mm1e on 2009-08-17
I understand that.
But am I now logged in once for the X session? Shouldn't profile.d be read as a global include then?

How am I supposed to get a consistent shell now on my local machine, just execute /etc/profile from within .bashrc skeleton is the only thing I can come up with.

---

### Post by geirha on 2009-08-18
> **t0mm1e said:**
> I understand that.
But am I now logged in once for the X session? Shouldn't profile.d be read as a global include then?


Only shells read profile, not X.

> **t0mm1e said:**
> 
How am I supposed to get a consistent shell now on my local machine, just execute /etc/profile from within .bashrc skeleton is the only thing I can come up with.

Typically, you put the aliases in your ~/.bashrc, or the global /etc/bash.bashrc.

The default ~/.profile also sources .bashrc.

---

