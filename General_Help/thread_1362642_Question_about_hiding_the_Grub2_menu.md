---
title: "Question about hiding the Grub2 menu"
date: 2009-12-23
forum: General Help
---

### Post by empty_spaces on 2009-12-23
I usually follow this guide when I edit Grub2.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[B]This guide mentions that the Grub2 menu may not be hidden if other OS's are present.
[/B]
[B]Can anyone confirm if this is still true or if it's possible to hide grub even with other OS's present?
[/B]
Here is the relevant quote from the link above.

> GRUB_HIDDEN_TIMEOUT=0

    * The menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    * The setting may depend on the presence of other operating systems.
          o Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
            According to some of the GRUB 2 developers, in Ubuntu the menu will not be hidden any time there are other OSs found by os-prober, regardless of this setting. This is in keeping with the Ubuntu Team's goal towards booting: [https://wiki.ubuntu.com/DesktopExper...pec#Bootloader](https://wiki.ubuntu.com/DesktopExper...pec#Bootloader)
          o No other OS Detected: The menu will be hidden.

---

### Post by john newbuntu on 2009-12-23
That is true, unless of course you tamper with the /etc/grub.d/30_os-prober.  Setting GRUB_TIMEOUT to 0 followed by a sudo update-grub will help.

---

### Post by empty_spaces on 2009-12-24
Thanks. Will try and play around with it when I get a chance.

---

### Post by meierfra. on 2009-12-24
You might try this: 

Use "GRUB_HIDDEN_TIMEOUT=10" (or however long you want the timeout to be) in /etc/default/grub    and remove the check for other OS's  by  placing a "#" in the front  of the two lines in /etc/grub.d/30_os-prober I marked in red:

```
adjust_timeout () {
[COLOR="Red"]#  if [ "x${found_other_os}" = "x" ] ; then[/COLOR]
    if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
	verbose=
      else
	verbose=" --verbose"
      fi

      if [ "x${GRUB_HIDDEN_TIMEOUT}" = "x0" ] ; then
	cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF
      else
	cat << EOF
if [ \${timeout} != -1 ]; then
  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
    set timeout=0
  fi
fi
EOF
      fi
    fi
 [COLOR="Red"]# fi[/COLOR]
}


```

Of course run "sudo update-grub" afterwards to generate the new "grub.cfg"

---

### Post by PARO on 2010-01-20
Great! Worked for me. I can now keep grub hidden, or hold shift to see a menu with my other OSs. Thanks meierfra!

---

### Post by meierfra. on 2010-01-21
> Worked for me.
Good. Have fun with all your OS's

---

