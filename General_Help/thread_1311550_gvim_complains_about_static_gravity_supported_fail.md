---
title: "gvim complains about: static_gravity_supported failed"
date: 2009-11-02
forum: General Help
---

### Post by firebush on 2009-11-02
I've just updated to Karmic Koala.

When I run gvim, I get the following output printed to my terminal:
[FONT="Courier New"]
** (gvim:22953): CRITICAL **: gtk_form_set_static_gravity: assertion `static_gravity_supported' failed[/FONT]

From searching for this online, I see that this is a recognized bug relating to gtk and the X server somehow (see [402188]("https://bugs.launchpad.net/ubuntu/+source/vim/+bug/402188")).  Someone has suggested redirecting all stderr from gvim to /dev/null, but that's not very satisfying to me as there could be valid errors I'd like to see.  

I'd like to fix this.  Is there a way for me to get the modified version of gvim that has this fix?  The previous link references a patch, but all I'm able to find is the source code change to gvim.  Is there a patch that someone has produced that will fix this for us?  Has someone else found other ways to address this?

Thanks!

---

### Post by Giblet5 on 2009-11-02
Well, you *could* redirect (via append) the errors to ~/.xsession-errors just like the gnome environment does.

Window gravity support is not particularly useful in an application like gvim, and while I understand a certain "need" to have everything run perfectly smoothly, that rarely happens (except in code that I write, of course).

Take a look at ~/.xsession-errors if you think everything else in the gtk or kde worlds run peachy-clean.

```
#!/bin/bash

## Execute gvim, sending X/gtk errors to the standard place.

exec /usr/bin/gvim $* > /dev/null 2>>$HOME/.xsession-errors
```

Save that as qgvim, make it executable, and put it in your PATH somewhere. Then use qgvim as you would gvim, but more **q**uietly.

---

### Post by firebush on 2009-11-02
Thanks, Giblet5.

Based on your suggestion, I found a setup that works in my environment ok.

I've created a script based off of yours called 'gvim' in my home's bin directory.  I made sure that ~/bin was before the standard location of gvim (/usr/bin on my machine) for my PATH variable.  I needed this to be called gvim instead of qgvim so that other things on my system which call gvim and don't know about qgvim will call the one from my home directory as well.  Mercurial is an example of this in my environment.

Also, since I don't want all output to be removed, I just filter out the annoyances I don't want.

The result is:
```

#!/bin/bash

# Execute gvim, filtering out the gravity gtk failures.
if echo $* | grep "argv(0)" > /dev/null
then
    # This is being called by mercurial to use the DirDiff plugin.
    exec /usr/bin/gvim -f '+next' '+execute "DirDiff" argv(0) argv(1)' $4 $5 2>&1 \
        | grep -v gtk_form_set_static_gravity | grep -v RANDR | sed '/^$/d'
else
    # All other calls for gvim.
    exec /usr/bin/gvim $* 2>&1 | grep -v gtk_form_set_static_gravity \
        | grep -v RANDR | sed '/^$/d'
fi

```

---

### Post by trungd_t on 2009-11-03
Giblet5...you are da man! Works like a charm. Thanks.

I tried firebush's script as well, but after running the gvim, the terminal is blocked until the gvim exits or I have to put it in background.

Giblet5 version worked better for me. Thanks all.

---

### Post by iapx86 on 2009-11-06
Same thing happened to me, but efforts to fix the problem have made it worse.

I downloaded and built vim 7.2 from the original vim web-site.  That made things a little worse :frown:.  So I decided to use Synaptic to remove vim as thoroughly as possible, then used Synaptic to reinstall everything.

Now all I get from gvim is a debugging dump and crash :oops:.

Any ideas how to restore the system to where it simply complains about static_gravity?

---

### Post by jitterman on 2010-04-13
The script given by Giblet5 does not properly handle quoted arguments that contain spaces. Here is an improved version.```
#!/bin/bash
# Execute gvim, sending X/gtk errors to the standard place.
exec /usr/bin/gvim "$@" > /dev/null 2>>$HOME/.xsession-errors
```
Notice that the $* was replaced by "$@". The script by firebush can be improved in the same way.

---

