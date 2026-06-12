---
title: "Ubuntu server not booting"
date: 2011-01-28
forum: General Help
---

### Post by mebunto on 2011-01-28
[FONT="Arial"]HELP!!!

I changed the first line of /etc/fstab in an attempt to get rid of  an annoying message "mount: unknown filesystem type 'static'"

All I did was put a "#" on the first line .... changing the original from:
[/FONT]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

to:

#
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

[FONT="Arial"]I have tried desperately to get to the file system so that I can edit that first line in fstab out but nothing works and the file system comes up as read only ... 

what did I do wrong?

how can I fix it? [/FONT]

---

### Post by mebunto on 2011-01-28
Can anyone help with this?  I don't want to trash the machine, because weeks have hard work have gone into getting it to where it is now ....
Thanks

---

### Post by mebunto on 2011-01-30
booted from a CD and went into rescue mode.  Copied a saved version of fstab over the bad one and rebooted.

I still don't understand why a line that is commented out makes a difference perhaps someone might explain?

---

### Post by asmoore82 on 2011-01-30
What editor did you use to make the change?

---

### Post by mebunto on 2011-01-31
Hi - thanks for the reply - I used XML copy editor to make the changes.

---

### Post by asmoore82 on 2011-02-07
It seems that XML Copy Editor places a Byte Order Mark (BOM) at the beginning of files.
This is safely ignored by `cat` but of course is visible with `hexdump`.
It is also pointed out by the `file` utility:
```
**cat fstab | head -n 3**
#
# /etc/fstab: static file system information.
#
**hd fstab | head -n 3**
00000000  [COLOR="Red"]ef bb bf[/COLOR] 23 0a 23 20 2f  65 74 63 2f 66 73 74 61  |[COLOR="Red"]...[/COLOR]#.# /etc/fsta|
00000010  62 3a 20 73 74 61 74 69  63 20 66 69 6c 65 20 73  |b: static file s|
00000020  79 73 74 65 6d 20 69 6e  66 6f 72 6d 61 74 69 6f  |ystem informatio|
**file fstab**
fstab: UTF-8 Unicode [COLOR="Red"](with BOM)[/COLOR] English text
```

One possible fix would be to trim these first few bytes off of
the file with the `tail` command:
```
[B]cd etc
file fstab [/B]
fstab: UTF-8 Unicode [COLOR="Red"](with BOM)[/COLOR] English text
[B]cat fstab | tail -c +4 > /tmp/fstab
file /tmp/fstab[/B]
/tmp/fstab: [COLOR="Red"]ASCII English text[/COLOR]
**sudo mv /tmp/fstab fstab**
```

---

### Post by mebunto on 2011-02-15
Asmoore82 - much appreciated!  Yes indeed my fstab had the three leading characters.  I'll post back if it makes a difference or not.

Thanks also for some new commands that I can add to my limited repetoir

Mebunto

---

### Post by mebunto on 2011-02-17
Another footnote ... it does seem that whatever processes fstab is very sensitive to spurious characters both at the beginning and end of lines.  I started fstab from scratch and ensured that no extra characters were there and that gives an error-free boot.

---

