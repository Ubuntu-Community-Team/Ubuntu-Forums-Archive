---
title: "Add to PATH"
date: 2009-11-02
forum: General Help
---

### Post by iEthan on 2009-11-02
I just installed a RubyGem (Jekyll, on GitHub) and the installation went smoothly. But when I go to Terminal to do the "jekyll" command, it doesn't work. It doesn't think it's a command.

So, how do I add /var/lib/gems/1.8/gems/mojombo-jekyll-0.5.4/bin to my PATH? That's where the executable is located.

---

### Post by Matt__ on 2009-11-02
Either enter the full path of executable into terminal 
or
create an alias of the full path (current session only)
or 
add this to etc/profile
PATH=$PATH:'full path of executable'
export PATH

as a newb user of Ubuntu I'm not sure if this will affect root you may have
to add it to the .bash_profile (as in mandrake systems)
or you could just copy the whole thing into a directory that IS in your PATH :)

---

