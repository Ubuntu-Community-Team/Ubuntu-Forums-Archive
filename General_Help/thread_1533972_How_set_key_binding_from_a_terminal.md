---
title: "How set key binding from a terminal"
date: 2010-07-18
forum: General Help
---

### Post by Muscovy on 2010-07-18
I'm trying to make a script that adds a systemwide keybinding, but I can't find a way to do it from a terminal. Can anyone help?

Thanks.

---

### Post by Zorgoth on 2010-07-18
If you are using compiz you can probably do it with gconftool-2; otherwise look at xbindkeys; I do not understand it, but you can try to learn...

Maybe gconftool-2 in /desktop/gnome/keybindings or /apps/compiz/plugins/commands/allscreens/options?

---

### Post by Zorgoth on 2010-07-18
Just confirmed that you can easily do it using gconftool-2 in /desktop/gnome/keybindings, at least in Fedora 13/metacity; just use the same format that is used for the other three (a subdirectory with three keys, binding, name, and action).  The directory will be automatically created when you try to set a key.

Just discovered it works with Fedora 13/compiz as well.

---

### Post by Muscovy on 2010-07-18
I found the info in /desktop/gnome/keybindings. Now I need to figure out how to work with it, but thanks. :p I'm sure setting gconf globals isn't hard.

---

### Post by Muscovy on 2010-07-18
I can't get it to work through gconf at all. I tried adding a key in /usr/share/gconf/defaults, I tried using gconf-tool2, and with the file browser. All did nothing.

---

### Post by Zorgoth on 2010-07-18
Try running these commands and tell me the results (Unless Shift-Control-P is bount to something on your computer)

```

gconftool-2 -s /desktop/gnome/keybindings/test/binding --type=string '<Shift><Control>p'
gconftool-2 -s /desktop/gnome/keybindings/test/name --type=string 'test'
gconftool-2 -s /desktop/gnome/keybindings/test/action --type=string 'gedit'

```

That is exactly what I did and it worked (As in Shift-Control-p now opens gedit).

---

### Post by Muscovy on 2010-07-19
Ok, thanks! Works for me too, I forgot the --type part.

Do you know how to apply this globally? I'm dreading making a system that sudo su's into all accounts to set this up.

---

### Post by Zorgoth on 2010-07-19
Well if you want to do it that way, then here is my suggestion, although you may want to consult someone wiser in the ways of linux than I, and I have not tried it; you could keep a "master list" of keybindings in a special directory (perhaps somwhere in /usr/share/directory_name).  You would want a directory which I will refer to as /special/directory containing nothing but the *directories* containing the keys; e.g. it would contain the directory /.gconf/desktop/gnome/keybindings/test (called simply test).  The files and directories inside should have world-readable permissions and not world writable permissions (if they were world-writable any user could change all other user's keybindings!).

If you want people to be allowed to turn off/configure your keybindings, use "cp -R" instead of "mount -B." and then set the permissions appropriately, and allow users to store information somewhere on which keybindings they want to not be overwritten (and then for each keybinding you can put an if statement before cp -R).

If you have not done so already:

Rename /etc/gdm/PostLogin/Default.sample to /etc/gdm/PostLogin/Default and then chmod +x /etc/gdm/PostLogin/Default.

Then add the following lines to /etc/gdm/PostLogin/Default:

```

KEYBINDS=`ls -A /special/directory`
for keybind in ${KEYBINDS}
do
    mount -B /special/directory/$keybind $HOME/.gconf/desktop/gnome/keybindings/$keybind
done

```

---

### Post by Zorgoth on 2010-07-19
Just a note; it seems like even altering the permissions of the files will not prevent changing keyboard shortcuts, at least within a session; but it seems like that probably isn't particularly important.

---

### Post by Zorgoth on 2010-07-19
Actually, I think that looking through gconftool-2 --help-all, you may find in the Installation section details on a more official way to do save/load configurations.

---

### Post by Muscovy on 2010-07-19
Schemas seems to be the way to do it. First problem I'm hitting in this is the values. Somehow, they're all set to "<schema>".

Here's an example from the three values.
```

      <schema>
      <key>/desktop/gnome/keybindings/imgur-uploader/action</key>
      <applyto>/desktop/gnome/keybindings/imgur-uploader/action</applyto>
      <owner>imgur-uploader</owner>
      <type>string</type>
      <default>/home/alex/Desktop/screenshot.sh</default>
      <locale name="C">
	<short>Screenshot and upload automatically.</short>
	<long>
	Take screenshots and upload them to imgur.
	</long>
      </locale>
      </schema>

```

I'm about to be going away for a few days, but hopefuly when I get back I can figure this out. Thanks for your help. :D

---

