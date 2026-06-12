---
title: "Problem with executing my first bash script"
date: 2009-10-30
forum: General Help
---

### Post by emigrant on 2009-10-30
hi,
iv started learning bash scripting from this tutorial:
[http://www.linuxcommand.org/wss0030.php](http://www.linuxcommand.org/wss0030.php)

here is what i did:
```

#!/bin/bash
# make_page - A script to produce an HTML file

title="System Information for"
RIGHT_NOW=$(date +"%x %r %z")
TIME_STAMP="Updated on $RIGHT_NOW by $USER"

# Functions...
function system_info
{
    echo "system_info"
}

function show_uptime
{
    #echo "system_uptime"
    uptime
}

function drive_space
{
    echo "<h2>system_space</h2>"
    df
}

function home_space
{
    echo "<h2>Home directory space by user</h2>"
    echo "<pre>"
    echo "Bytes Directory"
    du -sh /home/* | sort -n
    echo "</pre>"

}

# Main
cat <<- _EOF_
    <HTML>
    <HEAD>
        <TITLE>
        $title $HOSTNAME
        </TITLE>
    </HEAD>

    <BODY>
    <H1>$title $HOSTNAME</H1>
    <P>$TIME_STAMP</p>
    $(system_info)
    $(show_uptime)
    $(drive_space)
    $(home_space)
    </BODY>
    </HTML>
_EOF_

```

my problem is in terminal i can run the script, and the du command works with regard to the other user directories.

but when i try to make

```
make_page > page.html
```

i get permission denied for the du command on other users directories.

i cant do this even with sudo


any help would be highly appreciated.

thank you very much :)

---

### Post by alphaniner on 2009-10-30
I'm trying to understand what's going on here, but I'm struggling. :(

Could you post the exact error messages you get when you run **make_page > page.html**

---

### Post by emigrant on 2009-10-30
thank you for coming for the rescue :KS
here it is the error message i get:

```
du: cannot read directory `/home/user_1/.gconf': Permission denied
du: cannot read directory `/home/user_1/.mozilla': Permission denied
du: cannot read directory `/home/user_1/.openoffice.org/3': Permission denied
du: cannot read directory `/home/user_1/.gnome2': Permission denied
du: cannot read directory `/home/user_1/.update-notifier': Permission denied
du: cannot read directory `/home/user_1/.ggz': Permission denied
du: cannot read directory `/home/user_1/.pulse': Permission denied
du: cannot read directory `/home/user_1/.cache/compizconfig': Permission denied
du: cannot read directory `/home/user_1/.dbus': Permission denied
du: cannot read directory `/home/user_1/.gvfs': Permission denied
du: cannot read directory `/home/user_1/.thumbnails': Permission denied
du: cannot read directory `/home/user_1/.gnupg': Permission denied
du: cannot read directory `/home/user_1/.compiz': Permission denied
du: cannot read directory `/home/user_1/.gnome2_private': Permission denied
du: cannot read directory `/home/user_1/.config/enchant': Permission denied
du: cannot read directory `/home/user_1/.config/compiz': Permission denied
du: cannot read directory `/home/user_1/.config/totem': Permission denied
du: cannot read directory `/home/user_1/.config/gtk-2.0': Permission denied
du: cannot read directory `/home/user_1/.evolution/memos/local': Permission denied
du: cannot read directory `/home/user_1/.evolution/calendar/local': Permission denied
du: cannot read directory `/home/user_1/.evolution/tasks/local': Permission denied
du: cannot read directory `/home/user_1/.gconfd': Permission denied
du: cannot read directory `/home/user_1/.nautilus/metafiles': Permission denied
du: cannot read directory `/home/user_1/.local': Permission denied
du: cannot read directory `/home/user_2/.gconf': Permission denied
du: cannot read directory `/home/user_2/.ssh': Permission denied
du: cannot read directory `/home/user_2/.mozilla': Permission denied
du: cannot read directory `/home/user_2/.openoffice.org/3': Permission denied
du: cannot read directory `/home/user_2/.gnome2': Permission denied
du: cannot read directory `/home/user_2/.update-notifier': Permission denied
du: cannot read directory `/home/user_2/.pulse': Permission denied
du: cannot read directory `/home/user_2/.cache/compizconfig': Permission denied
du: cannot read directory `/home/user_2/.cache/chromium': Permission denied
du: cannot read directory `/home/user_2/.dbus': Permission denied
du: cannot read directory `/home/user_2/.gvfs': Permission denied
du: cannot read directory `/home/user_2/.thumbnails': Permission denied
du: cannot read directory `/home/user_2/.gnupg': Permission denied
du: cannot read directory `/home/user_2/.compiz': Permission denied
du: cannot read directory `/home/user_2/Desktop/user_2/avast__4.8.1287_PRO_': Permission denied
du: cannot read directory `/home/user_2/.gnome2_private': Permission denied
du: cannot read directory `/home/user_2/.config/compiz': Permission denied
du: cannot read directory `/home/user_2/.config/totem': Permission denied
du: cannot read directory `/home/user_2/.config/gtk-2.0': Permission denied
du: cannot read directory `/home/user_2/.config/brasero': Permission denied
du: cannot read directory `/home/user_2/.config/chromium': Permission denied
du: cannot read directory `/home/user_2/.gegl-0.0': Permission denied
du: cannot read directory `/home/user_2/.gconfd': Permission denied
du: cannot read directory `/home/user_2/.nautilus/metafiles': Permission denied
du: cannot read directory `/home/user_2/.local': Permission denied
du: cannot read directory `/home/user_3/.gconf': Permission denied
du: cannot read directory `/home/user_3/.mozilla': Permission denied
du: cannot read directory `/home/user_3/.gnome2': Permission denied
du: cannot read directory `/home/user_3/.update-notifier': Permission denied
du: cannot read directory `/home/user_3/.ggz': Permission denied
du: cannot read directory `/home/user_3/.pulse': Permission denied
du: cannot read directory `/home/user_3/.cache/compizconfig': Permission denied
du: cannot read directory `/home/user_3/.cache/chromium': Permission denied
du: cannot read directory `/home/user_3/.dbus': Permission denied
du: cannot read directory `/home/user_3/.gvfs': Permission denied
du: cannot read directory `/home/user_3/.thumbnails': Permission denied
du: cannot read directory `/home/user_3/.pki': Permission denied
du: cannot read directory `/home/user_3/.gnupg': Permission denied
du: cannot read directory `/home/user_3/.compiz': Permission denied
du: cannot read directory `/home/user_3/.gnome2_private': Permission denied
du: cannot read directory `/home/user_3/.config/compiz': Permission denied
du: cannot read directory `/home/user_3/.config/totem': Permission denied
du: cannot read directory `/home/user_3/.config/gtk-2.0': Permission denied
du: cannot read directory `/home/user_3/.config/chromium': Permission denied
du: cannot read directory `/home/user_3/.evolution/memos/local': Permission denied
du: cannot read directory `/home/user_3/.evolution/calendar/local': Permission denied
du: cannot read directory `/home/user_3/.evolution/tasks/local': Permission denied
du: cannot read directory `/home/user_3/.gconfd': Permission denied
du: cannot read directory `/home/user_3/.nautilus/metafiles': Permission denied
du: cannot read directory `/home/user_3/.local': Permission denied
arshad@arshad-desktop:~/Documents/BashTest$ secondBash > page.html
du: cannot read directory `/home/user_1/.gconf': Permission denied
du: cannot read directory `/home/user_1/.mozilla': Permission denied
du: cannot read directory `/home/user_1/.openoffice.org/3': Permission denied
du: cannot read directory `/home/user_1/.gnome2': Permission denied
du: cannot read directory `/home/user_1/.update-notifier': Permission denied
du: cannot read directory `/home/user_1/.ggz': Permission denied
du: cannot read directory `/home/user_1/.pulse': Permission denied
du: cannot read directory `/home/user_1/.cache/compizconfig': Permission denied
du: cannot read directory `/home/user_1/.dbus': Permission denied
du: cannot read directory `/home/user_1/.gvfs': Permission denied
du: cannot read directory `/home/user_1/.thumbnails': Permission denied
du: cannot read directory `/home/user_1/.gnupg': Permission denied
du: cannot read directory `/home/user_1/.compiz': Permission denied
du: cannot read directory `/home/user_1/.gnome2_private': Permission denied
du: cannot read directory `/home/user_1/.config/enchant': Permission denied
du: cannot read directory `/home/user_1/.config/compiz': Permission denied
du: cannot read directory `/home/user_1/.config/totem': Permission denied
du: cannot read directory `/home/user_1/.config/gtk-2.0': Permission denied
du: cannot read directory `/home/user_1/.evolution/memos/local': Permission denied
du: cannot read directory `/home/user_1/.evolution/calendar/local': Permission denied
du: cannot read directory `/home/user_1/.evolution/tasks/local': Permission denied
du: cannot read directory `/home/user_1/.gconfd': Permission denied
du: cannot read directory `/home/user_1/.nautilus/metafiles': Permission denied
du: cannot read directory `/home/user_1/.local': Permission denied
du: cannot read directory `/home/user_2/.gconf': Permission denied
du: cannot read directory `/home/user_2/.ssh': Permission denied
du: cannot read directory `/home/user_2/.mozilla': Permission denied
du: cannot read directory `/home/user_2/.openoffice.org/3': Permission denied
du: cannot read directory `/home/user_2/.gnome2': Permission denied
du: cannot read directory `/home/user_2/.update-notifier': Permission denied
du: cannot read directory `/home/user_2/.pulse': Permission denied
du: cannot read directory `/home/user_2/.cache/compizconfig': Permission denied
du: cannot read directory `/home/user_2/.cache/chromium': Permission denied
du: cannot read directory `/home/user_2/.dbus': Permission denied
du: cannot read directory `/home/user_2/.gvfs': Permission denied
du: cannot read directory `/home/user_2/.thumbnails': Permission denied
du: cannot read directory `/home/user_2/.gnupg': Permission denied
du: cannot read directory `/home/user_2/.compiz': Permission denied
du: cannot read directory `/home/user_2/Desktop/user_2/avast__4.8.1287_PRO_': Permission denied
du: cannot read directory `/home/user_2/.gnome2_private': Permission denied
du: cannot read directory `/home/user_2/.config/compiz': Permission denied
du: cannot read directory `/home/user_2/.config/totem': Permission denied
du: cannot read directory `/home/user_2/.config/gtk-2.0': Permission denied
du: cannot read directory `/home/user_2/.config/brasero': Permission denied
du: cannot read directory `/home/user_2/.config/chromium': Permission denied
du: cannot read directory `/home/user_2/.gegl-0.0': Permission denied
du: cannot read directory `/home/user_2/.gconfd': Permission denied
du: cannot read directory `/home/user_2/.nautilus/metafiles': Permission denied
du: cannot read directory `/home/user_2/.local': Permission denied
du: cannot read directory `/home/user_3/.gconf': Permission denied
du: cannot read directory `/home/user_3/.mozilla': Permission denied
du: cannot read directory `/home/user_3/.gnome2': Permission denied
du: cannot read directory `/home/user_3/.update-notifier': Permission denied
du: cannot read directory `/home/user_3/.ggz': Permission denied
du: cannot read directory `/home/user_3/.pulse': Permission denied
du: cannot read directory `/home/user_3/.cache/compizconfig': Permission denied
du: cannot read directory `/home/user_3/.cache/chromium': Permission denied
du: cannot read directory `/home/user_3/.dbus': Permission denied
du: cannot read directory `/home/user_3/.gvfs': Permission denied
du: cannot read directory `/home/user_3/.thumbnails': Permission denied
du: cannot read directory `/home/user_3/.pki': Permission denied
du: cannot read directory `/home/user_3/.gnupg': Permission denied
du: cannot read directory `/home/user_3/.compiz': Permission denied
du: cannot read directory `/home/user_3/.gnome2_private': Permission denied
du: cannot read directory `/home/user_3/.config/compiz': Permission denied
du: cannot read directory `/home/user_3/.config/totem': Permission denied
du: cannot read directory `/home/user_3/.config/gtk-2.0': Permission denied
du: cannot read directory `/home/user_3/.config/chromium': Permission denied
du: cannot read directory `/home/user_3/.evolution/memos/local': Permission denied
du: cannot read directory `/home/user_3/.evolution/calendar/local': Permission denied
du: cannot read directory `/home/user_3/.evolution/tasks/local': Permission denied
du: cannot read directory `/home/user_3/.gconfd': Permission denied
du: cannot read directory `/home/user_3/.nautilus/metafiles': Permission denied
du: cannot read directory `/home/user_3/.local': Permission denied
```

---

### Post by alphaniner on 2009-10-30
I get similar errors when I run the du command (du -sh /home/*) directly from the terminal:

```
du: cannot read directory `/home/testing/.config/gtk-2.0': Permission denied
du: cannot read directory `/home/testing/.config/autostart': Permission denied
du: cannot read directory `/home/testing/.config/brasero': Permission denied
du: cannot read directory `/home/testing/.config/compiz': Permission denied
du: cannot read directory `/home/testing/.config/chromium': Permission denied
du: cannot read directory `/home/testing/.pki': Permission denied
du: cannot access `/home/testing/.gvfs': Permission denied
du: cannot read directory `/home/testing/.mozilla': Permission denied
du: cannot read directory `/home/testing/.gnome2_private': Permission denied
du: cannot read directory `/home/testing/.compiz': Permission denied
du: cannot read directory `/home/testing/.adobe': Permission denied
du: cannot read directory `/home/testing/.macromedia': Permission denied
du: cannot read directory `/home/testing/.openoffice.org/3': Permission denied
du: cannot read directory `/home/testing/.dbus': Permission denied
du: cannot read directory `/home/testing/.hplip': Permission denied
du: cannot read directory `/home/testing/.local': Permission denied
du: cannot read directory `/home/testing/.gnupg': Permission denied
du: cannot read directory `/home/testing/.nautilus/metafiles': Permission denied
du: cannot read directory `/home/testing/.cache/compizconfig': Permission denied
du: cannot read directory `/home/testing/.cache/chromium': Permission denied
du: cannot read directory `/home/testing/.update-notifier': Permission denied
du: cannot read directory `/home/testing/.pulse': Permission denied
du: cannot read directory `/home/testing/.gconf': Permission denied
du: cannot read directory `/home/testing/.gegl-0.0': Permission denied
du: cannot read directory `/home/testing/.aptitude': Permission denied
du: cannot read directory `/home/testing/.ssh': Permission denied
du: cannot read directory `/home/testing/.thumbnails': Permission denied
du: cannot read directory `/home/testing/.gnome2': Permission denied
du: cannot read directory `/home/testing/.gconfd': Permission denied

```

And this is what should happen unless the command is run with root privileges.  Sorry, I don't think I can help.

---

