---
title: "Why does ssh-agent override ssh -i option?"
date: 2010-06-21
forum: General Help
---

### Post by mintroll on 2010-06-21
I'm not familiar with how ssh-agent is configured in Ubuntu (10.04), I don't even think this is a Ubuntu specific issue - but as far as I understand, shouldn't the identity option to ssh override ssh-agent?

I have several servers I connect to with subversion repositories on, using keys, and on the server each key is restricted to running svnserve.

I also need to ssh into several of these boxes, which I want to use keys for as well (no keyboard passwords).


So, I set up my local subversion config file with a tunnel using ssh -i pointing to the restricted key,
I then added the unrestricted key to ssh-agent using ssh-add

Now, when I run svn, ssh-agent jumps in and uses the unrestricted key...

(I know this, because the restricted key sets the root of the subversion repositories... so when using the unrestricted key, svn can't find the repository - it connects ok, but then exits not finding a valid repository).


So, my question is, shouldn't the identity option to ssh in my subversion tunnel override ssh-agent?

If not, does anyone have any suggestions?


As an aside,
If I remove all keys using ssh-add -D, then the subversion tunnel works fine (using the restricted key) and I can connect to the servers using ssh -i /path/to/unrestrictedfile explicitly (that is, use the unrestricted key)... but then I have to type that every time I log in... and I'm a lazy typer.

---

