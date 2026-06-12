---
title: "alias behaving differently on ubuntu than Mandriva"
date: 2010-06-07
forum: General Help
---

### Post by mathog on 2010-06-07
In .bashrc in Ubuntu 10.04LTS I have this line:

```
  alias cp="cp -i"

```
whereas in Mandriva 2010.0 in /etc/profile.d/alias.sh there is this line:

```
  alias cp="cp -i"

```
In both of them:

```
% alias | grep cp
alias cp='cp -i'

```
So far so good.  They act the same for this:

```
% cd /tmp
% touch src
% cp src dst
% cp src dst
cp: overwrite `dst'? Y

```
but here they diverge:

```
% cp -f src dst

```
On Mandriva the -f overrides the -i and there is no prompt, whereas on Ubuntu the -i takes precedence and the -f is ignored.

Where is this difference in behavior coming from?

---

### Post by dcstar on 2010-06-08
> **mathog said:**
> 
.........
On Mandriva the -f overrides the -i and there is no prompt, whereas on Ubuntu the -i takes precedence and the -f is ignored.

Where is this difference in behaviour coming from?

From man cp:

```
       -f, --force
              if an existing destination file cannot be opened, remove it  and
              try again (redundant if the -n option is used)
```

As far as I can see it is working as it should be in Ubuntu.

---

### Post by mathog on 2010-06-08
> **dcstar said:**
> From man cp:

```
       -f, --force
              if an existing destination file cannot be opened, remove it  and
              try again (redundant if the -n option is used)
```

As far as I can see it is working as it should be in Ubuntu.

also

```
       -i, --interactive
              prompt before overwrite
```

Looks like the Ubuntu behavior does correspond to the man page description.  What's odd though is that this is all the same program, gnu cp.  Different versions, but I don't think that is the key issue.  The one thing that does seem to correlate with this is whether or not /bin/cp is linked to libselinux.so.  When it is, then the Ubuntu behavior is observed, when it isn't, then the Mandriva behavior is.

---

