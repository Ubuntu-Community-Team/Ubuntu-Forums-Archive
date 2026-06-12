---
title: "way to make Shred command display confirmation before shredding?"
date: 2011-02-05
forum: General Help
---

### Post by nrundy on 2011-02-05
I use nautilus-action to create a right-click shred command with these parameters.: 
-f -u -v -z %M

I thought the -v would give me some feedback as well as an "are you sure" dialog before deleting. But when I run Shred it just deletes the file without any feedback and no confirmation beforehand.

How can I get a confirmation prompt to occur before shredding occurs (to prevent me from accidentaly shredding something--sometimes I click the wrong item cause the mouse shifts last second).

Any why don't any icons ever appear on my context menu even though I'm assigning icons?

---

### Post by ajgreeny on 2011-02-05
The -v does not give any "are you sure?" dialog, but it should show the verbose output of what is happening.  There does not appear to be an equivalent of the -i option available for the rm command, as far as I can see.  I wonder if the lack of output is because you are doing it from nautilus-actions, rather than direct in terminal; having never used nautilus-actions, I can not comment on that.

Does shred work normally if you use terminal?  Here's the output from a test I just made:-
```
user@ubuntu1004:~/Backup/xorg$ shred -vuzn 10 testshred 
shred: testshred: pass 1/11 (random)...
shred: testshred: pass 2/11 (492492)...
shred: testshred: pass 3/11 (000000)...
shred: testshred: pass 4/11 (ffffff)...
shred: testshred: pass 5/11 (555555)...
shred: testshred: pass 6/11 (random)...
shred: testshred: pass 7/11 (924924)...
shred: testshred: pass 8/11 (dddddd)...
shred: testshred: pass 9/11 (aaaaaa)...
shred: testshred: pass 10/11 (random)...
shred: testshred: pass 11/11 (000000)...
shred: testshred: removing
shred: testshred: renamed to 000000000
shred: 000000000: renamed to 00000000
shred: 00000000: renamed to 0000000
shred: 0000000: renamed to 000000
shred: 000000: renamed to 00000
shred: 00000: renamed to 0000
shred: 0000: renamed to 000
shred: 000: renamed to 00
shred: 00: renamed to 0
shred: testshred: removed

```but as you see there is no interactive failsafe "are you sure?", and a test adding the -i option just shows an error for invalid option.

---

### Post by t0p on 2011-02-05
Is **srm** in the repos?  If not, you can get it from sourceforge.

srm is a "secure deletion" tool.  If you use the **- i** tag, it goes into "interactive mode" and will "prompt before any removal".  I guess that's what you want, yeah?

---

### Post by Spyderkid on 2011-02-05
You could try this:

```
shred --verbose -v FILENAME
```

---

### Post by nrundy on 2011-02-05
> **t0p said:**
> Is **srm** in the repos?  If not, you can get it from sourceforge.

srm is a "secure deletion" tool.  If you use the **- i** tag, it goes into "interactive mode" and will "prompt before any removal".  I guess that's what you want, yeah?

Yeah, I'm looking for an interactive mode like you describe. With normal delete it goes to Trash. With Shred it's GONE.  An accidental click can be costly.

---

### Post by nrundy on 2011-02-05
> **ajgreeny said:**
> 
Does shred work normally if you use terminal?  Here's the output from a test I just made:-
```
user@ubuntu1004:~/Backup/xorg$ shred -vuzn 10 testshred 
shred: testshred: pass 1/11 (random)...
shred: testshred: pass 2/11 (492492)...
shred: testshred: pass 3/11 (000000)...
shred: testshred: pass 4/11 (ffffff)...
shred: testshred: pass 5/11 (555555)...
shred: testshred: pass 6/11 (random)...
shred: testshred: pass 7/11 (924924)...
shred: testshred: pass 8/11 (dddddd)...
shred: testshred: pass 9/11 (aaaaaa)...
shred: testshred: pass 10/11 (random)...
shred: testshred: pass 11/11 (000000)...
shred: testshred: removing
shred: testshred: renamed to 000000000
shred: 000000000: renamed to 00000000
shred: 00000000: renamed to 0000000
shred: 0000000: renamed to 000000
shred: 000000: renamed to 00000
shred: 00000: renamed to 0000
shred: 0000: renamed to 000
shred: 000: renamed to 00
shred: 00: renamed to 0
shred: testshred: removed

```but as you see there is no interactive failsafe "are you sure?", and a test adding the -i option just shows an error for invalid option.

Yeah, using terminal gives me feedback (verbose). Must be something to do with nautilus-action.

---

### Post by nrundy on 2011-02-05
guys, what about the missing Icons? Do you guys get icons when right-clicking? I got none. I also noticed I got no icons in my NoScript add-on for Firefox either--when I right-click the icon in the Fx toolbar. But I have icons along the left side of the context menu in MS Windows.

---

### Post by ajgreeny on 2011-02-05
Yes I get icons against some of my context menu items, but not all, see screenshot.  Have you set the system to show menu icons in gconf-editor?

If not open up Configuration Editor -> desktop -> gnome -> interface and put tick in
1) menus_have_icons
2) buttons have icons

That may do it for you.

---

### Post by nrundy on 2011-02-05
> **ajgreeny said:**
> Yes I get icons against some of my context menu items, but not all, see screenshot.  Have you set the system to show menu icons in gconf-editor?

If not open up Configuration Editor -> desktop -> gnome -> interface and put tick in
1) menus_have_icons
2) buttons have icons

That may do it for you.

This got it. Thank you ajgreeny! :) Now I have icons!

I'm surprised this setting isn't ticked by default.

---

### Post by ajgreeny on 2011-02-06
> **nrundy said:**
> This got it. Thank you ajgreeny! :) Now I have icons!

I'm surprised this setting isn't ticked by default.
So am I, but on slower, older machines the icons can slow down the menu rendering, apparently.

---

### Post by nrundy on 2011-02-12
In the future, if anyone learns how to make Shred give a Confirmation Dialog I'd really appreciate it if you posted it in this thread. Thanks

---

### Post by warsev on 2011-02-25
Try this. Put this script in your /home/user/bin folder. Set it up with Nautilus Actions to point to the script and give you a right-click context menu with Shred as the name and %M as the parameter. It's a nice little script &#8211; confirmation dialog, handles multiple file names, with spaces in the file names, catches errors, and displays a progress bar.

```
#!/usr/bin/env bash
nfiles="$#"
files=""
for file in "$@" ; do 
  if [ ${#files} -gt 0 ] ; then files="$files\n"; fi
  files=$files$(basename "$file")
done
zenity --question --title="shred these $nfiles files - REALLY??" --text="$files"
if [ "$?" = 1 ] ; then
  exit $?
else
  nfile=0
 (for file in "$@" ; do
    echo \# shredding $(basename "$file")...
    shredout=$(shred -u -z -n 1 "$file" 2>&1)
    rc=$?
    if [ $rc -ne 0 ] ; then
      echo "100"
      zenity --error --title="No break for you today" --text="$shredout"
      exit $rc
    else
      let nfile++
      echo $((nfile * 100 / nfiles))
    fi
  done ) | zenity --progress --title="Wiping files..." --auto-close \
          --percentage=0 --text="starting..." --no-cancel
fi
exit 0
```

---

### Post by nrundy on 2011-02-25
hey, thanks so much for this warsev :)

I'll try it soon as I have some time. Real busy with a project at work at the moment so don't have time at the moment.

---

### Post by zero244 on 2011-08-13
> **warsev said:**
> Try this. Put this script in your /home/user/bin folder. Set it up with Nautilus Actions to point to the script and give you a right-click context menu with Shred as the name and %M as the parameter. It's a nice little script – confirmation dialog, handles multiple file names, with spaces in the file names, catches errors, and displays a progress bar.

```
#!/usr/bin/env bash
nfiles="$#"
files=""
for file in "$@" ; do 
  if [ ${#files} -gt 0 ] ; then files="$files\n"; fi
  files=$files$(basename "$file")
done
zenity --question --title="shred these $nfiles files - REALLY??" --text="$files"
if [ "$?" = 1 ] ; then
  exit $?
else
  nfile=0
 (for file in "$@" ; do
    echo \# shredding $(basename "$file")...
    shredout=$(shred -u -z -n 1 "$file" 2>&1)
    rc=$?
    if [ $rc -ne 0 ] ; then
      echo "100"
      zenity --error --title="No break for you today" --text="$shredout"
      exit $rc
    else
      let nfile++
      echo $((nfile * 100 / nfiles))
    fi
  done ) | zenity --progress --title="Wiping files..." --auto-close \
          --percentage=0 --text="starting..." --no-cancel
fi
exit 0
```

Thanks for the script....its working fine and does give you an out if you selected shred by mistake.
Which you could do very easily without a confirmation box.

---

