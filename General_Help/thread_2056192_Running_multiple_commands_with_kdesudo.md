---
title: "Running multiple commands with kdesudo???"
date: 2012-09-11
forum: General Help
---

### Post by Stonecold1995 on 2012-09-11
I'm writing a script and it will ask for the root password by using  kdesudo, but I'm having trouble finding out how to run multiple commands  as root. I want it to work something like this:

```
kdesudo command1 && command2
```

I feel like I've tried everything...  Any ideas?

---

### Post by Vaphell on 2012-09-11
kdesudo cmd1 && kdesudo cmd2 ?

---

### Post by Stonecold1995 on 2012-09-11
> **Vaphell said:**
> kdesudo cmd1 && kdesudo cmd2 ?

That asks for my password twice in a row.  I want to be able to run them *both* as root with one password.  I know it can be done with sudo (if the commands are run less than 15 minutes apart), but I'm lost in trying to find out how I can do it with kdesudo.

---

### Post by Epodx64 on 2012-09-11
maybe try "alt+f2" and try it from there?

---

### Post by Stonecold1995 on 2012-09-11
> **Epodx64 said:**
> maybe try "alt+f2" and try it from there?
I need it in a Bash script.

---

### Post by dodo3773 on 2012-09-11
I think you will probably either have to call the script from kdesudo like:
```

kdesudo bash scriptname.sh

```

or you will have to call a script from a script using the above. The reason you cannot figure out how to do it is that I think it is a limitation of the program (it cannot be done without hacking the source code of kdesudo). Don't bang your head against the wall for too long on this one. I am pretty sure that's it.

---

### Post by Vaphell on 2012-09-11
```
$ kdesudo rm /a/b/c || kdesudo rm /d/e/f
rm: cannot remove `/a/b/c': No such file or directory
rm: cannot remove `/d/e/f': No such file or directory
```

that requires only single kdesudo window on my 10.04

---

### Post by Stonecold1995 on 2012-09-11
> **dodo3773 said:**
> I think you will probably either have to call the script from kdesudo like:
```

kdesudo bash scriptname.sh

```

or you will have to call a script from a script using the above. The reason you cannot figure out how to do it is that I think it is a limitation of the program (it cannot be done without hacking the source code of kdesudo). Don't bang your head against the wall for too long on this one. I am pretty sure that's it.

So then how should I go about doing it with this?
```
#!/bin/bash

# small script to check if files under /boot changed
# Author: ju (ju at heisec dot de)
# Modified slightly by Stonecold
#
# License: GPLv2 or later

chkdir=/var/chkboot
chgfile=$chkdir/bootfiles-diff
bback=$chkdir/boot.tar
bdir=/boot

function update {
    rm -f $chgfile $bback
    tar -pscf $bback $bdir
}

function no_change {
    kdialog --warningyesno  "You have decided not to accept changes.  A backup of $bdir at its\nlast known good state can be found at $bback.\n\nWould you like to try to manually restore $bdir or leave it as it is?" --yes-label "Restore files" --no-label "Leave as is"
    if [ $? -eq 0 ]; then
        kdialog --msgbox "A backup of $bdir at its last known good state is located at $bback.\nTo prevent damage to $bdir, you must restore any changed files manually."
        (dolphin $chkdir &) 2>/dev/null
    fi
    exit 2
}

if [ -s $chgfile ]; then
    cat $chgfile | zenity --title "ALERT: Boot changes" --text-info --width 500 --height 300
    if [ $? -ne 0 ]; then
        no_change
    fi
    sudo -K
    kdesudo -d --comment "Enter your password to confirm changes." update
    if [ $? -eq 0 ]; then
        kdialog --title "Confirmation" --msgbox "Deleted $chgfile.\nA backup of $bdir has been created.\nChanges have been saved."
    else
        no_change
    fi
fi
```

I tried having it run a function ("update") but that didn't work.  Is there a way to run a script from within a script without having to create an extra .sh file?

> **Vaphell said:**
> ```
$ kdesudo rm /a/b/c || kdesudo rm /d/e/f
rm: cannot remove `/a/b/c': No such file or directory
rm: cannot remove `/d/e/f': No such file or directory
```

that requires only single kdesudo window on my 10.04

Didn't work.  It also tried to open two windows.

---

### Post by Epodx64 on 2012-09-11
kdesudo dolphin && kate 
opened dolphin then as soon as I closed dolphin Kate launched in su without prompting me for a second password.

---

### Post by Stonecold1995 on 2012-09-11
> **Epodx64 said:**
> kdesudo dolphin && kate 
opened dolphin then as soon as I closed dolphin Kate launched in su without prompting me for a second password.

Yes but Kate won't be run as root.  That's almost the same as:
```
kdesudo dolphin
kate
```

I want them BOTH to be run as root, not one run sequentially after the other. -_-

---

### Post by Epodx64 on 2012-09-11
and if you open Konsole and open two tabs (I guess you could do this with however many you wanted) 

Konsole Tab one

kdesudo dolphin

Konsole tap two

kdesudo kate

That works too only prompted be for the password on dolphin

---

### Post by Stonecold1995 on 2012-09-11
> **Epodx64 said:**
> and if you open Konsole and open two tabs (I guess you could do this with however many you wanted) 

Konsole Tab one

kdesudo dolphin

Konsole tap two

kdesudo kate

That works too only prompted be for the password on dolphin

It's not working for me...

---

### Post by Epodx64 on 2012-09-11
Are you inputing the 
kdesudo dolphin - in Konsole tab one
kdesudo kate - in console tab two 

execute dolphin first then switch tabs and execute kate

---

### Post by Stonecold1995 on 2012-09-11
> **Epodx64 said:**
> Are you inputing the 
kdesudo dolphin - in Konsole tab one
kdesudo kate - in console tab two 

execute dolphin first then switch tabs and execute kate

Yes.  Also, that won't help me anyways.  I need it in a script, not separate Konsole tabs...

---

### Post by Epodx64 on 2012-09-11
I can reduplicate it every single time make sure you're just using 1 konsole it wont work if you have 2 konsoles open just two tabs in one window

---

### Post by Epodx64 on 2012-09-11
You could probably pipe a command from konsole tab 1 to konsole tab 2 I don't how but I'm sure its possible

---

### Post by Stonecold1995 on 2012-09-11
> **Epodx64 said:**
> I can reduplicate it every single time make sure you're just using 1 konsole it wont work if you have 2 konsoles open just two tabs in one window

See this:
LQ: [http://videobam.com/XxDQP]("http://videobam.com/XxDQP")
HQ: [http://depositfiles.com/files/4423ylnc7]("http://depositfiles.com/files/4423ylnc7")

Also, not sure if it's relevant, but here's the output of "ls /tmp":
```
alex@kubuntu:~$ ls /tmp
akonadi-alex.ogx3lb  kdesudo-i10259-xauth  kdesudo-i11463-xauth  kdesudo-i12054-xauth  kdesudo-i13052-xauth  kdesudo-i13527-xauth  kdesudo-i16123-xauth  kdesudo-i32317-xauth  kdesudo-Ti6744-xauth  kdesudo-Ti7273-xauth  kdesudo-Z10654-xauth  pulse-PKdhtXMmr18n
gpg-NWm1Q7           kdesudo-i10668-xauth  kdesudo-i11542-xauth  kdesudo-i12175-xauth  kdesudo-i13137-xauth  kdesudo-i13611-xauth  kdesudo-i17935-xauth  kdesudo-Ti2264-xauth  kdesudo-Ti7133-xauth  kdesudo-Ti7284-xauth  ksocket-alex          pulse-s8INn79jAH0b
hsperfdata_root      kdesudo-i10803-xauth  kdesudo-i11729-xauth  kdesudo-i12250-xauth  kdesudo-i13244-xauth  kdesudo-i13686-xauth  kdesudo-i23169-xauth  kdesudo-Ti3672-xauth  kdesudo-Ti7209-xauth  kdesudo-Ti7968-xauth  ksocket-root          ssh-LnPCuAdF4109
kde-alex             kdesudo-i10877-xauth  kdesudo-i11804-xauth  kdesudo-i12759-xauth  kdesudo-i13332-xauth  kdesudo-i14759-xauth  kdesudo-i24464-xauth  kdesudo-Ti3684-xauth  kdesudo-Ti7220-xauth  kdesudo-Ti7977-xauth  libgksu-W2WP02        thumbnails
kde-root             kdesudo-i11383-xauth  kdesudo-i11977-xauth  kdesudo-i12836-xauth  kdesudo-i13413-xauth  kdesudo-i15672-xauth  kdesudo-i31334-xauth  kdesudo-Ti6666-xauth  kdesudo-Ti7245-xauth  kdesudo-Ti9319-xauth  orbit-alex
```
This has to be because of all the times I tried using kdesudo.  Does this have anything to do with it?

---

### Post by sienile on 2012-09-11
Here's the script to run 2 programs (example: gimp and firefox) at the same time. Just launch the script as root.

```
#!/bin/bash

gimp &
firefox
```

---

### Post by Epodx64 on 2012-09-11
> **Stonecold1995 said:**
> See this:
LQ: [http://videobam.com/XxDQP]("http://videobam.com/XxDQP")
HQ: [http://depositfiles.com/files/4423ylnc7]("http://depositfiles.com/files/4423ylnc7")

Also, not sure if it's relevant, but here's the output of "ls /tmp":
```
alex@kubuntu:~$ ls /tmp
akonadi-alex.ogx3lb  kdesudo-i10259-xauth  kdesudo-i11463-xauth  kdesudo-i12054-xauth  kdesudo-i13052-xauth  kdesudo-i13527-xauth  kdesudo-i16123-xauth  kdesudo-i32317-xauth  kdesudo-Ti6744-xauth  kdesudo-Ti7273-xauth  kdesudo-Z10654-xauth  pulse-PKdhtXMmr18n
gpg-NWm1Q7           kdesudo-i10668-xauth  kdesudo-i11542-xauth  kdesudo-i12175-xauth  kdesudo-i13137-xauth  kdesudo-i13611-xauth  kdesudo-i17935-xauth  kdesudo-Ti2264-xauth  kdesudo-Ti7133-xauth  kdesudo-Ti7284-xauth  ksocket-alex          pulse-s8INn79jAH0b
hsperfdata_root      kdesudo-i10803-xauth  kdesudo-i11729-xauth  kdesudo-i12250-xauth  kdesudo-i13244-xauth  kdesudo-i13686-xauth  kdesudo-i23169-xauth  kdesudo-Ti3672-xauth  kdesudo-Ti7209-xauth  kdesudo-Ti7968-xauth  ksocket-root          ssh-LnPCuAdF4109
kde-alex             kdesudo-i10877-xauth  kdesudo-i11804-xauth  kdesudo-i12759-xauth  kdesudo-i13332-xauth  kdesudo-i14759-xauth  kdesudo-i24464-xauth  kdesudo-Ti3684-xauth  kdesudo-Ti7220-xauth  kdesudo-Ti7977-xauth  libgksu-W2WP02        thumbnails
kde-root             kdesudo-i11383-xauth  kdesudo-i11977-xauth  kdesudo-i12836-xauth  kdesudo-i13413-xauth  kdesudo-i15672-xauth  kdesudo-i31334-xauth  kdesudo-Ti6666-xauth  kdesudo-Ti7245-xauth  kdesudo-Ti9319-xauth  orbit-alex
```
This has to be because of all the times I tried using kdesudo.  Does this have anything to do with it?

Yeah it's possible though mine looks pretty similar not quite as many but there's a bunch mine have an nnXXXX though.

---

### Post by Stonecold1995 on 2012-09-11
> **sienile said:**
> Here's the script to run 2 programs (example: gimp and firefox) at the same time. Just launch the script as root.

```
#!/bin/bash

gimp &
firefox
```

I know how to run a script as root...  The problem is that I have a script already, and there are two commands that must be run as root, but with only one kdesudo, like this:
```
#!/bin/bash

if [ blah ]; then
   kdesudo command1 && command2
fi

```
I want the script to only ask for the password if "blah" is true, and only ask once, but run the two commands.  I know it can work with sudo, because it caches the credentials for 15 minutes, but I don't know how to do that with kdesudo.

---

### Post by Epodx64 on 2012-09-11
alright try this run
kdesudo dolphin | kdesudo kate

that will prompt you twice for a password but then run

sudo kdesudo dolphin | kdesudo kate

Brings them both up at the same time in root.

---

### Post by Epodx64 on 2012-09-11
pretty much run any sudo command sudo cat or something then run
sudo kdesudo kdesudo dolphin | kdesudo kate

works every single time both windows at once no password prompt
so i guess all you'd really need to do then is hit "alt+f2" type in kdesudo konsole

when your in root konsole
kdesude dolphin | kdesudo kate

one password prompt not perfect but it works.

---

### Post by Epodx64 on 2012-09-11
ok so alt+f2 then kdesudo konsole
then just type 

dolphin | kate

there's no need for the kdesudo since your already root.

---

### Post by Stonecold1995 on 2012-09-11
None of these are working for me!  Plus, I need to be able to put this in a script so it asks *only* once, and runs two commands.

The only way I can think of would be to use "kdialog --inputbox" and then send the result to two sudos, but that seems really insecure.

---

### Post by Stonecold1995 on 2012-09-11
> **Epodx64 said:**
> ok so alt+f2 then kdesudo konsole
then just type 

dolphin | kate

there's no need for the kdesudo since your already root.

I cannot do that.  I need to be able to put this *in a script*, and I don't have the option to have the script open Konsole and then tell me to put in all the commands manually...

Is there some way to do something like this (or an equivalent of sudo -v for kdesudo)?
```
kdesudo "sudo -v"
sudo command1
sudo commadn2
```

---

### Post by Epodx64 on 2012-09-11
well I the easiest way I've gotten it to work is 
sudo ls /home && kdesudo dolphin | kdesudo kate

---

### Post by Stonecold1995 on 2012-09-11
> **Epodx64 said:**
> well I the easiest way I've gotten it to work is 
sudo ls /home && kdesudo dolphin | kdesudo kate
That didn't work.......

Plus, I need the script to ask for the password once with *kdesudo*.  If that's not possible just tell me but it feels like you're dragging me through a bunch of "solutions" that aren't relevant to this.

If that's not possible, then can someone help me with a way to use "kdialog --inputbox" to get my password and then send it to sudo with "sudo -S" (or however that works)?

This seems like an awful amount of trouble just to get kdesudo to run two commands...

---

### Post by dodo3773 on 2012-09-11
I don't see how you are still confused about this. Create a script:

```

#!/bin/bash
blahblahblah

```

run command like this 

```

kdesudo /path/to/script.sh

```

put the second part in an alias etc.. Or create another script like this:
```

#!/bin/bash
kdesudo /path/to/script.sh

```


To answer your question:
> 
Is there a way to run a script from within a script without having to create an extra .sh file?


I really don't think so. I thought about this a long time ago and I think in the end the answer was no not really.

---

### Post by Stonecold1995 on 2012-09-11
OK.  So if this is the current script that *isn't* working:
```
#!/bin/bash

# small script to check if files under /boot changed
# Author: ju (ju at heisec dot de)
# Modified slightly by Stonecold
#
# License: GPLv2 or later

chkdir=/var/chkboot
chgfile=$chkdir/bootfiles-diff
bback=$chkdir/boot.tar
bdir=/boot

[b]function update {
    rm -f $chgfile $bback
    tar -pscf $bback $bdir
}[/b]

function no_change {
    kdialog --warningyesno  "You have decided not to accept changes.  A backup of $bdir at its\nlast known good state can be found at $bback.\n\nWould you like to try to manually restore $bdir or leave it as it is?" --yes-label "Restore files" --no-label "Leave as is"
    if [ $? -eq 0 ]; then
        kdialog --msgbox "A backup of $bdir at its last known good state is located at $bback.\nTo prevent damage to $bdir, you must restore any changed files manually."
        (dolphin $chkdir &) 2>/dev/null
    fi
    exit 2
}

if [ -s $chgfile ]; then
    cat $chgfile | zenity --title "ALERT: Boot changes" --text-info --width 500 --height 300
    if [ $? -ne 0 ]; then
        no_change
    fi
    sudo -K
    kdesudo -d --comment "Enter your password to confirm changes." **update**
    if [ $? -eq 0 ]; then
        kdialog --title "Confirmation" --msgbox "Deleted $chgfile.\nA backup of $bdir has been created.\nChanges have been saved."
    else
        no_change
    fi
fi
```

This is the solution?
```
#!/bin/bash

# small script to check if files under /boot changed
# Author: ju (ju at heisec dot de)
# Modified slightly by Stonecold
#
# License: GPLv2 or later

chkdir=/var/chkboot
chgfile=$chkdir/bootfiles-diff
bback=$chkdir/boot.tar
bdir=/boot

function no_change {
    kdialog --warningyesno  "You have decided not to accept changes.  A backup of $bdir at its\nlast known good state can be found at $bback.\n\nWould you like to try to manually restore $bdir or leave it as it is?" --yes-label "Restore files" --no-label "Leave as is"
    if [ $? -eq 0 ]; then
        kdialog --msgbox "A backup of $bdir at its last known good state is located at $bback.\nTo prevent damage to $bdir, you must restore any changed files manually."
        (dolphin $chkdir &) 2>/dev/null
    fi
    exit 2
}

if [ -s $chgfile ]; then
    cat $chgfile | zenity --title "ALERT: Boot changes" --text-info --width 500 --height 300
    if [ $? -ne 0 ]; then
        no_change
    fi
    [b]tmp=$(mktemp)
    echo '#!/bin/bash'"

rm -f $chgfile $bback
tar -pscf $bback $bdir
exit 0" > $tmp
    chmod +x $tmp[/b]
    sudo -K
    kdesudo -d --comment "Enter your password to confirm changes." **$tmp**
    if [ $? -eq 0 ]; then
        kdialog --title "Confirmation" --msgbox "Deleted $chgfile.\nA backup of $bdir has been created.\nChanges have been saved."
    else
        no_change
    fi
    **rm -f $tmp**
fi
```
And there's no simpler way to do this?

---

