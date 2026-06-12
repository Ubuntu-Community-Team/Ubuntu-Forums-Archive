---
title: "Need an easy, preferably GUI-based way to list contents of a folder."
date: 2011-01-27
forum: General Help
---

### Post by HelloIndustries on 2011-01-27
I know this is possible via the command line, and it's a little beyond me.
I've looked around, and there's more than enough documentation on the possibilities availagble to me, but it just goes over my head every time.


What i would like to do is:

Select folder, say:
/media/Media/Music

[LIST]
[*]Make a text list of all the folders contained within, but *just* the name of the folders.
[*]List any folders within folders
[*]Output to, say /home/<user>/Documents/filelist-2011-01-27.txt
[/LIST]

Example:

/media/Media/Music
[INDENT]Folder name
[INDENT]sub-folder name
sub-folder name
sub-folder name
sub-folder name
sub-folder name[/INDENT][/INDENT]
[INDENT]Folder name
[INDENT]sub-folder name
sub-folder name
sub-folder name
sub-folder name
sub-folder name
sub-folder name
[INDENT]sub-folder name[/INDENT]
sub-folder name[/INDENT][/INDENT]

If there's a app available to do this: Awesome! Please let me know.
If not; If someone could let me know what i need to paste into the terminal, that'd be great!

No need to worry about cd commands, as i'll just open a terminal in the folder i want to list the contents of.

Thanks in advance.

---

### Post by AlphaLexman on 2011-01-27
on the command line:
```
tree -d > ~/Documents/filelist_2011-01-27.txt
```

---

### Post by HelloIndustries on 2011-01-27
> **AlphaLexman said:**
> on the command line:
```
tree -d > ~/Documents/filelist_2011-01-27.txt
```

Thanks so much! ^__^

---

### Post by frenchian on 2011-01-27
> **AlphaLexman said:**
> on the command line:
```
tree -d > ~/Documents/filelist_2011-01-27.txt
```

AlphaLexman, as another Ubuntu innocent, I'd appreciate some more help.

That command works perfectly for me in the terminal, but I'm trying to be smart and add it to the Nautilus menu - the right-click (contextual?) actions - using Nautilus Actions Configuration Tool.

I've got the path (/user/bin/tree) but I can't specify the parameters in such a way as to give me the same result. The best I can do is get it to list my home folder.

I'd be very grateful if you could help me with this.

Regards

---

### Post by AlphaLexman on 2011-01-27
> **frenchian said:**
> AlphaLexman, as another Ubuntu innocent, I'd appreciate some more help.

That command works perfectly for me in the terminal, but I'm trying to be smart and add it to the Nautilus menu - the right-click (contextual?) actions - using Nautilus Actions Configuration Tool.

I've got the path (/user/bin/tree) but I can't specify the parameters in such a way as to give me the same result. The best I can do is get it to list my home folder.

I'd be very grateful if you could help me with this.

Regards
I NEVER suggested it would work in nautilus, only at the command line. The OP was looking for a GUI solution, and if that could not be found a CLI solution would be acceptable, that is what I gave.

The OP could 'cd' to the directory they wanted to 'tree', in their example it was /media/Media/Music/

If you need help with the 'cd' command or the 'tree' command you should look at the 'man' page for each command,
```
man cp
man tree
```
else, start a new thread for your specific problem.

---

