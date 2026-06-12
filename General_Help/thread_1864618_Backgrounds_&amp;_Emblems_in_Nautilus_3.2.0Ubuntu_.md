---
title: "Backgrounds &amp; Emblems in Nautilus 3.2.0/Ubuntu 11.10"
date: 2011-10-19
forum: General Help
---

### Post by Trilby on 2011-10-19
I've just done a fresh install of Ubuntu 11.10 with Gnome Shell as my desktop environment. I normally set the main region of Nautilus (ie, the bit where icons appear) to black. However, I can no longer find the *Backgrounds and Emblems* options which allow(ed) me to do this.

Does anyone know how to find them or if a similar effect can be achieved through the Terminal?

Many thanks,
Trilby

---

### Post by Dark Slipstream on 2011-10-19
I am also experiencing this.

I recently (successfully) upgraded from 11.04 to 11.10 and the "Backgrounds and Emblems" option has been removed. As well, the "Emblems" tab under folder properties is also gone.

---

### Post by wowotiel on 2011-10-21
> **Dark Slipstream said:**
> I am also experiencing this.

I recently (successfully) upgraded from 11.04 to 11.10 and the "Backgrounds and Emblems" option has been removed. As well, the "Emblems" tab under folder properties is also gone.
After a clean install Ubuntu 11.10 (2D) I have also no more a tab for "Eblems" under folder properties.
How can I get back this tab.
Is this bug allready rapported ?

---

### Post by philinux on 2011-10-21
Technically its not a bug but I think it has been reported as one.

The feature is not available yet in the latest version of nautilus. I suspect a nautilus update at some point will bring it back.

---

### Post by wowotiel on 2011-10-21
> **philinux said:**
> Technically its not a bug but I think it has been reported as one.

The feature is not available yet in the latest version of nautilus. I suspect a nautilus update at some point will bring it back.
Thanks for the explanation.

---

### Post by kvgkvg on 2011-10-23
I'm missing the emblems option too. They were pretty useful for me..

---

### Post by krennecke on 2011-10-25
Not sure but this [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/841332](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/841332) might be related or arrive at being related when resolved.

[edit] Since the above entry concerns emblems for Ubuntu One specifically, I opened a fresh one for the generic emblems UI in nautilus here [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/881864](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/881864)

---

### Post by BioTeX on 2011-11-05
Comments in the bug report seem to indicate it was intentionally removed.  Hopefully the developers will reconsider and bring it back.

Meanwhile, there must be some command-line way to access the functionality.  I can still see the emblems that I set previously, so the functionality must still be there under the hood.

---

### Post by Trilby on 2011-11-07
> **BioTeX said:**
> Comments in the bug report seem to indicate it was intentionally removed.  Hopefully the developers will reconsider and bring it back.

Meanwhile, there must be some command-line way to access the functionality.  I can still see the emblems that I set previously, so the functionality must still be there under the hood.

Indeed.
Does any one know if there same applies for the backgrounds settings?

---

### Post by Germar on 2011-11-10
Hey,

I've hacked a script to change emblems with nautilus-actions. Hope you like it

```

#!/bin/bash

# change emblem's in Nautilus with nautilus-actions
# add a new action in nautilus-actions-config-tool with
# Path /path/to/this/script.sh
# Parameter %F
# Nautilus has to be reload to show the emblem's.
# So you have to press F5 after changes.

# Germar Reitze <germar.reitze(AT)gmx.de> Nov 2011

emblem="art cool danger default desktop development documents downloads draft favorite important mail marketing money new nowrite \
ohno OK package people personal photos pictures plan presentation readonly shared sound symbolic-link system \
ubuntuone-unsynchronized ubuntuone-updating unreadable urgent videos web"
#debug=1

# ask which emblem to add
pick_emblem() {
   emblem_list=""
   for i in $emblem; do
    if [ $(echo "$@" | grep -c $i) -eq 1 ]; then
       emblem_list="$emblem_list TRUE $i"
    else
       emblem_list="$emblem_list FALSE $i"
    fi
   done
   if [ "$multiple_files" == "true" ]; then
    text="Which embleme to add to files?\nDon't forget to press [F5] after OK"
   else
    text="Which embleme to set?\nDon't forget to press [F5] after OK"
   fi
   zenity  --list  --text "$text" --checklist  --column "Pick" --column "Emblem" $emblem_list --separator=" " --height=700 --width=300
   return $?
}

# do we already have emblem's?
get_used_emblem() {
   a=$(gvfs-info "$1" -a metadata::emblems)
   b=${a#*[}
   b=${b%]*}
   echo "$b" | sed -e 's/,//g'
}

# emblem won't show without
set_icon_view_auto_layout() {
   if [ $(gvfs-info "$1" -a metadata::nautilus-icon-view-auto-layout | grep -c true) -lt 1 ]; then
    [ $debug ] && echo "SET: metadata::nautilus-icon-view-auto-layout true"
    gvfs-set-attribute -t string "$1" metadata::nautilus-icon-view-auto-layout true
    return $?
   else
    [ $debug ] && echo "metadata::nautilus-icon-view-auto-layout already set"
   fi
}

set_emblem() {
   file="$1"
   shift
   gvfs-set-attribute -t stringv "$file" metadata::emblems $@
   return $?
}

report_error() {
   zenity --error --text "Failed in $1"
}



multiple_files=false
if [ $# -gt 1 ]; then
   multiple_files=true
fi

if [ "$multiple_files" == "true" ]; then
   add_emblem=$(pick_emblem)
   err=$?
   if [ $err -gt 0 ]; then
        [ $debug ] && echo "cancel"
        exit 1
   fi
   [ $debug ] && echo "embleme to add: $add_emblem"

   # process every file separate
   while [ $# -gt 0 ]; do
    used_emblem=$(get_used_emblem "$1")
    err=$?
    [ $err -gt 0 ] && report_error "$1" && exit 1
    emblem_list=""
    for i in $emblem; do
       if [ $(echo "$used_emblem $add_emblem" | grep -c $i) -ne 0 ]; then
        emblem_list="$emblem_list $i"
       fi
    done
    set_icon_view_auto_layout "$1"
    err=$?
        [ $err -gt 0 ] && report_error "$1" && exit 1

    if [ "$emblem_list" != "" ]; then
       [ $debug ] && echo "$1: $emblem_list"
       set_emblem "$1" $emblem_list
       err=$?
           [ $err -gt 0 ] && report_error "$1" && exit 1
    fi
    shift
   done
else
   # we only have one file
   add_emblem=$(pick_emblem $(get_used_emblem "$1") )
   err=$?
   if [ $err -gt 0 ]; then
        [ $debug ] && echo "cancel"
        exit 1
   fi
   [ $debug ] && echo "embleme to add: $add_emblem"

   set_icon_view_auto_layout "$1"
   err=$?
   [ $err -gt 0 ] && report_error "$1" && exit 1

   if [ "$add_emblem" != "" ]; then
    [ $debug ] && echo "$1: $add_emblem"
    set_emblem "$1" $add_emblem
    err=$?
   else
    [ $debug ] && echo "$1: delete emblem"
    set_emblem "$1" \"\"
    err=$?
   fi
   [ $err -gt 0 ] && report_error "$1" && exit 1
fi

```BTW if nautilus-actions isn't working for you either on 11.10 you can download the [3.1.4-1 build here]("https://launchpad.net/ubuntu/+source/nautilus-actions/3.1.4-1") and install with ```
sudo dpkg -i nautilus-actions_3.1.4-1_i386.deb
```That works for me.

Best regards,
Germar

---

### Post by Germar on 2011-12-12
Hey,

due to a missing return-value in two functions there was an error preventing to set multiple emblems and remove them. Strange. With activated debug everything was working fine because the debug-function itself gave a positive return-value.

---

### Post by Germar on 2011-12-12
added function to remove emblems in multiple files and using '-t unset' to remove instead of [FONT=monospace]empty string[/FONT]

---

### Post by Germar on 2011-12-13
added automatic refresh of Nautilus.

you have to download and install liblineak and lineakd. You find the package that fit for your platform [here]("https://launchpad.net/ubuntu/oneiric/+source/lineakd/+builds")

```

cd ~/Downloads
sudo dpkg -i liblineak*.deb
sudo dpkg -i lineakd*.deb
```emblem.sh
```
#!/bin/bash

# change emblem's in Nautilus with nautilus-actions
# add a new action in nautilus-actions-config-tool with
# Path /path/to/this/script.sh
# Parameter %F
# Nautilus has to be reload to show the emblem's.
# So you have to press F5 after changes.

# Germar Reitze <germar.reitze(AT)gmx.de> Nov 2011
# 2011-12-12 Germar Reitze - bugfix and new function to remove emblems in multiple files
# 2011-12-14 Germar Reitze - automatic refresh Nautilus after change

emblem="art cool danger default desktop development documents downloads draft favorite important mail marketing money new nowrite \
ohno OK package people personal photos pictures plan presentation readonly shared sound symbolic-link system \
ubuntuone-unsynchronized ubuntuone-updating unreadable urgent videos web"
#debug=1
xsendkeycode=$(which xsendkeycode)

# ask which emblem to add
pick_emblem() {
   emblem_list=""
   for i in $emblem; do
        if [ $(echo "$@" | grep -c $i) -eq 1 ]; then
           emblem_list="$emblem_list TRUE $i"
        else
           emblem_list="$emblem_list FALSE $i"
        fi
   done
   if [ "$multiple_files" == "true" ]; then
        text="Which embleme to add to files?"
        emblem_list="FALSE DELETE_ALL_EMBLEMS $emblem_list"
   else
        text="Which embleme to set?"
   fi
   # if lineakd is not installed remind to press F5
   if ! [ -x "$xsendkeycode" ]; then
      text="$text \nDon't forget to press [F5] after OK"
   fi
   zenity  --list  --text "$text" --checklist  --column "Pick" --column "Emblem" $emblem_list --separator=" " --height=700 --width=300
   return $?
}

# do we already have emblem's?
get_used_emblem() {
   a=$(gvfs-info "$1" -a metadata::emblems)
   err=$?
   b=${a#*[}
   b=${b%]*}
   echo "$b" | sed -e 's/,//g'
   return $err
}

# emblem won't show without
set_icon_view_auto_layout() {
   if [ $(gvfs-info "$1" -a metadata::nautilus-icon-view-auto-layout | grep -c true) -lt 1 ]; then
        [ $debug ] && echo "SET: metadata::nautilus-icon-view-auto-layout true"
        gvfs-set-attribute -t string "$1" metadata::nautilus-icon-view-auto-layout true
        return $?
   else
        [ $debug ] && echo "metadata::nautilus-icon-view-auto-layout already set"
        return 0
   fi
}

set_emblem() {
   file="$1"
   shift
   gvfs-set-attribute -t stringv "$file" metadata::emblems $@
   return $?
}

del_emblem() {
   gvfs-set-attribute -t unset "$1" metadata::emblems
   return $?
}

report_error() {
   zenity --error --text "Failed in $1"
}



multiple_files=false
if [ $# -gt 1 ]; then
   multiple_files=true
fi

if [ "$multiple_files" == "true" ]; then
   add_emblem=$(pick_emblem)
   err=$?
   if [ $err -gt 0 ]; then
        [ $debug ] && echo "cancel"
        exit 1
   fi
   [ $debug ] && echo "embleme to add: $add_emblem"

   # process every file separate
   while [ $# -gt 0 ]; do
        if [ $(echo "$add_emblem" | grep -c DELETE_ALL_EMBLEMS) -eq 1 ]; then
           [ $debug ] && echo "$1: delete emblems"
           del_emblem "$1"
           err=$?
           [ $err -gt 0 ] && report_error "$1" && exit 1
        else
           used_emblem=$(get_used_emblem "$1")
           err=$?
           [ $err -gt 0 ] && report_error "$1" && exit 1
           emblem_list=""
           for i in $emblem; do
                if [ $(echo "$used_emblem $add_emblem" | grep -c $i) -ne 0 ]; then
                   emblem_list="$emblem_list $i"
                fi
           done
           set_icon_view_auto_layout "$1"
           err=$?
           [ $err -gt 0 ] && report_error "$1" && exit 1

           if [ "$emblem_list" != "" ]; then
                [ $debug ] && echo "$1: $emblem_list"
                set_emblem "$1" $emblem_list
                err=$?
                [ $err -gt 0 ] && report_error "$1" && exit 1
           fi
        fi
        shift
   done
else
   # we only have one file
   add_emblem=$(pick_emblem $(get_used_emblem "$1") )
   err=$?
   if [ $err -gt 0 ]; then
        [ $debug ] && echo "cancel"
        exit 1
   fi
   [ $debug ] && echo "embleme to add: $add_emblem"

   set_icon_view_auto_layout "$1"
   err=$?
   [ $err -gt 0 ] && report_error "$1" && exit 1

   if [ "$add_emblem" != "" ]; then
        [ $debug ] && echo "$1: $add_emblem"
        set_emblem "$1" $add_emblem
        err=$?
   else
        [ $debug ] && echo "$1: delete emblem"
        del_emblem "$1"
        err=$?
   fi
   [ $err -gt 0 ] && report_error "$1" && exit 1
fi

# refresh Nautilus if lineakd is installed
if [ -x "$xsendkeycode" ]; then
   $xsendkeycode 71 1
   $xsendkeycode 71 0
fi
```

---

### Post by Frogs Hair on 2011-12-13
[http://www.webupd8.org/2011/12/how-to-manually-add-emblems-in-nautilus.html](http://www.webupd8.org/2011/12/how-to-manually-add-emblems-in-nautilus.html)

---

