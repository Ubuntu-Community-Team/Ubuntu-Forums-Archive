---
title: "Gconf, nautilus and me"
date: 2009-07-12
forum: General Help
---

### Post by dumblebee100 on 2009-07-12
Well I have some problem with Gconf and nautilus lately .
recently I created a script which is like this 
```
#!/bin/bash
current_setting=`gconftool-2 --get /apps/nautilus/preferences/always_use_location_entry`
if [ $current_setting = "true" ]; then
gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry false
fi
if [ $current_setting = "false" ]; then
gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry true
fi
```

I used this script to toggle the nautilus address bar to text input and button style ... and I gave it a keyboard shortcut ALT+D( well Im kinda habituated to that keyboard shortcut ..dont feel that I'm a windows fan) 

well that worked very good ..and I played some time pressing that key combination and highlighting address bar with CTRL+L and copying the address bar contents then pressing again ALT+D ...

but after shutdown and next day the nautilus wont start .so I started gconf-editor and found out a error like key not writable..

I tried sudo gconf-editor ..and even deleted the gconf-saved state in my home dir .....if you insist me to reinstall gconf then my app-get is telling me that I have to download more 428mb just to uninstall and Im not ready for it even for my 1mbps connection ....I just don't want correcting a simple script to download that much 

at first I made a mistake in script ..I gave string instead of boolean .and even if I changed the script to boolean the string true is not getting unset in gconf after pressing ALT+D
if gconfd2 is running in my processes then it don't let my nautilus to run ...so I have to kill it and unset the key but it is again reverting back to false 
so next time I killed gconfd2 and set it as mandatory false ..that would let my nautilus run ..so I stuck here 

that is one problem ..next is ...can you please correct the script ..it would be lot helpful 

right now I killed the gconfd2 and set the value to mandatory false .so I could run my nautilus ..now the pencil button don't work for me anymore ....now all I left with is button style address bar 

can you please help me ..without me messing my installation

---

### Post by CatKiller on 2009-07-12
GConf settings are just XML files in ~/.gconf. Since your gconfd is conflicted, it might be possible to amend these files to what they should be directly, and then sort out the mandatory stuff so that you can have both gconfd and nautilus running at the same time again.

---

### Post by dumblebee100 on 2009-07-12
that would be first reply to all my threads and Im happy to see that some one is helping me 

well I did find the .gconf directory and searched for nautilus folder and inner gconf xml files ...but all it has is the details which we setup in nautilus preferences and not the "always_show_location_bar" entry ...

well in other words I have to say that didnt worked for me ...

can you guys tell me how can I restore the gconf settings to factory settings

---

### Post by CatKiller on 2009-07-12
> **dumblebee100 said:**
> ...but all it has is the details which we setup in nautilus preferences and not the "always_show_location_bar" entry ...

Potentially that's why that setting is broken, then, don't you think?

FWIW, this is what the last line of my ~/.gconf/apps/nautilus/preferences/%gconf.xml file says.

```

    <entry name="always_use_location_entry" mtime="1240022676" type="bool" value="true"/>

```

> 
can you guys tell me how can I restore the gconf settings to factory settings

Delete the ~/.gconf and ~/.gconfd directories. You might need to log out and log back in for it to take effect. Actually, it might be sensible to log out, switch to a virtual console (Ctrl-Alt-F1) to delete the files, and then switch back (Alt-F7) and log in, just so that gconfd definitely isn't running when you delete its directory.

---

### Post by dumblebee100 on 2009-07-13
Yeah I did in the same way as you said ..

I appended the entry to the last of %gconf.xml in $home/.gconf/apps/nautilus/preferences/%gconf.xml

but after restart or atleast logout ..the problem still existed ..then I checked the gconf.xml ...but the last entry was automatically deleted ...

then next step I deleted the .gconf and .gconfd directories ..then after logout ..I came up with factory settings ..I mean ...desktop as of ubuntu first look ,...so It took lot of time reconfiguring all the settings ..and now Im replying ..

I think I messed up my gconf and only a clean install will rectify it ...but I will wait till karmic for clean install ...I kinda of installed karmic alpha 2 but after kernel update it crashed so did a clean install of januty and now I dont dare to install alpha releases ..so waiting for final release

---

### Post by CatKiller on 2009-07-13
> **dumblebee100 said:**
>  I think I messed up my gconf and only a clean install will rectify it ...

Not really. It's all working now that you've reset your GConf settings to their defaults, isn't it? Just don't use a string when you mean a boolean value, and you'll be fine.

---

### Post by kaibob on 2009-07-13
> **dumblebee100 said:**
> ...that is one problem ..next is ...can you please correct the script ..it would be lot helpful...

I don't think you script is going to work as presently written. After getting the current setting, it changes that setting to false if currently true, and then immediately changes it back to true. I think you need something like:

```
#!/bin/bash

current=$(gconftool-2 --get /apps/nautilus/preferences/always_use_location_entry)

if [ "$current" = true ] ; then
   gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_location_entry false
else
   gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_location_entry true
fi
```

I tried this on my computer; it worked fine.

---

### Post by dumblebee100 on 2009-07-14
> **kaibob said:**
> I don't think you script is going to work as presently written. After getting the current setting, it changes that setting to false if currently true, and then immediately changes it back to true. I think you need something like:

```
#!/bin/bash

current=$(gconftool-2 --get /apps/nautilus/preferences/always_use_location_entry)

if [ "$current" = true ] ; then
   gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_location_entry false
else
   gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_location_entry true
fi
```

I tried this on my computer; it worked fine.


I dont know if it works or not but before that I get error while setting gconf values manually from gconf-editor 

the error is 
Could not change key value. Error message:
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/apps/nautilus/preferences/always_use_location_entry' set in a read-only source at the front of your configuration path

I googled and could not find one promising solution..

---

