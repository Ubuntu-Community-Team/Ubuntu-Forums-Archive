---
title: "Nautilus action to find files"
date: 2010-08-27
forum: General Help
---

### Post by holocene on 2010-08-27
When I am in Nautilus, I want to be able to select a directory, then right click (or some other action) to do a file find on that directory. The gnome-search-tool would be a good candidate for this, if it could be an action in Nautilus.

I know I can do a file find through other means, but Nautilus seems to be where I am when I want to search directories.

Anyone know how to do this, or where to look to see how to do it?

Regards
Steve.

---

### Post by _0R10N on 2010-08-27
Take a look here [http://techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/](http://techthrob.com/2009/03/02/howto-add-items-to-the-right-click-menu-in-nautilus/) I am in Linux Mint with Xfce right now, and I'm not able to try what the links says.

By the way, Thunar (Xfce's Nautilus) already got the search utility associated in its right click menu. lol

---

### Post by holocene on 2010-08-27
I messed around with putting the gnome-search tool into the Nautilus Actions Configuration tool, trying all the different parameters, but failed to find one that would work.

So, the newbie that I am, I created a file like this:

```
me@mybox:~$ cat gst.sh 
#!/bin/bash
gnome-search-tool --path=$1
```I used gnome-search-tool --help to find the command line option for --path=

In the Nautilus Actions Configuration Command tab:
under command: /home/me/gst.sh
under parameters: %f

Now, I can right click any directory, anywhere, and I have a context menu selection for the gnome-search-tool that will launch with the pointed-to directory loaded in the "look in" folder. 

I have noticed that sometimes, for folders on the desktop, the 'look in' folder will show your home folder instead. But still, a huge improvement!

Seems like any script you can write, you can use nautilus to feed it a parameter according to the "legend" and get pretty general functionality. 

Any help or hints appreciated. 
Steve.

---

### Post by Vaphell on 2010-08-27
probably your script thinks that there is something wrong with the path. i checked and gnome-search defaults to home when directory does not exist, also it doesn't like ~ alias for current user's home and does the same.

maybe it's about spaces and those dirs at desktop have one? replace $1 with "$1" and see what happens

---

### Post by holocene on 2010-08-27
> **Vaphell said:**
> probably your script thinks that there is something wrong with the path. i checked and gnome-search defaults to home when directory does not exist, also it doesn't like ~ alias for current user's home and does the same.

maybe it's about spaces and those dirs at desktop have one? replace $1 with "$1" and see what happens

Ok. I added the "$1" as you indicated, and did not see any difference in the way it works.

If I invoke the script like this:

$./gst.sh /home/me/Desktop/somedir 

it works.

If I do the same from Nautilus as an action, it comes up with /home/me

any other ideas? Anyone?

Thanks 
Steve.

---

### Post by Vaphell on 2010-08-27
i debugged it with
```
#!/bin/sh

gnome-terminal -e "sh -c 'echo $1;read a'"
gnome-search-tool --path="$1"
```
first line spawned the terminal window to print the parameter

%f sucks - it is the name alone, not a full path
go with %M

---

### Post by holocene on 2010-08-28
> **Vaphell said:**
> i debugged it with
```
#!/bin/sh

gnome-terminal -e "sh -c 'echo $1;read a'"
gnome-search-tool --path="$1"
```first line spawned the terminal window to print the parameter

%f sucks - it is the name alone,

 not a full path
go with %M

Vaphell, works perfectly as far as I can tell.

Thanks.
Steve.

ps I've been to L'viv and Stryii. Do you know where they are?

---

