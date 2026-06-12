---
title: "gconf-editor missing ftp entry"
date: 2011-05-02
forum: General Help
---

### Post by TLangas on 2011-05-02
For some reason my gconf-editor does not have a ftp entry. (**/desktop/gnome/url-handlers/ftp**)
This is annoying as it sets all unknown urls to firefox. I always liked Nautilus as the default. 

I tried creating a **%gconf.xml** file to **$HOME/.gconf/desktop/gnome/url-handlers/ftp/** and still no luck.

Any ideas?

---

### Post by Benchamoneh on 2011-06-29
I tried this too before I went Googling, anyone else have any ideas? Seems to be a change made on 11.04 as the option is still available on my 10.10 install...

---

### Post by Benchamoneh on 2011-06-29
Ok, to 'technically' answer your question, this code will get the ftp URL handler options back into gconf (copypaste friendly):
```
gconftool -s --type=string /desktop/gnome/url-handlers/ftp/command "nautilus %s"
gconftool -s --type=bool /desktop/gnome/url-handlers/ftp/enabled true
gconftool -s --type=bool /desktop/gnome/url-handlers/ftp/needs_terminal false
gconftool --set-schema --short-desc="The handler for \"ftp\" URLs" --long-desc="The command used to handle \"ftp\" URLs, if enabled" --owner=gnome --type=string /schemas/desktop/gnome/url-handlers/ftp/command
gconftool --set-schema --short-desc="Whether the specified command should handle \"ftp\" URLs" --long-desc="True if the command specified in the \"command\" key should handle \"ftp\" URLs." --owner=gnome --type=bool /schemas/desktop/gnome/url-handlers/ftp/enabled
gconftool --set-schema --short-desc="Run the command in a terminal" --long-desc="True if the command used to handle this type of URL should be run in a terminal." --owner=gnome --type=bool /schemas/desktop/gnome/url-handlers/ftp/needs_terminal
gconftool --apply-schema /schemas/desktop/gnome/url-handlers/ftp/command /desktop/gnome/url-handlers/ftp/command
gconftool --apply-schema /schemas/desktop/gnome/url-handlers/ftp/enabled /desktop/gnome/url-handlers/ftp/enabled
gconftool --apply-schema /schemas/desktop/gnome/url-handlers/ftp/needs_terminal /desktop/gnome/url-handlers/ftp/needs_terminal
exit

```

Though much to my annoyance it would appear that the handler keys are completely ignored by firefox anyway, as it just grabs the URL and opens regardless, like a fat kid being told not to touch the cake :-x ...

---

### Post by Benchamoneh on 2011-06-29
So it would seem that this problem is caused because gvfs-open is now used for file/extension associations instead of gnome-open in 11.04? (someone correct me if I'm wrong here!)

You can set nautilus to open FTP links by appending the following line to /etc/gnome/defaults.list

```
x-scheme-handler/ftp=nautilus-folder-handler.desktop
```

Works for me anyway. Depending on what you've been doing with your system you might need to stick it in ~/.local/share/applications/mimeapps.list too by adding

```
x-scheme-handler/ftp=nautilus;
```

though I didn't need to, YMMV...

---

### Post by TLangas on 2011-06-29
Funny, both solutions look like it should work. Still no luck, Firefox still steals the ftp connections when going through the Places menu.

At the moment I've been opening Nautilus first, then going to File -> Connect to Server. Or using FileZilla.

---

### Post by johnitsa on 2011-07-20
Worked like a charm.

Thanks :)

Later edit: Apparently I got fooled. It only worked once. Firefox started "stealing" ftp links again

> **Benchamoneh said:**
> Ok, to 'technically' answer your question, this code will get the ftp URL handler options back into gconf (copypaste friendly):
```
gconftool -s --type=string /desktop/gnome/url-handlers/ftp/command "nautilus %s"
gconftool -s --type=bool /desktop/gnome/url-handlers/ftp/enabled true
gconftool -s --type=bool /desktop/gnome/url-handlers/ftp/needs_terminal false
gconftool --set-schema --short-desc="The handler for \"ftp\" URLs" --long-desc="The command used to handle \"ftp\" URLs, if enabled" --owner=gnome --type=string /schemas/desktop/gnome/url-handlers/ftp/command
gconftool --set-schema --short-desc="Whether the specified command should handle \"ftp\" URLs" --long-desc="True if the command specified in the \"command\" key should handle \"ftp\" URLs." --owner=gnome --type=bool /schemas/desktop/gnome/url-handlers/ftp/enabled
gconftool --set-schema --short-desc="Run the command in a terminal" --long-desc="True if the command used to handle this type of URL should be run in a terminal." --owner=gnome --type=bool /schemas/desktop/gnome/url-handlers/ftp/needs_terminal
gconftool --apply-schema /schemas/desktop/gnome/url-handlers/ftp/command /desktop/gnome/url-handlers/ftp/command
gconftool --apply-schema /schemas/desktop/gnome/url-handlers/ftp/enabled /desktop/gnome/url-handlers/ftp/enabled
gconftool --apply-schema /schemas/desktop/gnome/url-handlers/ftp/needs_terminal /desktop/gnome/url-handlers/ftp/needs_terminal
exit

```Though much to my annoyance it would appear that the handler keys are completely ignored by firefox anyway, as it just grabs the URL and opens regardless, like a fat kid being told not to touch the cake :-x ...

---

