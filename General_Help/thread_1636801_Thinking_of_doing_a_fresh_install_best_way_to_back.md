---
title: "Thinking of doing a fresh install: best way to backup my stuff?"
date: 2010-12-03
forum: General Help
---

### Post by ninjaaron on 2010-12-03
While I am overall very satisfied with 10.10, there have been a few weird things going on since I upgraded. The most irritating of these is definitely the fact that I can't get the most recent kernels working. I'm stuck with the Kernel from 10.04.

Anyway, I suppose a fresh install might fix the issues, but I need to backup. Obviously this would entail backing up my home folder, but I would also prefer not to have to reinstall all my applications, especially since some of them are from repositories that I don't even remember anymore. In addition, I've installed some fonts of which I've become rather fond, and I would hate to loose those.

I know that I'll have to backup my /home folder and /usr/share, but I'm not sure what else I will need to save all my apps and settings.

---

### Post by 0949er on 2010-12-03
in your case I would suggest a second HD and just coping most of everything over

---

### Post by ninjaaron on 2010-12-03
> **0949er said:**
> in your case I would suggest a second HD and just coping most of everything over

Eh... wouldn't that make it as if I hadn't done a fresh install at all?

---

### Post by ninjaaron on 2010-12-03
After looking at my file system a bit more, it seems like the only things I would really need to back up are my home folder and my /usr folder, since that seems to be where all the binaries and fonts and configurations are in the first place. Any thoughts?

---

### Post by Mosabama on 2010-12-03
you can use APTonCD to backup all the applications you want in the new ubuntu.

---

### Post by CharlesA on 2010-12-03
> **ninjaaron said:**
> After looking at my file system a bit more, it seems like the only things I would really need to back up are my home folder and my /usr folder, since that seems to be where all the binaries and fonts and configurations are in the first place. Any thoughts?

Just backup yer home directory.

You'd have to reinstall all yer apps on the new install.

---

### Post by oldfred on 2010-12-03
You want to make a list of installed apps so you can reinstall with the newest versions:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

### Post by CharlesA on 2010-12-03
Thanks oldfred. I was trying to figure out how they did that with Synaptic. :)

---

### Post by ninjaaron on 2010-12-04
Thanks for all the tips guys. I'll have a look-see about all this stuff.

---

### Post by ninjaaron on 2010-12-05
Out of curiosity, are any of the backup applications useful for this, or is it better just to do it all manually?

---

### Post by CharlesA on 2010-12-05
> **ninjaaron said:**
> Out of curiosity, are any of the backup applications useful for this, or is it better just to do it all manually?
As far as I know there isn't really any software that'll backup yer applications for you automatically.

---

### Post by ninjaaron on 2010-12-10
Ok, I did it (a few days back). I just backed up my home folder on an external, backed up a few of my favourite fonts which aren't part of Ubuntu (but I had installed system-wide) and a few other odds and ends. I also backed up my package archive, just in case I couldn't find anything.

Then formatted my drive and did a fresh install.

I decided just to install the software over again as I needed it, and to move only migrate my home folder as I wanted things. Some things got moved very quickly (like my documents, custom keyboard layout, and OOo settings), and other things aren't going to be moved until they are wanted (like my music library, one album or artist at a time). I don't imagine I'll be using the package archive at all, but it is there just in case.

So thanks. The fresh install fixed my bugs, and I've got all the stuff I wanted (and so far, none of what I don't).

---

