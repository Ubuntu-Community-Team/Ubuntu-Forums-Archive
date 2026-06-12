---
title: "Merge Netbook Remix and Desktop"
date: 2010-01-29
forum: General Help
---

### Post by grizato on 2010-01-29
Ok, I've been mesing around with my distros lately and at the moment I am running a dual boot of UNR and Ubuntu Desktop. I was wondering if there is a way to sort of merge them together as much as possible(e.g. The home directory). So that I have the same files and programs but just a diffirent DE.

I am mainly posting this thread for others with the same interest!:o

---

### Post by Brandon Williams on 2010-01-30
This is difficult to do, since they are both fundamentally gnome desktop environments. You would have to come up with a way to dynamically set the configuration for the panels, whether or not nautilus runs, and whether or not netbook-launcher runs. This is difficult to do in a way that automatically "remembers" the differences in panel and theme configuration, which is part of the reason why the desktop-switcher application was so buggy and then eventually discarded.

---

### Post by grizato on 2010-01-31
Is there a way that I can mount directories on my deskotp ubuntu and kind of 'replace' the ones in UNR so I'd have the same apps and files but just another desktop mode?

---

### Post by Brandon Williams on 2010-01-31
Hmmm. That might be workable. If you had two copies of each of the important configuration directories, then you could use symlinks to dynamically select which one to use at login. I think that ~/.config and ~/.gconf are probably enough, though ~/.cache might also be important.

The trick will be to come up with a way to identify which session type you want. If you look in /usr/share/xsessions/, you'll find a few .desktop files that are used to identify session types to gdm. You could add a .desktop file there that specifies a custom Exec command, one that takes an argument indicating which session type you want and reconfigures the symlinks accordingly. Something like this:
```
#!/bin/sh

# first arg is symlink name; second arg is base directory
reset_symlink()
{
    [ -e $HOME/$1 ] && rm -f $HOME/$1
    ln -s $HOME/$2 $HOME/$1
}

# get first arg; use default value if no arg is present
SESSION_TYPE="${1:-netbook}"
reset_symlink .config .config-$SESSION_TYPE
reset_symlink .cache  .cache-$SESSION_TYPE
reset_symlink .gconf  .gconf-$SESSION_TYPE

exec gnome-session
```

This example is quite simple. It assumes that the base directory (e.g. $HOME/.config-netbook) already exists and that the symlink target, if it already exists, is a symlink, not a real directory.

It's worth a try. It might work for what you're trying to accomplish. Bear in mind that you won't be able to have two concurrent gnome session running for the same user but different session types. That said, gnome doesn't handle that very well any way.

---

