---
title: "Hide GRUB2 Menu?"
date: 2009-10-27
forum: General Help
---

### Post by zzzBrett on 2009-10-27
In GRUB legacy, there was an option to 'hide' the menu (require to press ESC to access menu at boot).

Is there an option for this with GRUB2?

---

### Post by dcstar on 2009-10-27
> **zzzBrett said:**
> In GRUB legacy, there was an option to 'hide' the menu (require to press ESC to access menu at boot).

Is there an option for this with GRUB2?

/etc/default/grub

---

### Post by nightalon on 2009-10-29
Well, I figured out that that was a config file, but your response was very terse.

There seem to only be timeouts for the hidden menu.  Do you know how this works?  I guess I'll run a clean install on another machine with Grub2 and see how it all gets set up with default settings.

I install grub to partition, not to MBR, by the way.  I use EasyBCD and the Windows 7 bootloader to chainload everything, since Windows is still my production OS, and I can't have that fail.

---

### Post by philinux on 2009-10-29
Hope this helps. This is gonna take some getting used to.

[https://help.ubuntu.com/community/Grub2#Boot%20Display%20Behavior](https://help.ubuntu.com/community/Grub2#Boot%20Display%20Behavior)

Another good link from drs305.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub)

---

### Post by tom4everitt on 2010-05-02
This citation is from the first link:

> 
Note to multiple-OS users: If GRUB 2's os-prober  identifies additional operating systems while running the /etc/grub.d/30_os-prober  script the hidden menu timeout feature is disabled by conditional statements. This also disables the ability to use the SHIFT  key to display the menu during boot. Users with multiple operating systems wishing to hide the menu can find script edits on various forums which will allow them to add a hidden timeout feature to the boot sequence. 


took me a while to find it. Wish there was an easy way to hide the menu even if having several os's. But then again, I guess one could just turn off the os-prober in the first place, in case one is not interested in booting the other os's.

---

### Post by Redsandro on 2011-03-14
Since it takes a while to find it and you already found it, can you provide us with such a script edit example to hide the GRUB menu even with multiple OSses present?

---

### Post by wilee-nilee on 2011-03-14
> **Redsandro said:**
> Since it takes a while to find it and you already found it, can you provide us with such a script edit example to hide the GRUB menu even with multiple OSses present?

> **Users with multiple operating systems wishing to hide the menu can find script edits on various forums** which will allow them to add a hidden timeout feature to the boot sequence. 

You might have to go looking if you really want this. I have never seen one on this forum, doesn't mean there aren't any but it is a unusual request 
while dual or multi-booting.

This is also a really old thread you might start one and get help you never know.:)

---

### Post by Redsandro on 2011-03-15
Meanwhile, found this:

According to [SIZE="3"][Grub2 @ help.ubuntu.com]("https://help.ubuntu.com/community/Grub2")[/SIZE] the solution is in [SIZE="3"][Grub 2 Tweaks @ ubuntuforums]("http://ubuntuforums.org/showthread.php?t=1287602")[/SIZE].

Someone mentioned how it it done in 10.10:

[SIZE="3"]**Ubuntu 10.10 Grub 2 hide multi-OS menu guide:**[/SIZE] [COLOR="DarkRed"](untested)[/COLOR]

> **drs305 said:**
> [...]

If the "GRUB_TIMEOUT=0" does not work, [...] open /etc/grub.d/00_header and go to approximately line 238: 
```
gksu gedit +238 /etc/grub.d/00_header
```

Find this section and make the changes in **[COLOR="DarkRed"]dark red[/COLOR]**, then save the file and run "sudo update-grub".

> make_timeout ()
{
cat << EOF
if [ "\${recordfail}" = 1 ]; then
set timeout=-1
else
[B][COLOR="DarkRed"]
# Manually change timeout to 0
# set timeout=${2} 
set timeout=0
# End manual change
[/COLOR][/B]
fi
EOF
}

This should eliminate the menu display [...]. It also preserves the ability to display the menu by holding down the SHIFT key during boot.
[...]

-update-

Found out how to do it in 10.04.

[SIZE="3"]**Ubuntu 10.04 LTS Grub 2 hide multi-OS menu guide:**[/SIZE]

run *gksudo gedit /etc/grub.d/00_header*

near-bottom (line 154), find:
```
  set timeout=${GRUB_TIMEOUT}
```

replace with:
```
#  set timeout=${GRUB_TIMEOUT}
#RED 2011-03-15 force hidden menu
  set timeout=0
```

run *sudo update-grub*

:D

[SIZE="1"][COLOR="DimGray"]*Um, I don't get the Grub2 thing. This is clearly not the sweet old grub from the old days, but it sais 1.96, which is not 2 either. Anyway, this is about the standard Grub that comes with Ubuntu.*[/COLOR][/SIZE]

---

