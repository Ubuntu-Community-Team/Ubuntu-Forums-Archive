---
title: "Permission denied and sudo for everything after recent update?"
date: 2009-11-24
forum: General Help
---

### Post by beju0506 on 2009-11-24
Hey guys,

I upgraded my linux box to Ubuntu 9.10 recently and everything was going well... but last night I did an update with the update manager and it asked me to restart. I did so, and now when I connect to the computer via SSH (i.e. in a terminal) it gives me "permission denied" for nearly everything and then I have to do "sudo <whatever>" to accomplish it. All sorts of things that never needed it before, i.e. compiling a c++ program with g++, opening a file, copying things, etc etc... It's really obnoxious. Does anyone know what could have happened, or how I can fix that?

Any help you can give would be awesome!! :)

Thanks!

-Justin

---

### Post by fluffman86 on 2009-11-24
Check the permissions in your home directory with

ls -la

Almost everything except for .gnupg and .dmrc should be -rwxr-xr-x and belong to user, group user.

First, make yourself the owner with:

sudo chown -R user:user /home/user/

After that, things should work.  If not, you may need to change a few more permissions.  Post back with more if necessary.

---

