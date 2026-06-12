---
title: "How to correct this error?"
date: 2012-01-14
forum: General Help
---

### Post by tiger63 on 2012-01-14
I keep getting an error when trying to customize grub2 via the grub customizer program and I noticed I get the same error when trying to update grub via the terminal.  

```
~:sudo update-grub
/etc/default/grub: 35: Syntax error: EOF in backquote substitution

```

I haven't changed the /etc/default/grub file and examining it gives me no clue as to why I keep getting this error.  In any event, here it is:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash plymouth:debug=file:/var/log" > /plymouth-debug.log plymouth"
GRUB_CMDLINE_LINUX="splash"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

I can't seem to get plymouth to work and I think this error may be the culprit.

---

### Post by WasMeHere on 2012-01-14
> **tiger63 said:**
> I keep getting an error when trying to customize grub2 via the grub customizer program and I noticed I get the same error when trying to update grub via the terminal.  

```
~:sudo update-grub
/etc/default/grub: 35: Syntax error: EOF in backquote substitution

```
...
```
# If you change this file, run 'update-grub' afterwards to update
...
[COLOR="Red"]GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"[/COLOR]
...
```

I can't seem to get plymouth to work and I think this error may be the culprit.

The only backquotes I find is in the [COLOR="Red"]red[/COLOR] line

What happens if you change that line into a comment line with # and and add a simple line?
```
# GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_DISTRIBUTOR="Ubuntu"
```

---

### Post by tiger63 on 2012-01-14
> **Olle Wiklund said:**
> The only backquotes I find is in the [COLOR="Red"]red[/COLOR] line

What happens if you change that line into a comment line with # and and add a simple line?
```
# GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_DISTRIBUTOR="Ubuntu"
```

After making the changes, the error persists, only now with one more line...
```
~:sudo update-grub
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
```

---

### Post by ajgreeny on 2012-01-14
I am not sure if the error ```
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
```suggests that there is a problem with line 35 in your file, but if so it may be that there is an empty line at the end, ie EOF in the error, and as far as I can see, your file shows only 34 lines.

My file of the same name does not have an empty line at the end, so I wonder - - ?

---

### Post by tiger63 on 2012-01-14
> **ajgreeny said:**
> I am not sure if the error ```
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
```suggests that there is a problem with line 35 in your file, but if so it may be that there is an empty line at the end, ie EOF in the error, and as far as I can see, your file shows only 34 lines.

My file of the same name does not have an empty line at the end, so I wonder - - ?

There was an empty line at the end.  Deleting that line and saving the file, however, did not eliminate the error, unfortunately.

---

### Post by WasMeHere on 2012-01-14
OK, you have sorted out the first guesses. What about this one:

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="640x480"

```

Maybe you can check if the GFXMODE works: at the grub menu

1. press ***c*** (to get a command prompt)
2. type ***vbeinfo*** and press Enter
3. or type ***vbeinfo 640x480*** and press Enter

This should show if the specified graphics mode is supported by your system. If not, select another one, that is listed by vbeinfo!

---

### Post by bogan on 2012-01-14
Hi!, **tiger63**,
You Posted: > I keep getting an error when trying to customize grub2 via the grub  customizer program and I noticed I get the same error when trying to  update grub via the terminal.  ```


     Code:
     ~:sudo update-grub /etc/default/grub: 35: Syntax error: EOF in backquote substitution 

```The " 35:" surely means the error was located in line 35 of your file, though it depends how you count the lines at start and finish whether there is a line 35 in the code you Posted
The end of my /etc/default/grub file, after completely running Grub Customizer looks like this:```
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
[COLOR=Green]# Edited: This would be line 35: and the end of file before running GC, counting from 1, not zero.#[/COLOR]
[COLOR=Red]
export GRUB_COLOR_NORMAL="blue/black"
export GRUB_COLOR_HIGHLIGHT="red/black"
export GRUB_MENU_PICTURE="/usr/share/images/grub/Moraine_Lake_17092005.tga"
GRUB_SAVEDEFAULT="false"[/COLOR]
``` Green line added now by me; Red lines added by GC.

There should be a backup copy saved by GC and you could try renaming both files and rebooting and running update-grub. 

 Chao!, **bogan**.

---

### Post by bogan on 2012-01-14
Hi!, **tiger63**,

I see the 35 point had already been noted, How about this one:?
 Are you looking at the right /etc/default/grub file??

If you have a multi ubuntu installation the operative file Grub looks at would normally be the one in the first ( ie the top ) grub menu entry.
 If you have altered the sequence in Grub Customizer, or were running a different  previous version of ubuntu, you could be looking in or at the wrong one.

BTW, I think the GFXMODE resolution should not be in inverted commas, though whether it matters a trial would show.

Edit: My Grub_Distributor line is exactly the same as the one you posted, and Grub Customizer found no error there, so I doubt that is the problem.

Chao!, **boga**n

---

### Post by Toz on 2012-01-14
You have 3 double-quotes in this line:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash plymouth:debug=file:/var/log" > /plymouth-debug.log plymouth"

I think the proper way to this is something like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash plymouth:debug=file:/var/log/plymouth-debug.log"
```

---

### Post by tiger63 on 2012-01-14
> **Toz said:**
> You have 3 double-quotes in this line:


I think the proper way to this is something like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash plymouth:debug=file:/var/log/plymouth-debug.log"
```

Thanks to all who replied.  This was indeed the culprit.  Many thanks to Toz's sharp eyes.  Just goes to show, no matter how thoroughly you *think* you examine a file, a fresh pair of eyes is always helpful.

---

### Post by WasMeHere on 2012-01-14
> **tiger63 said:**
> Thanks to all who replied.  This was indeed the culprit.  Many thanks to Toz's sharp eyes.  Just goes to show, no matter how thoroughly you *think* you examine a file, a fresh pair of eyes is always helpful.
Yes, you have sharp eyes, ***Toz***:KS

And I'm glad your problem is solved, ***tiger63***. Please mark your thread SOLVED.

---

