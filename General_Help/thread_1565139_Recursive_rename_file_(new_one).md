---
title: "Recursive rename file (new one)"
date: 2010-08-31
forum: General Help
---

### Post by vak002 on 2010-08-31
Hi forum,

couldn't find the exact script for this (and i'm absolute beginner).

I have a lot of accidentally hidden files (accidentally named such as .name1.zip, .name2.zip,...) in various folders.

I'm trying to rename them in order to un-hidde them, i.e.:

.name1.zip->name1.zip
.name2.zip->name2.zip

to make matter worst, the files are in a large number of folders:
i.e. 

~/data/1995/01 Jan/
~/data/2005/02 Feb/
....

so the script should do it for all .zip files in all the sub-folders of ~/data


Can you help?:confused:

---

### Post by inameiname on 2010-08-31
you could do a search through Nautilus and highlight all you want changed, then use this handy script to rename all:

[http://www.omgubuntu.co.uk/2010/08/batch-rename-files-in-ubuntu-with.html](http://www.omgubuntu.co.uk/2010/08/batch-rename-files-in-ubuntu-with.html)

---

### Post by vak002 on 2010-08-31
thanks, but there is a large number of sub-folders (25*12). Can't it be scripted ? (all the .zip files in the main folders are to change).


GPrename does it one folder at the time.

Edit:KRename took care of the problem.

---

### Post by inameiname on 2010-08-31
Renamer's is GUI-based, so I'm not sure. You could maybe 'cd' several folders in the command to start renamer, idk. 

I just know that if you know just what and where the folders and subfolders are that have the files you want to change the name of, you could easily do a Nautilus search for them, and only highlight those '.' files from the folders you desire, and then right click and select the script, renamer, and then use the substitute command there that will remove the '.' for all. And as I'm sure you know, you could sort the files in a Nautilus search based on location, so it shouldn't be too hard. 

Anyway, perhaps there is a better script. Or if you want to check out the other renaming apps/scripts, Pyrenamer, Gwenrename, Gprename seem to be the most popular. Of course, you mentioned you already know about Gprename. Or find a simpler command line from someone on here if exists. Hopefully somebody might give you a better one, idk.

Or, seeing as how Renamer is a script, maybe you can tweak it to do your bidding the way you'd like.

---

### Post by dv3500ea on 2010-08-31
> **vak002 said:**
> Can't it be scripted ?.
Something like this:
```

ruby -e '
require "find"
require "FileUtils"
Find.find(Dir.pwd) do |p|
	if File.basename(p) =~ /\.(.*)\.zip$/
		n = "#{File.dirname(p)}/#{$1}.zip"
		puts "#{p} -> #{n}"
		FileUtils.mv(p, n)
	end
end
'

```
should work.

[SIZE="1"]*EDIT: oh, you solved it while I was typing...*[/SIZE]

---

### Post by vak002 on 2010-08-31
Actually, KRename failed to change many of the names :(

Do i just copy/past your script in the terminal?

---

### Post by dv3500ea on 2010-08-31
> **vak002 said:**
> Actually, KRename failed to change many of the names :(

Do i just copy/past your script in the terminal?

Yes. Make sure you are in the directory above all of the directories with the .zip files in.

You need to have [ruby]("apt:ruby") installed. If it is not installed, install it:
```

sudo apt-get install ruby

```

---

### Post by EricBaenen on 2010-10-28
Krename is a great way to accomplish this except the recursion in krename seems to be broken if your directory structure is two or more levels deep.  If it renamed all the files first and then the directories it would be ok - but it renames the directories - and then can't find the file below.  Does anyone know how to work around this with krename?

---

