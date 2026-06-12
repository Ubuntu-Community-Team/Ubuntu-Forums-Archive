---
title: "bash has begun acting strangely"
date: 2011-02-16
forum: General Help
---

### Post by zeigfreid on 2011-02-16
Hi

I'm using Ubuntu 10.04! 

Recently I've encountered a problem. When I open a new terminal in my GUI I am greeted immediately by the following:

bash: 1 2 + 1 : syntax error in expression (error token is "2 + 1 ")

In an attempt to find out what was going on, I ran the command '$ bash -v' to get a more verbose error message. I found the above error message nestled in these lines:

TTY_CTR=`cat $TTY_CTR_FILE`
cat $TTY_CTR_FILE
TTY_CTR=$(( $TTY_CTR + 1 ))
bash: 1 2 + 1 : syntax error in expression (error token is "2 + 1 ")
echo $TTY_CTR | cat > $TTY_CTR_FILE

Not really sure what it all means. After running that command, anything that I do is followed by

__git_ps1) \$ 
__git_ps1
__gitdir)"
__gitdir)
__gitdir

which were the last five lines printed when I invoked 'bash -v'.

Now, I'm no Ubuntu expert or anything, and I don't really know much about scripts and bash and all that jazz (though I'm making an effort to learn) but this just doesn't seem right. Any ideas as to what I might have done to deserve this?

Help will be greatly appreciated! Thanks!

z.

---

### Post by quadproc on 2011-02-16
> **zeigfreid said:**
> 
Recently I've encountered a problem. When I open a new terminal in my GUI I am greeted immediately by the following:

bash: 1 2 + 1 : syntax error in expression (error token is "2 + 1 ")

It looks like something fouled up some file associated with bash.  The most likely place to look is in ~/.bashrc; that file may have been edited by accident.

quadproc

---

