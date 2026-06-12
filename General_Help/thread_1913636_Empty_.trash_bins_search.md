---
title: "Empty .trash bins search"
date: 2012-01-22
forum: General Help
---

### Post by diskmaster23 on 2012-01-22
I've been searching for a script or a command that searches a file system for all the files in .trash files and deletes them. I am not exactly the most 'creative' type when it comes to the command line. Any help would be greatly appreciated.

---

### Post by SuaSwe on 2012-01-22
Hello there!

This should be nice and simple, provided you know where the trash folders in question are? You can find out like this (the below assumes you're looking for trash cans of all users and the system):

```

sudo find / -type d -name *[tT]rash*

```

Let's say for argument's sake you found the following (plus some other directories that you should omit):

/home/user1/.local/share/Trash
/home/user2/.local/share/Trash
/home/root/.local/share/Trash

You could then write a script a bit like:

```

#!/bin/bash
# let's say script is called /home/user1/rubbish.sh
# script to remove files in all trash folders

rm -rf /home/user1/.local/share/Trash/*
rm -rf /home/user2/.local/share/Trash/*
rm -rf /home/root/.local/share/Trash/*

exit

```

Then do the following to be able to use it:

```

chmod +x rubbish.sh     # to make executable
sudo ./rubbish.sh       # to run

```

That's about as simplistic as you can get! Is it this sort of thing you have in mind, or something more advanced (and prettier-looking :D)? You can also install apps that will clean out trash dirs, as per [[color=blue]this site[/color]]("http://maketecheasier.com/4-more-ways-to-clean-up-your-ubuntu-machine/2010/08/06"), for example. :)

You could also write a one-liner but I wouldn't do that if you're also looking to remove stuff in root directories (too risky!). Something like this would remove everything in your home directory contained within all directories called 'Trash': 

```

for i in `find ~ -type d -name Trash`; do rm -rf $i/*; done;

```

Just beware that there's no checks, control or nuances with this, it will simply find every directory called Trash and remove whatever's in it. :)

---

### Post by diskmaster23 on 2012-01-29
That was incredibly helpful. Thank you so much for posting that comprehensive way of emptying one's trash bins.

---

