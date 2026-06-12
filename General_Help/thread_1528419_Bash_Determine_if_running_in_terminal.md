---
title: "Bash: Determine if running in terminal"
date: 2010-07-10
forum: General Help
---

### Post by realillusions on 2010-07-10
Hey everyone,

I'm writing a bash script to move files around based on various bits of metadata. For a few reasons, this script will be run regularly both from the terminal, and from the nautilus-scripts folder ("graphically", if you will).

What I'm stumped on is having the script defer outputs based on which mode the script is running in. For example, how can I have the script know whether to echo error statements, or pump them out to zenity based on the method of invocation?

---

### Post by DaithiF on 2010-07-10
Hi, 
I'm not in front of a gui where i can test this right now, but I think this should work:

```
[ -t 0 ] && terminal=1

```then later, 

```
[ $terminal ] && do terminal stuff   

```or ```

[ ! $terminal ] && do gui stuff

```(The -t operator tests if a file descriptor is associated with a terminal, and 0 is the file descriptor for stdin)

---

### Post by realillusions on 2010-07-10
I had a hunch it'd be a stdio-related comparison, but didn't know where to look. Works great, thanks!

---

