---
title: "GRUB2 and previewing the GRUB_INIT_TUNE"
date: 2011-04-26
forum: General Help
---

### Post by Mozai on 2011-04-26
Installed Grub2 for... well, I forgot the reason.  Documentation is sparse, and the official GRUB2 wiki has been down for I don't know how long.  The Ubuntu wiki seems to be the next-best place for documentation on GRUB2, which is why I'm saying (announcing?) this here.

There's a feature of a start-up sound, a little something to be pushed through the squeaker before showing the menu of OSes to boot with.  Set 'GRUB_INIT_TUNE' in /etc/default/grub and then 'update-grub2'.  The default is just a single beep.  There's a 'ninendo mario' tune that you can find easy enough with Google, and I saw a 'speilberg's aliens greeting tune' elsewhere in Ubuntuforums.org.

I wanted to test GRUB_INIT_TUNE values without needing to reboot my machine over and over again.  I figured this out tonight:

```
#!/bin/dash
tune="$*";
if [ ! "$tune" ];then echo "Usage: $0 tempo freq dur (freq dur freq dur...)" >&2;exit 1;fi
f="";tmpdir=$(mktemp -d);for d in $tune;do if [ ! "$t" ];then t=$d;elif [ ! "$f" ];then f=$d;
else sox -U -r 8000 -n -t raw - synth $(echo "$d*(60/$t)"|bc -l) sine $f >>$tmpdir/grubtune.ul;f="";fi;done;
sox -c1 -r 8000 $tmpdir/grubtune.ul $tmpdir/grubtune.au;play -q $tmpdir/grubtune.au;/bin/rm -r $tmpdir

```

I put this into /usr/local/bin/grub-playtune, and
[FONT="monospace"]$ grub-playtune 480 900 2 1000 2 800 2 400 2 600 3[/FONT]
gives me the Close-Encounters greeting tune similar to what I should hear if I used those numbers in GRUB_INIT_TUNE.

I think this is useful enough to add to the Ubuntu documentation for Grub2... or after some fool-proofing, d'you think this tiny script would be worth adding to the Ubuntu grub-common package?  (er, how do I submit to a package maintaner?  The package's 'Maintainer:' field just has a generic 'ubuntu-devel-discuss' mailing list for contact information.  I guess I should notify Robbie Williamson since bootloaders are "plumbing"?

---

### Post by rduke15 on 2011-05-01
Thanks a lot! This is a great tip.

Since I wanted to understand what your script really did and how, I reformatted it, and then changed a few details to my taste. In case anyone else is interested in a longer but more readable version, here it is:

```
#!/bin/dash

if [ $# -lt 3 ]; then
    echo "Usage: $0 tempo freq dur [freq dur freq dur...]" >&2
    exit 1
fi

tempo=$1; shift

tmpdir=$(mktemp -d)

while [ -n "$*" ]; do
    freq=$1; shift
    dur=$1;  shift
    dur=$(echo "$dur*(60/$tempo)"|bc -l)
    sox -U -r 8000 -n -t raw - synth $dur sine $freq >>$tmpdir/grubtune.ul
done

play -q -c1 -r 8000 $tmpdir/grubtune.ul

rm -r $tmpdir

```

(Note I suppressed the raw to .al conversion. Not sure why it was there.)

---

