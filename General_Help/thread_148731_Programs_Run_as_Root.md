---
title: "Programs Run as Root"
date: 2006-03-22
forum: General Help
---

### Post by Geffers on 2006-03-22
I understand that some of the 'system' programs need to be run as root and to do so the program needs to be entered into the run dialog and run as a different user.

When I do this often extra data appears after the program name, sometimes I find that I need to delete this Extra data to get the program to appear on the desktop as if I leave it as it is I get disk activity then nothing.

Should I be doing something else..

Geffers

---

### Post by aysiu on 2006-03-22
Can you give an example of what this "extra data" after the name is? I'm not sure I know what you're talking about.

---

### Post by Geffers on 2006-03-24
[QUOTE=aysiu]Can you give an example of what this "extra data" after the name is? I'm not sure I know what you're talking about.[/QUOTE]

I'm not on Linux at the moment so can't oblige but will not the extra data when I next log on.

Geffers

---

### Post by Geffers on 2006-03-25
[QUOTE=aysiu]Can you give an example of what this "extra data" after the name is? I'm not sure I know what you're talking about.[/QUOTE]

systemsettings -caption "%c" %i %m
adept %i %m -caption "%c"
kfmclient openProfile webbrowsing

None of these will open if I put each into the 'run' dialog box and run as root with the correct password.

Geffers

---

### Post by aysiu on 2006-03-25
[QUOTE=Geffers]systemsettings -caption "%c" %i %m
adept %i %m -caption "%c"
kfmclient openProfile webbrowsing

None of these will open if I put each into the 'run' dialog box and run as root with the correct password.

Geffers[/QUOTE] Yeah, that's weird. I don't know what the deal is with that.

If I do ```
kdesu adept %i %m -caption "%c"
``` from the run dialogue box, it just doesn't run.

If I do ```
kdesu adept
``` it does.

If I click on the KMenu launcher (which uses the command ```
adept %i %m -caption "%c"
``` as root), then it works.

No explanation that I know of...

---

### Post by Geffers on 2006-03-25
[QUOTE=aysiu]Yeah, that's weird. I don't know what the deal is with that.

If I do ```
kdesu adept %i %m -caption "%c"
``` from the run dialogue box, it just doesn't run.

If I do ```
kdesu adept
``` it does.

If I click on the KMenu launcher (which uses the command ```
adept %i %m -caption "%c"
``` as root), then it works.

No explanation that I know of...[/QUOTE]

Must be a bug :-k 

Might resolve itself in Dapper Drake when it gets launched.

Geffers

---

### Post by Barrakketh on 2006-03-25
> **Geffers]Must be a bug :-k 

Might resolve itself in Dapper Drake when it gets launched.

Geffers[/QUOTE]
It's the same in Dapper.  Ever consider that those are variables that the K-Menu is aware of?

[quote=KDE Menu Editor Manual]Following the command, you can have several place holders which will be replaced with actual values when the program is run: 
[indent]%f - a single file name
%F - a list of files said:**
> 

---

### Post by z-vet on 2006-03-25
From kmenuedit handbook:
"You can have several place holders which will be replaced with actual values when the program is run: 
f% - a single file name
F% - a list of files; use for applications that can open several local files at once
u% - a single URL
U% - a list of URLs
d% - the folder of a file to open
D% - a list of folders
i% - the icon
m% - the mini icon
c% - the caption"

I know very little about how exactly it used when running programs from KMenu (i think i will do a little research on it), but:
1. I assume that Geffers' problem is not these arguments used in KMenu: i have the very same arguments passed to many programs that run as root and as user and have no problem.
2. I tried to run KsCD from "Run" dialog with the following: 
```
kscd -caption "%c" %i %m
```
and a result was funny: first, i've got the following error (CD-ROM tray was open):
```
CD-ROM read or access error (or no audio disc in drive).
Please make sure you have access permissions to: %i
``` 
Next, i've got a "%c" instead of "KsCD" in it's window title and when i pressed "Close" button in right-click menu of KsCD's tray icon i was prompted: ```
Are you sure you want to quit %c ?
```

---

### Post by Barrakketh on 2006-03-25
The arguments from the manual (I've already filed a bug report for the typos) are processed only from within K-Menu.  The Run dialog has no knowledge of them, and is only passing along the arguments to the program you're trying to run.  Needless to say, the program sees %c in ARGV and is thinking "WTF?"

---

### Post by z-vet on 2006-03-25
[QUOTE=Barrakketh]The arguments from the manual (I've already filed a bug report for the typos) are processed only from within K-Menu.  The Run dialog has no knowledge of them, and is only passing along the arguments to the program you're trying to run.  Needless to say, the program sees %c in ARGV and is thinking "WTF?"[/QUOTE]
Can you explain a bit more what typos you're talking about, please? And it would be nice to get a link to bug report too. :)

---

### Post by Barrakketh on 2006-03-25
[QUOTE=z-vet]Can you explain a bit more what typos you're talking about, please? And it would be nice to get a link to bug report too. :)[/QUOTE]
Look at the piece of the manual I posted.  Or that you posted after that >_>  Notice the location of the "%" in relation to the characters...which are wrong.  If you compare them to the shortcuts you'd notice that "%" comes first, whereas the examples show the character being first.

---

### Post by z-vet on 2006-03-25
[QUOTE=Barrakketh]Look at the piece of the manual I posted.  Or that you posted after that >_>  Notice the location of the "%" in relation to the characters...which are wrong.  If you compare them to the shortcuts you'd notice that "%" comes first, whereas the examples show the character being first.[/QUOTE]
Yes, not in all of them but you're right. Thanks.

---

