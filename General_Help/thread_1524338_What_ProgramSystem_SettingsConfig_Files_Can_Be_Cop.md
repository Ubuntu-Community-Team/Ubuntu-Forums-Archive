---
title: "What Program/System Settings/Config Files Can Be Copied Over to a New Ubuntu Install?"
date: 2010-07-05
forum: General Help
---

### Post by OzzyFrank on 2010-07-05
Hi. I'm interested to hear what config/settings files - or whole folders - you've managed to simply copy over from your previous installation and have working in the new. This can be either for specific programs or for parts of the system, but I suppose most of what people would find useful is getting some of their programs back to how they had them.

These can be individual files or whole folders, but if there is a settings folder for a program but only one of the files is actually worth copying, just mention the one file and what it does.

Also interested in hearing from KDE and Xfce users, for the benefit of those of us who have multiple desktop environments in the same system. (Besides, even those with only Gnome will use some of the great KDE apps like Amarok and K3b).

*************************
Here are my contributions:
*************************
(**[COLOR="DarkRed"]~/[/COLOR]** denotes your home folder; any subfolders starting with a period [**[COLOR="DarkRed"].[/COLOR]**] are hidden files or folders)

**[COLOR="DarkRed"]~/.cache/rhythmbox/covers[/COLOR]** (the folder containing all your **album cover art displayed in Rhythmbox**)

**[COLOR="DarkRed"]~/.gnome2/nautilus-scripts[/COLOR]** (any **scripts you added to Nautilus** will be in this folder)

**[COLOR="DarkRed"]~/.lyrics[/COLOR]**  (the folder containing all your **song lyrics displayed in Rhythmbox**)

**[COLOR="DarkRed"]~/.local/share/rhythmbox/rhythmdb.xml[/COLOR]** (**Rhythmbox's database file**; if you were forced to edit this because of some incorrectly displayed tags, don't forget to copy it over).

**[COLOR="DarkRed"]~/.gconf/apps/rhythmbox/plugins/[/COLOR]** (**Rhythmbox's plugins** folder; plugins should be accessible when you restart Rythmbox).

**[COLOR="DarkRed"]~/.bash_aliases[/COLOR]** (**Terminal command aliases** you may have created will be in this file).

**[COLOR="DarkRed"]~/.gconf/apps/nautilus/preferences/%gconf.xml[/COLOR]** (**Nautilus folder preferences** file)
[B][COLOR="DarkRed"]
**~/.mozilla/firefox**[/COLOR][/B] (Folder for **Firefox settings, cache, bookmarks**, etc. If there are 2 or more subfolders with names like ***2tb4r91t.default*** just copy over the latest one, and make sure ***profiles.ini*** points to it)

**[COLOR="DarkRed"]~/.thunderbird[/COLOR]** (Mozilla **Thunderbird** folder with all accounts, emails, settings, etc)

************
Well, there's a few from me, so look forward to seeing what you suggest as well. Cheers.

---

### Post by dcstar on 2010-07-05
> **OzzyFrank said:**
> Hi. I'm interested to hear what config/settings files - or whole folders - you've managed to simply copy over from your previous installation and have working in the new. This can be either for specific programs or for parts of the system, but I suppose most of what people would find useful is getting some of their programs back to how they had them.
........

Why bother "copying" anything when you can use a separate /home partition which remains no matter how many installs you do?

If you want to make your life complicated then "copy" things, otherwise the simple way of doing things has been around for ages.

---

### Post by OzzyFrank on 2010-07-05
Forgive me if I am wrong here, but wouldn't that also mean that all the other config files and folders I perhaps **don't want** will still be there? Personally, I've installed millions of packages, and besides the fact I want to have my system as EXT4 (without converting it, thanks), I'm ready to leave behind a whole lot of junk I don't use, install only those apps I actually used more than once, and just copy over settings I need. Your suggestion really doesn't cater for that scenario.

And, no offence, I asked for suggestions for **what** to copy over, not **why not** to, but thanks anyway.

---

### Post by OzzyFrank on 2010-07-11
**_[COLOR="Indigo"]Azureus/Vuze:[/COLOR]_**

**[COLOR="DarkRed"]~/.azureus[/COLOR]** (folder for all of your **previous Vuze settings**)

**[COLOR="DarkRed"]~/Downloads/Azureus Downloads/[/COLOR]** (or wherever your **download temp folder** is located)

After installing Azureus in a new system, copying these over will ensure your file-sharing will resume from where you were previously.

---

