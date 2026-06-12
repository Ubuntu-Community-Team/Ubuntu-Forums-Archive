---
title: "Export Existing Registry Keys From Windows Using Bash"
date: 2009-10-14
forum: General Help
---

### Post by allenwjones on 2009-10-14
[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="4"]Hello![/SIZE]

[SIZE="2"]I am an IT Professional who is using Linux as a tool to repair/backup network profiles for domain users. So far I have found sufficient methods to recover the data.

What I need:
My next phase in creating this tool is to be able to access an existing Windows registry hive or cached profile to export specific keys relating to mapped drive and network printers.

Also, it would be a real boon to be able to do this all from a BASH command script (which is how all the other recovery is done).

What I have tried so far:
I have attempted to use the wine regedit.exe as well as copying a 'real' regedt32.exe (and supporting .dll's) but neither of these will connect to an existing Windows registry. I have also tried to find an open sourced registry editor for linux or for windows (to use in wine) with no success.


I realize this is an advanced topic, but I feel it will be fairly useful when solved with many fringe benefits from discovering this process. I appreciate any experience anyone can give to help.[/SIZE]

[SIZE="4"]Thank You![/SIZE]
[/COLOR][/FONT]

---

### Post by Giblet5 on 2009-10-14
I'm 99 and 44/100ths percent sure you'll need to partner with Microsoft on this effort.

It will require internals knowledge for the Windows registry's physical structure and logical layout, indexing, etc.

Windows' registry mechanism is proprietary and your proposed utility is, potentially, a massive security risk so I'm skeptical that you'll succeed in any partnering attempt.

You can find out where it is by scanning the raw disk for known registry values, taking the block offset of a match and tracking down the location in the MFT.

---

### Post by allenwjones on 2009-10-14
[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Thanks for your reply![/SIZE]

[SIZE="2"]However, I do know that it is possible to access a remote Windows registry (albeit in a limited fashion) using 'chntpw -e' and pointing to a registry hive file. Unfortunately I have not found a way to utilize this tool to export individual or group keys. I know which keys I need, it's a matter of being able to export them, specifically from Bash.


I agree that any attempt to work with Microsoft directly would be fruitless.[/SIZE]

[/COLOR][/FONT]

---

### Post by Giblet5 on 2009-10-14
> **allenwjones said:**
> [FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Thanks for your reply![/SIZE]

[SIZE="2"]However, I do know that it is possible to access a remote Windows registry (albeit in a limited fashion) using 'chntpw -e' and pointing to a registry hive file. Unfortunately I have not found a way to utilize this tool to export individual or group keys. I know which keys I need, it's a matter of being able to export them, specifically from Bash.


I agree that any attempt to work with Microsoft directly would be fruitless.[/SIZE]

[/COLOR][/FONT]


Yes, you can access a remote Windows registry... But can you read registry entries from a mounted NTFS partition w/o Windows executing? That's what you need to accomplish, right?

---

### Post by allenwjones on 2009-10-14
> But can you read registry entries from a mounted NTFS partition?

[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Yes,[/SIZE] [SIZE="2"]I can mount a local NTFS partition using 'mount -t ntfs' to a folder of choice and access it with the 'chntpw -e' tool.

I just have not been able to use this particular tool from Bash to export specific keys(s)/groups.

Additional:
I have not found a 3rd party open source registry editor with CLI that I could wine either.[/SIZE]

[/COLOR][/FONT]

---

### Post by StuartN on 2009-10-14
There is this Offline NT Password and Registry Editor [http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/) that claims "There is also a registry editor and other registry utilities that works under linux/unix, and can be used for other things than password editing."

---

### Post by Giblet5 on 2009-10-14
> **allenwjones said:**
> [FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Yes,[/SIZE] [SIZE="2"]I can mount a local NTFS partition using 'mount -t ntfs' to a folder of choice and access it with the 'chntpw -e' tool.

I just have not been able to use this particular tool from Bash to export specific keys(s)/groups.

Additional:
I have not found a 3rd party open source registry editor with CLI that I could wine either.[/SIZE]

[/COLOR][/FONT]


Hmmm. I've never used it.

Does it use screen/cursor control? If not, you can "feed" commands to it via redirection, just like ftp or anything else.

Example ftp session from a bash script: ```
#!/bin/bash

ftp -n -i ftp.x.org << ! > /dev/null 2>&1
user anonymous me@here
get ls-lR.Z
quit
!
```

The redirection '<< !' tells the shell to use subsequent lines, up to the next occurrence of '!' as input to the ftp command.

The '> /dev/null 2>&1' part tells the shell to send stdout and stderr to /dev/null (bottomless bit bucket).

Therefore, if you know what commands need to be executed, you can execute them, capturing the output in a temp file or variable for later extraction.

---

### Post by allenwjones on 2009-10-14
> **StuartN said:**
> There is this Offline NT Password and Registry Editor [http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/) that claims "There is also a registry editor and other registry utilities that works under linux/unix, and can be used for other things than password editing."

[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Thanks![/SIZE] [SIZE="2"]I will try that application also..[/SIZE]

[/COLOR][/FONT]

---

### Post by allenwjones on 2009-10-14
> **Giblet5 said:**
> Does it use screen/cursor control? If not, you can "feed" commands to it via redirection, just like ftp or anything else.

[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Hmmm,[/SIZE] [SIZE="2"]I'm not sure I am following you on this? Yes, the 'chntpw -e' is terminal so if there is a way to automate the terminal responses (as you suggested with your FTP example) then I don't see why something along that line might work.. be a bit of a pain to get set up, but thank you for that suggestion!

I am really hoping for something more direct to surface, but that could be a solution.[/SIZE]

[/COLOR][/FONT]

---

### Post by Giblet5 on 2009-10-14
> **allenwjones said:**
> [FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Hmmm,[/SIZE] [SIZE="2"]I'm not sure I am following you on this? Yes, the 'chntpw -e' is terminal so if there is a way to automate the terminal responses (as you suggested with your FTP example) then I don't see why something along that line might work.. be a bit of a pain to get set up, but thank you for that suggestion!

I am really hoping for something more direct to surface, but that could be a solution.[/SIZE]

[/COLOR][/FONT]


Well, a direct solution would be to rip the needed code from chntpw's source code and implement exactly what you need. If that's too much trouble, the redirection thing should work and it's easy enough to try....

---

### Post by allenwjones on 2009-10-14
> **Giblet5 said:**
> Well, a direct solution would be to rip the needed code from chntpw's source code and implement exactly what you need. If that's too much trouble, the redirection thing should work and it's easy enough to try....

[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]A good point..[/SIZE]
[SIZE="2"]Can I accept that as a volunteer? :D I mean, I am not a coder. Sure I hack a few scripts together but source is out of my league.. But that does sound like a reasonable solution.[/SIZE]

[/COLOR][/FONT]

---

### Post by Giblet5 on 2009-10-14
> **allenwjones said:**
> [FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]A good point..[/SIZE]
[SIZE="2"]Can I accept that as a volunteer? :D I mean, I am not a coder. Sure I hack a few scripts together but source is out of my league.. But that does sound like a reasonable solution.[/SIZE]

[/COLOR][/FONT]

Volunteer? What's that? ;)

Try the redirection route.

What's the path to the hive? What key/value pairs do you need? I'll try it and, if it works, I'll post the code.

---

### Post by allenwjones on 2009-10-14
> **Giblet5 said:**
> What's the path to the hive? What key/value pairs do you need? I'll try it and, if it works, I'll post the code.

[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Nice![/SIZE] [SIZE="2"]I have a better suggestion: As I am sure I will not be the only person who will ultimately use this, why don't you make two CLI switch/inputs? Make one for location of the hive and one for an answer file (to specify key variables) to allow for flexibility down the road..[/SIZE]

[SIZE="2"]By the way, I really appreciate your willingness to take a crack at the code. I will be pursuing the automation route anyways if not for practice only but as a fallback in case you do not succeed right away.[/SIZE]

[SIZE="3"]Thank You![/SIZE]
[/COLOR][/FONT]

---

### Post by Giblet5 on 2009-10-14
> **allenwjones said:**
> [FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Nice![/SIZE] [SIZE="2"]I have a better suggestion: As I am sure I will not be the only person who will ultimately use this, why don't you make two CLI switch/inputs? Make one for location of the hive and one for an answer file (to specify key variables) to allow for flexibility down the road..[/SIZE]

[SIZE="2"]By the way, I really appreciate your willingness to take a crack at the code. I will be pursuing the automation route anyways if not for practice only but as a fallback in case you do not succeed right away.[/SIZE]

[SIZE="3"]Thank You![/SIZE]
[/COLOR][/FONT]


I can't even find the registry files on Vista64 or XP64.

The Wiki claims they're stored in %SystemRoot%\System32\config...

Guess where they're NOT stored on an x64 install...

---

### Post by allenwjones on 2009-10-14
[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Let's Simplify:[/SIZE]

[SIZE="2"]Windows 2000/XP keeps the user specific settings in:

c:\Documents and Settings\{logon}\Ntuser.dat

I can access this using 'chntpw -e {mapping}' and it would seem that access is very similar to using a file system.. 'ls' and 'cd' work to navigate.[/SIZE]

[/COLOR][/FONT]

---

### Post by Giblet5 on 2009-10-14
> **allenwjones said:**
> [FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="3"]Let's Simplify:[/SIZE]

[SIZE="2"]Windows 2000/XP keeps the user specific settings in:

c:\Documents and Settings\{logon}\Ntuser.dat

I can access this using 'chntpw -e {mapping}' and it would seem that access is very similar to using a file system.. 'ls' and 'cd' work to navigate.[/SIZE]

[/COLOR][/FONT]

It doesn't work for x64.

```
chntpw -e NTUSER.DAT
chntpw version 0.99.5 070923 (decade), (c) Petter N Hagen
openHive(NTUSER.DAT): File does not seem to be a registry hive!
Simple registry editor. ? for help.
get_abs_path: Not a 'nk' node!

> ls
trav_path: Error: Not a 'nk' node!
nk_ls: Key <> not found
get_abs_path: Not a 'nk' node!

> q
``` ```
file NTUSER.DAT
            MS Windows registry file, NT/2000 or above
```

(That's Windows XP Professional x64 Edition)

---

### Post by allenwjones on 2009-10-14
[FONT="Century Gothic"][COLOR="DarkRed"]
[SIZE="2"]Well, that takes the steam out of the engine then. At least I have been able to verify the locations and methods for listing the various keys on a standard Windows XP Pro install, but there is no forward compatibility and I am sure the corporation I work for will move to a 64 bit OS soon enough. If automation is not very difficult, I will pursue that route until a full Open Source registry editor is devised.

I suppose this is not bad for a tool that was built over 2 years ago.. The second link that was posted turns out to be the same application packaged for bootability.

Again, I appreciate your time and effort on this and anything else you are willing to do.[/SIZE]

[SIZE="3"]Thank You![/SIZE]
[/COLOR][/FONT]

---

