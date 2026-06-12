---
title: "Can dd command be verbose?"
date: 2006-03-20
forum: General Help
---

### Post by edm00se on 2006-03-20
I know it's not in the man pages, but is there a way to make dd verbose? i.e.- display progress in either size or percentage, or both (perhaps in the same way wget shows download progress). Could it be a script?
  Just thought it'd be nifty to have.

---

### Post by encompass on 2006-03-20
I don't seem to see it in the man dd file... I am wondering why you would want to see this raw data?

---

### Post by edm00se on 2006-03-20
[QUOTE=encompass]I don't seem to see it in the man dd file...[/QUOTE]
That's because it isn't. I already had looked. [QUOTE=edm00se]I know it's not in the man pages[/QUOTE]

[QUOTE=encompass]I am wondering why you would want to see this raw data?[/QUOTE]
I'm not looking for raw data, merely progress on file currently being processed.  [QUOTE=edm00se]i.e.- display progress in either size or percentage[/QUOTE]
Reason being: I wan't to know how long it'll take to process a large file.

---

### Post by edm00se on 2006-03-21
Okay, to kind of answer my own question, I'm going to be making an attempt at writing a script to do the job. I plan on basically just setting it up to grab file size of the source and output a progress bar using zenity as percentage copied of source. If anyone wants to chip in with any known command that merely grabs file size in bash, let me know.

---

### Post by edm00se on 2006-03-22
Okay, here's where I have. I think I have the right components. This is, of course, sans the zenity --file-progress portion.
> #!/bin/sh

OUTPUT='zenity --file-selection --save'

dd if=$1 of=$OUTPUT
[EDIT]Then it'll work the zenity --progress option in.[/EDIT]

Anyone care to help me out? Yes it's saved in my .gnome2/nautilus-scripts/ folder and is executable. It appears to do nothing from nautilus and yields the following error when run from terminal:
> dd: unrecognized option `--file-selection'
Try `dd --help' for more information.

To me, it looks like the script is attempting to pass the --file-selection flag to dd, not to zenity. So this leads me to wonder whether there's something fundamentally wrong with my defining of the variable OUTPUT. Thoughts?

---

