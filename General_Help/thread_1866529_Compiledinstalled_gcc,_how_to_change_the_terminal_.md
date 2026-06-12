---
title: "Compiled/installed gcc, how to change the terminal command for it?"
date: 2011-10-21
forum: General Help
---

### Post by pr0grammer1 on 2011-10-21
After compiling and installing a new copy of gcc to test something last week, my installation seems to have taken over the gcc command in terminal (to run the usual copy of gcc, I need to use gcc-4.6 instead). How can I revert this?

---

### Post by hwttdz on 2011-10-21
You can:
1) give the full path to the one you want (simplest, also involves some effort)
2) make sure the one you want occurs in your path before the one you don't (I don't like this, as you probably in general want /usr/local to override /usr, or wherever you've installed)
3) make a link from somewhere in your path before the one you don't want to the one you do want (I might suggest ~/bin)
4) alias the gcc command to point to the one you want (easy, but sometimes substitutions are weird)

---

### Post by TeoBigusGeekus on 2011-10-21
You could create an alias or uninstall the new version of gcc.

---

### Post by pr0grammer1 on 2011-10-21
> **hwttdz said:**
> You can:
1) give the full path to the one you want (simplest, also involves some effort)
2) make sure the one you want occurs in your path before the one you don't (I don't like this, as you probably in general want /usr/local to override /usr, or wherever you've installed)
3) make a link from somewhere in your path before the one you don't want to the one you do want (I might suggest ~/bin)
4) alias the gcc command to point to the one you want (easy, but sometimes substitutions are weird)

How would I do #4? I managed to find it in /bin and delete it and it's working now, but it'd be nice to know how to have both versions installed in case I need it again in the future.

---

### Post by hwttdz on 2011-10-22
The two I like best:

3) make a link from somewhere in your path before the one you don't want to the one you do want (I might suggest ~/bin)

cd
mkdir bin
cd bin
ln -s /usr/bin/gcc gcc

and add this block to your .bashrc if it's not already there (after any other path manipulation happens, at the end would certainly be safe):
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

in this case if you want to go back to using the one you installed, just delete the link, and then you can remake it if you want to switch back.

4) alias the gcc command to point to the one you want (easy, but sometimes substitutions are weird) 
put this in your .bashrc

alias gcc='/usr/bin/gcc'

then you can just "unalias gcc" to go back to using the one you installed, though this change will only affect the one terminal you're in.

---

