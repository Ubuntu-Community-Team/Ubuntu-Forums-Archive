---
title: "Setup Script"
date: 2012-02-17
forum: General Help
---

### Post by OldManRiver on 2012-02-17
All,

I'm wondering if there is an operations "set-up" script that can be run on boot to configure the desktop to your exact working environment?

Example:
I have 6 workspaces declared on my Desktop. Each has a functional designation.  They are:
[LIST=1]
[*]Personal & Spriitual,
[*]Projects,
[*]Blogs,
[*]Personal Passion Projects,
[*]Work, Operations, Invoicing,
[*]Marketing.
[/LIST]
I have apps that need to open for each workspace and FireFox must open, with specific pages, some on localhost, for work in each.

How would one go about writing a script to auto open all these in the right workspace?

Thanks!

OMR

---

### Post by OldManRiver on 2012-02-29
All

Can I get some help here?

OMR

---

### Post by collisionystm on 2012-02-29
look at this

[http://ubuntuforums.org/showthread.php?t=1128091](http://ubuntuforums.org/showthread.php?t=1128091)

---

### Post by Lars Noodén on 2012-02-29
> **collisionystm said:**
> look at this

[http://ubuntuforums.org/showthread.php?t=1128091](http://ubuntuforums.org/showthread.php?t=1128091)

Interesting but [font=Courier New]firefox --workspace 0 1[/font] seems to have no effect in Unity.  Can you suggest a solution or work-around? [font=Courier New]launch-in-workspace[/url] doesn't seem to exist even in the package database.

---

### Post by collisionystm on 2012-02-29
> **Lars Noodén said:**
> Interesting but [font=Courier New]firefox --workspace 0 1[/font] seems to have no effect in Unity.  Can you suggest a solution or work-around? [font=Courier New]launch-in-workspace[/url] doesn't seem to exist even in the package database.

[http://www.foosel.org/linux/devilspie](http://www.foosel.org/linux/devilspie)

[http://ubuntuforums.org/showthread.php?t=1847298](http://ubuntuforums.org/showthread.php?t=1847298)

---

### Post by OldManRiver on 2012-04-02
All,

Found the following command easily does the multi tab thing:
```

firefox -url https://localhost:10000 -url http://www.google.com

```
Now experimenting with FF sessions

Will also test the:

firefox --workspace

and see what I get.

I tried the -new-window option from the KB at:

[http://kb.mozillazine.org/Command_line_arguments](http://kb.mozillazine.org/Command_line_arguments)

and only opens new tab in current session, not a new session.  The --workspace option does not work at all, as workspace is not a firefox option but a linux option, so trying to figure out how to call it right.

Cheers!

OMR

---

### Post by OldManRiver on 2012-04-02
All,

None of the info at:

[http://ubuntuforums.org/showthread.php?t=1128091](http://ubuntuforums.org/showthread.php?t=1128091)

is valid or works!

Cheers!

OMR

---

### Post by Habitual on 2012-04-02
> **OldManRiver said:**
> ...How would one go about writing a script to auto open all these in the right workspace?...

OMR: Although not a 'script' proper, it will/should do the job... **devilspie** in a repo near you.

Coding the ~/.devilspie/*.ds files can be irritating at first, but once it works, it's a gem.

HTH

---

### Post by Habitual on 2012-04-02
> **OldManRiver said:**
> All,

I'm wondering if there is an operations "set-up" script that can be run on boot to configure the desktop to your exact working environment?

I am not addressing that issue here.

I am addressing a possible solution here...
> **OldManRiver said:**
> 
Example:
...
I have apps that need to open for each workspace and FireFox must open, with specific pages, some on localhost, for work in each.

You will need to write a shell script for each program that you want to open in a given workspace, IGNORING the workspace placement, for the moment.  OR...
write  a single shell script that calls the other scripts files. Edit: Do you know how to open multiple Firefox Browsers with tabs for each site?
Once the scripts are written and run as expected from command-line, THEN you would have to tweak this snippet to suit each program that is running and save it as ./devilspie/[*0-5][A-Za-z*].ds / whatever.ds...

Here's my 'edt.ds" file (Embedded Desktop Terminal) devilspie script.
```

~/.devilspie/edt.ds
; generated_rule trans
( if
( and
;( matches ( window_name ) "trans" )
)
( begin
( undecorate )
;( skip_pager )
;( skip_tasklist )
;( wintype "normal" )
;( wintype "dialog" )
;( wintype "menu" )
;( wintype "toolbar" )
;( wintype "splashscreen" )
;( wintype "utility" )
( wintype "dock" )
;( wintype "desktop" )
( set_workspace 1 )
( center )
;( geometry "834x818+150+100" )
;( geometry "896x800+180+68" )
;( geometry "900x860+180+68" )
( geometry "192+74+187+50" )
; width + height + x + y
( below )
)
)
```Once you have a working .ds file (we hope) then you can 'test' it with terminal > "devilsipie -a"
Work on one ds file at a time is my suggestion.

This topic seems eerily similar to a recent LM forum post...

[Devilspie Documenation]("http://www.foosel.org/linux/devilspie")
Good Luck!

HTH?!

---

### Post by Habitual on 2012-04-02
> **OldManRiver said:**
> All,

I'm wondering if there is an operations "set-up" script that can be run on boot to configure the desktop to your exact working environment?

I am not addressing that issue here.

I am addressing a possible solution here...
> **OldManRiver said:**
> 
Example:
...
I have apps that need to open for each workspace and FireFox must open, with specific pages, some on localhost, for work in each.

You will need to write a shell script for each program that you want to open in a given workspace, IGNORING the workspace placement, for the moment.  OR...
write  a single shell script that calls the other scripts files.
Once the scripts are written and run as expected from command-line, THEN you would have to tweak this snippet to suit each program that is running and save it as ./devilspie/[*0-5][A-Za-z*].ds / whatever.ds...

Here's my 'edt.ds" file (Embedded Desktop Terminal) devilspie script.
```

~/.devilspie/edt.ds
; generated_rule trans
( if
( and
;( matches ( window_name ) "trans" )
)
( begin
( undecorate )
;( skip_pager )
;( skip_tasklist )
;( wintype "normal" )
;( wintype "dialog" )
;( wintype "menu" )
;( wintype "toolbar" )
;( wintype "splashscreen" )
;( wintype "utility" )
( wintype "dock" )
;( wintype "desktop" )
( set_workspace 1 )
( center )
;( geometry "834x818+150+100" )
;( geometry "896x800+180+68" )
;( geometry "900x860+180+68" )
( geometry "192+74+187+50" )
; width + height + x + y
( below )
)
)
```Once you have a working .ds file (we hope) then you can 'test' it with terminal > "devilsipie -a" and fire off one of the script(s).sh
Work on one ds file at a time is my suggestion.

This topic seems eerily similar to a recent LM forum post...

[Devilspie Documenation]("http://www.foosel.org/linux/devilspie")
Good Luck!

HTH?!

Edit2: I wrote this like 3 years ago and it still works today, (with minor tweaking) on every platform I've installed. :P

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #13 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

