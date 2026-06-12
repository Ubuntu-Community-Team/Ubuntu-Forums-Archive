---
title: "For Loop help"
date: 2011-07-06
forum: General Help
---

### Post by mistertee on 2011-07-06
Hi there, just looking for a quick assist on writing a for loop.

So I have flat file with a list of hostnames called "list1".  This is just a small number of hosts within the population on my subnet.  I then have a directory that contains a file for each hostname on my subnet.  What I need to do is write a little for loop that looks only at the files for those hosts in "list1" that do not contain a certain attribute.  What I am having problems with is defining $HOSTNAME as the hosts in "list1" and telling grep to list files that do not include the attribute.

So something like

!#/bin/bash
for
each $HOSTNAME in list1
do
grep -l 'all that do not contain this attribute' * .c
done

Can someone give me a little help please?

Thanks!!

---

### Post by stlsaint on 2011-07-06
You should ask for help in the programming section of the forum.

---

### Post by mistertee on 2011-07-06
OK thanks, I'll repost there.

---

### Post by decoherence on 2011-07-06
Just to get you started, instead of

```

for
each $HOSTNAME in list1

```

you want

```

for HOSTNAME in $(cat list1)

```

You'll also probably want to reference $HOSTNAME somewhere in the body of the loop. I'm not totally clear on what you're trying to do so no suggestions here. I'll take a closer look if I have time but that might be all you need.

And yes, this should be in the programming forum ;)

---

