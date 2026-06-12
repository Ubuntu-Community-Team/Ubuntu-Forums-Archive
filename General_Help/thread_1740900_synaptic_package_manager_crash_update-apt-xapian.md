---
title: "synaptic package manager crash update-apt-xapian"
date: 2011-04-27
forum: General Help
---

### Post by harrismh777 on 2011-04-27
Greetings,
   I upgraded an older system from jaunty 9.04 to karmic 9.10/

   Following the upgrade, and about six hours of stable use, I ran the synaptic package manager, to pull in fvwm-crystal and a couple of other nits. Synaptic went into its usual tiring Rebuild Index while the resource hog update-apt-xapian ran away gleefully with the cpu pegged... for longer than I've ever seen it... about 15 minutes, and then the system crashed. 

   ... and, I mean it crashed hard. I have not seen linux do this in years. Not just a seg fault, the whole machine just crashed (cpu, display, keyboard, the works).

    Restart and no problem, until I ran Synaptic (Rebuild Index... several minutes, crash).

    I played this game for a while;  thinking the system might just 
might be overheating... let it cool down, and retried... same result.

    I tried running one last time, and this time pressed the reload (on Synaptic main panel) prior to the crash... it pulled in the repository updates and completed the Rebuild Index. (no crash)

    I have run Synaptic several times since that... downloaded some goodies, and have had no further crashes (although, it does run Rebuild Index every time I start it... and update-apt-xapian pegs the cpu while this is going on.

    The question(s) I have are:

1) I was not aware that an apt these days can bring down the kernel (no panic, no logging, just down....)   How is update-apt-xapian tied into the kernel that permits this vulnerability?

2) There appears (from searches) to be a problem with Synaptic or at least with xapian...??  What is going on with this resource pig..?

3) If I disable xapian and use sudo apt-get instead, instead of Synaptic, does this solve this resource problem?

4) Is there another forum area where this might be addressed besides general?

Thanks in advance folks...   :confused:

---

### Post by KegHead on 2011-04-27
Hi!

I've always used the following w/no problems;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

KegHead

---

### Post by harrismh777 on 2011-04-27
Thanks for the reply on apt-get.... that is good to know. 

I have an update for everyone...  I found another search that recommended this as a fix, which worked for some,   :

    sudo apt-get purge apt-xapian-index
    sudo apt-get intall apt-xapian-index


I tried this--- the purge went fine... the install went fine... and then xapian went into an index build and the system crashed hard (requires only hard reboot... everything is dead).

I have purged xapian from my system.

This is a problem, me thinks, because several packages use the quick searching provided by xapian... including Synaptic PM. I find that although the quick search is gone from Synaptic, the button search still works, and Synaptic is still usable.

Anyone know what is going on here?


Thanks

8-[

---

### Post by harrismh777 on 2011-04-27
Ok, I think I've come to the bottom of this... the resource problem with apt-xapian-index is well known and has a fix... which I post further down...

... on a system with limited resources (like my 640M memory) will crash if the xapian index must be rebuilt from scratch. This is what I did to get past this snag on my old system....

    reboot but do not logon to greeter; instead open terminal with 
    ctl-alt-F2
    logon

    sudo apt-get install apt-xapian-index

    When the index rebuild begins in the background after the install, kill the process (I used top to find the process number, then killed it with):

    kill -9  <the process number>

    then run this script:

============= begins here ======================
#!/bin/sh

CMD=/usr/sbin/update-apt-xapian-index
IONICE=/usr/bin/ionice

# Rebuild the index
if [ -x $CMD ]
then
	if [ -x $IONICE ]
	then
		nice -n 19 $IONICE -c 3 $CMD --update --quiet
	else
		nice -n 19 $CMD --update --quiet
	fi
fi
=========================== ends here ===================

    The index rebuild completed without crashing... yippie !

    I replaced the  script  /etc/cron.weekly/apt-xapian-index 

    with the code above.


    The code above will rebuild the index with nice set to 19, which means that the indexing process that fires up each week will not claim the cpu to the exclusion of all else...  the options are set so that the index will be updated instead of completely rebuilt... doh.

    This is a miserable work-around (not a fix) but a work-around none-the-less...   

    kind regards,

    m harris

---

### Post by harrismh777 on 2011-04-27
> **Eiríkr said:**
> [size=+1]Hallelujah, a Fix![/size]

For anyone else bitten by this bug, [the Launchpad discussion](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/363695) makes it clear that a fix exists and will be incorporated into Ubuntu at some point.  For those impatient to get the fix working now, [this post](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/363695/comments/43) from the Launchpad thread includes the following:

```
#!/bin/sh

CMD=/usr/sbin/update-apt-xapian-index
IONICE=/usr/bin/ionice

# Rebuild the index
if [ -x $CMD ]
then
	if [ -x $IONICE ]
	then
		nice -n 19 $IONICE -c 3 $CMD --update --quiet
	else
		nice -n 19 $CMD --update --quiet
	fi
fi
```
Fire up your favorite text editor with [font=courier]sudo[/font], open the [font=courier]/etc/cron.weekly/apt-xapian-index[/font] file, and edit the contents to match the above.

[size=+1]What This Does[/size]

[font=courier]update-apt-xapian-index[/font] helps maintain an index of packages, and this helps speed up searching for packages in Synaptic, and possibly in other package managers as well.  

[font=courier]cron[/font] is a utility for scheduling tasks to run at certain times.  System tasks run weekly are, unsurprisingly, stored in the [font=courier]/etc/cron.weekly[/font] directory.  You can also set up personal tasks to run pretty much whenever you want.  For that, have a look at [font=courier]man crontab[/font].

Looking at the internals of the code we're using here, the first line, the "crunchbang" line (#!), tells the system what executable to use to run the contents -- in this case, [font=courier]/bin/sh[/font], or your basic **_sh_**ell.  

The next two lines establish two shorthand variables.  Variables in shell scripts are generally defined in ALL CAPS for easy readability.  This is more of a best practice than any hard-and-fast requirement.  When referenced later in the script, the variable names are prefixed with a $.  Here, [font=courier]CMD[/font] is simply shorthand for the path to the [font=courier]update-apt-xapian-index[/font] binary, and [font=courier]IONICE[/font] is shorthand for the path to the [font=courier]ionice[/font] utility for getting or setting a process's I/O scheduling class and priority.

In the [font=courier]if[/font] statements, the [font=courier]-x[/font] checks to see if the next argument exists, so [font=courier]if [ -x $CMD ][/font] will check to see if [font=courier]/usr/sbin/update-apt-xapian-index[/font] exists in the filesystem.  

[font=courier]nice -n[/font] is basically how you assign a priority to a process.  **An important caveat**, however, is that [font=courier]nice[/font] is just that -- a high [font=courier]nice[/font] value (up to a maximum of [font=courier]-n 19[/font]) means the process is nice and gets out of the way, and a low [font=courier]nice[/font] value (down to a minimum of [font=courier]-n -20[/font]) means the process is *not* nice and barges to the front of the line to be the first to use system resources.  Niceness defaults to 10 if not otherwise specified, and apparently the default [font=courier]update-apt-xapian-index[/font] setup does not specify any value.  

[font=courier]ionice[/font] is new in this fix.  It works along similar lines, affecting a process's input/output niceness, only using the flag [font=courier]-c[/font] for "class".  The [font=courier]ionice[/font] man page describes [font=courier]-c[/font]:


Finally, we have the two options passed to [font=courier]update-apt-xapian-index[/font] itself, [font=courier]--update[/font] and [font=courier]--quiet[/font].  [font=courier]--quiet[/font] just tells it to not generate much text, only outputting for fatal errors, which makes sense for a background process.  [font=courier]--update[/font] is **new** here in this fix together with the [font=courier]nice[/font] value and the [font=courier]ionice[/font] prioritization, and is a real kicker: it tells [font=courier]update-apt-xapian-index[/font] to *only update those items in the index that have actually changed*.  This seems like a no-brainer, since the index includes *every* package installed in the system, but unfortunately the default [font=courier]update-apt-xapian-index[/font] setup in a fresh install of Jaunty, Karmic, or Lucid all leave this option out, meaning that [font=courier]update-apt-xapian-index[/font] will rebuild the ENTIRE package index every time it runs.  No wonder it eats up so much memory and CPU time!  With [font=courier]--update[/font], it should take much less resources and much less time.

----------

Hope this helps, folks!

Cheers,

-- Eiríkr

:popcorn:

---

