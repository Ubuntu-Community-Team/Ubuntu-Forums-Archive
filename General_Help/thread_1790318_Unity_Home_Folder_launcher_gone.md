---
title: "Unity Home Folder launcher gone"
date: 2011-06-24
forum: General Help
---

### Post by Paulgirardin on 2011-06-24
After following the procedure on this page:

[http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity](http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity)

to  add an updated quicklist to the Home folder launcher in Unity,I have lost the icon completely. This is the script the tweak runs:

```
#!/bin/bash
# tabsize: 4, encoding: utf8
#
# © 2011 con-f-use@gmx.net. Use under the MIT license:
#     http://www.opensource.org/licenses/mit-license.php
# 
# CONTRIBUTORS: Chris Druif <cyber.druif@gmail.com>
# 
# This script updates the unity quicklist menu for nautilus to contain the user
# bookmarks. The updates will have efect after unity is restarted (either on
# the next login or by invoking 'unity --replace').

# location of template and unity bar launchers
nautempl="/usr/share/applications/nautilus-home.desktop"
target="$HOME/.local/share/applications/nautilus-home.desktop"
bookmarks="$HOME/.gtk-bookmarks"

# backup if file allready exists
if [ -e "$target" ]; then
    echo "Creating backup of: $target."
    mv -n "$target" "$target.bak"
fi

# copy template
cp "$nautempl" "$target"

sed -i "s/\(OnlyShowIn=GNOME;\)/\1Unity;/" "$target"

echo "X-Ayatana-Desktop-Shortcuts=" >> $target

bmcount=0
while read bmline; do
    bmcount=$(($bmcount+1))     # number of current bookmark
    bmname=${bmline#*\ }        # name of the bookmark
    bmpath=${bmline%%\ *}       # path the bookmark leads to
    # deal with bookmarks that have no name
    if [ "$bmname" = "$bmpath" ]; then
        bmname=${bmpath##*/}
    fi
    # extend shortcut list with current bookmark
    sed -i "s/\(X-Ayatana-Desktop-Shortcuts=.*\)/\1Scg${bmcount};/" "$target"
    # write bookmark information
    cat - >> "$target" <<EOF

[Scg$bmcount Shortcut Group]
Name=$bmname
Exec=nautilus $bmpath
OnlyShowIn=Unity
EOF
done < "$bookmarks"

# Add a root file manager entry
sed -i "s/\(X-Ayatana-Desktop-Shortcuts=.*\)/\1RootFM;/" "$target"
cat - >> "$target" <<EOF

[RootFM Shortcut Group]
Name=ROOT
Exec=gksudo nautilus
OnlyShowIn=Unity
EOF

exit 0
```

Can anyone suggest how I can get the home folder launcher back?

---

### Post by heyandy889 on 2011-06-24
Sorry, I don't have 11.04 in front of me. o'_'o Maybe try right-clicking on the fat panel? Is there some sort of "Add Shortcut" option? I know that your home folder is located at /home/me, where "me" is you- well, you get the picture!

---

### Post by Paulgirardin on 2011-06-24
Not sure what the "fat panel" is.

It is the Home Folder launcher that I need to restore.The Home Folder still exists.
I can start file manager and pin it to the launch panel but it doesn't have the quicklist the home folder launcher had.

---

### Post by Paulgirardin on 2011-06-24
I ran the command: "unity --reset-icons" and recreated my custom launchers

---

### Post by mjbennison on 2011-10-31
You could also have just dragged the 'home folder' entry in /usr/share/applications back to the unity dock.

What I have found is that any trailing spaces on lines in the quick list configuration cause problems.

---

