---
title: "Oneiric: Change tty font and make the change persistent (on GRUB too)..."
date: 2011-11-05
forum: General Help
---

### Post by zia.newversion on 2011-11-05
I had read somewhere in some Ubuntu tutorial some 5 years ago when I was beginning to warm up to Ubuntu and the command-line philosophy that you could change the default font of tty console (the Ctrl+Alt+F1 to F6 terminal screens) by running


```
sudo dpkg-reconfigure console-setup
```I used to use that method quite effectively until I installed Oneiric.

Now, when I use the particular console directive to change the console font, it works fine.. UNTIL I REBOOT!

In previous versions of Ubuntu, when I applied that procedure, the GRUB font also changed to the default console font. I liked it because the font in question (Terminus Bold 32x16) looks so much better on my 1080p screen compared to the default (vga) font.

Now, when I reboot, the same old (vga) font appears on GRUB. Then, proceeding to GDM login, when I press Ctrl+Alt+F1 on the desktop, it takes me to tty1, which has the same old (vga) font that I am frankly starting to HATE!!!

Can anyone please help me make that change in the font persistent and make it apply on the GRUB as well? Thanks in advance. :)

EDIT: The dpkg-reconfigure console-setup also builds a new kernel image at the end! But I don't know why the new kernel image doesn't save the changes!

EDIT: Uploaded the photo. Sorry, since it is tty, I cannot take screenshots (or could I?)... And I have a really low-quality camera in my phone (2MP)... The change in font may not be obvious, but it is a different font (and a whole lot better), I promise. :D

EDIT: Uploaded the better quality screencasts (taken through fbgrab)...

---

### Post by zia.newversion on 2011-11-07
Bump!
85 views and not a single reply?!

:(

---

### Post by matt_symes on 2011-11-07
Hi

You can change the console font -from the console and not the terminal- when you log in with the setfont command passing it a path to the font you want to use.

From the CONSOLE.

```
setfont /usr/share/consolefonts/<name_of_font>.psf.gz
```There is no need to *sudo dpkg-reconfigure ....* just to change the font for that tty.

Also, the command ```
setupcon
``` run from the console will use the values stored in /etc/default/console-setup to setup the console and you can change keyboard, font and other values.

However, the above points are by the by as they do not fix your problem.

> 
The dpkg-reconfigure console-setup also builds a new kernel image at the  end! But I don't know why the new kernel image doesn't save the  changes!I believe it rebuilds the initramfs and not the kernel so i would suggest the problem is there, especially as you want the font setup early in the boot process.

I may be the initramfs is not being created correctly. It may be that the /usr directory is not mounted when the consoles are setup. It may be a bug in the configuration of console-setup. I really don't know but if we work through the problem then maybe we can find a solution. If not then at least it gives others a change to see the thread.

We can try to work through the problem though and there is a work around if you are not too worried about the font very early in the boot process.

First lets have a look at your configuration file after you have reconfigured it to terminus bold.

```
ls -l /etc/default/console-setup
```and cat 

```
cat /etc/default/console-setup
```Maybe we can work through the problem and find a solution.

Also, do you have any special partitioning in your system ? How is it partitioned ?

Kind regards

---

### Post by zia.newversion on 2011-11-08
> **matt_symes said:**
> Hi

You can change the console font -from the console and not the terminal- when you log in with the setfont command passing it a path to the font you want to use.

From the CONSOLE.

```
setfont /usr/share/consolefonts/<name_of_font>.psf.gz
```There is no need to *sudo dpkg-reconfigure ....* just to change the font for that tty.

Also, the command ```
setupcon
``` run from the console will use the values stored in /etc/default/console-setup to setup the console and you can change keyboard, font and other values.

However, the above points are by the by as they do not fix your problem.

You are right. They don't solve my problem.
I need to set the default console font; like when I boot the system, the console already has the font that I desire. (And of course, GRUB too)... I know we have some workarounds for changing the fonts for GRUB, but I need a genuine method, not a sloppy workaround. Something that works for the Ubuntu console altogether, not separately for GRUB and for the tty consoles.

The setfont method works for the current session only. And it sure doesn't change the font on all consoles (tty1-6).

I used dpkg-reconfigure because it sets the default console font and not temporarily changes it. It creates a new kernel image (or initramfs, I would like to know in detail about these things) which contains the new font (and keyboard+language) settings and next time on, the same font is shown on all tty's.

> **matt_symes said:**
> 
I may be the initramfs is not being created correctly. It may be that the /usr directory is not mounted when the consoles are setup. It may be a bug in the configuration of console-setup. I really don't know but if we work through the problem then maybe we can find a solution. If not then at least it gives others a change to see the thread.

We can try to work through the problem though and there is a work around if you are not too worried about the font very early in the boot process.

Sure thing, sir! I would like that very much. :)
I am not "too" worried, but I do want to change the font as quickly as possible. The default font creeps the hell out of me!

> **matt_symes said:**
>  First lets have a look at your configuration file after you have reconfigured it to terminus bold.

```
ls -l /etc/default/console-setup
```and cat 

```
cat /etc/default/console-setup
```

```

zia@Brainloggers-Unix:~$ ls -l /etc/default/console-setup
-rw-r--r-- 1 root root 2064 2011-11-08 17:55 /etc/default/console-setup
zia@Brainloggers-Unix:~$ cat /etc/default/console-setup
# Change to "yes" and setupcon will explain what is being doing
VERBOSE_OUTPUT="no"

# Setup these consoles.  Most people do not need to change this.
ACTIVE_CONSOLES="/dev/tty[1-6]"

# Put here your encoding.  Valid charmaps are: UTF-8 ARMSCII-8 CP1251
# CP1255 CP1256 GEORGIAN-ACADEMY GEORGIAN-PS IBM1133 ISIRI-3342
# ISO-8859-1 ISO-8859-2 ISO-8859-3 ISO-8859-4 ISO-8859-5 ISO-8859-6
# ISO-8859-7 ISO-8859-8 ISO-8859-9 ISO-8859-10 ISO-8859-11 ISO-8859-13
# ISO-8859-14 ISO-8859-15 ISO-8859-16 KOI8-R KOI8-U TIS-620 VISCII
CHARMAP="UTF-8"

# The codeset determines which symbols are supported by the font.
# Valid codesets are: Arabic Armenian CyrAsia CyrKoi CyrSlav Ethiopian
# Georgian Greek Hebrew Lao Lat15 Lat2 Lat38 Lat7 Thai Uni1 Uni2 Uni3
# Vietnamese.  Read README.fonts for explanation.
CODESET="Uni2"

# Valid font faces are: VGA (sizes 8, 14 and 16), Terminus (sizes
# 12x6, 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBold (sizes
# 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBoldVGA (sizes 14
# and 16) and Fixed (sizes 13, 14, 15, 16 and 18).  Only when
# CODESET=Ethiopian: Goha (sizes 12, 14 and 16) and 
# GohaClassic (sizes 12, 14 and 16).
# Set FONTFACE and FONTSIZE to empty strings if you want setupcon to
# set up the keyboard but to leave the console font unchanged.
FONTFACE="TerminusBold"
FONTSIZE="28x14"

# You can also directly specify nonstandard font or console map to load.
# Use space as separator if you want to load more than one font.
# You can use FONT_MAP in order to specify the Unicode map of the font
# in case the font doesn't have it embedded.

# FONT='lat9w-08.psf.gz /usr/local/share/braillefonts/brl-08.psf'
# FONT_MAP=/usr/share/consoletrans/lat9u.uni
# CONSOLE_MAP=/usr/local/share/consoletrans/my_special_encoding.acm

# You can also specify a screen size that setupcon will enforce.  This can not
# exceed what the current screen resolution can display according to the size of
# the loaded font.
#
# SCREEN_WIDTH=80
# SCREEN_HEIGHT=25

if [ -f /etc/default/keyboard ]; then
    . /etc/default/keyboard
fi


```
Ok. You can observe that /etc/console-setup is fine... It's just that the system doesn't obey it while booting.
I would go with the possibility that the partition isn't mounted until later in the boot process. But you see, I have only one system partition (that is "/") and /etc/ and /usr/ lie in the same partition as /boot/ so the partition is mounted fine since the GRUB stages...
Also, when booted, I go to tty1 and run setupcon and the console changes appearance as it should... I don't get it.
Do I have to add setupcon to the startup scripts?
But that wouldn't apply it to GRUB, would it? And in case I discard the bootsplash and turn on the text boot, the booting text will appear in the same default font and not the Terminus Bold... I want to change the font throughout the system!
> **matt_symes said:**
> Also, do you have any special partitioning in your system ? How is it partitioned ?
```
zia@Brainloggers-Unix:/dev$ sudo fdisk -l /dev/sda
[sudo] password for zia: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcd769706

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400   de  Dell Utility
/dev/sda2          206848   348162047   173977600    7  HPFS/NTFS/exFAT
/dev/sda3       348162048   406755327    29296640   83  Linux
/dev/sda4       406755328   976771071   285007872    f  W95 Ext'd (LBA)
/dev/sda5       406757376   966531071   279886848    7  HPFS/NTFS/exFAT
/dev/sda6       966534723   976768064     5116671   82  Linux swap / Solaris

```

---

### Post by matt_symes on 2011-11-08
Hi

> You can observe that /etc/console-setup is fine...Agreed. Looks fine from here as well.

> I would go with the possibility that the partition isn't mounted until  later in the boot process. But you see, I have only one system partition  (that is "/") and /etc/ and /usr/ lie in the same partition as /boot/  so the partition is mounted fine since the GRUB stages...I think we can -almost- discount any mounting issues with /usr if /usr is on your root partition. It may be some race condition but....

> Do I have to add setupcon to the startup scripts?That was going to be my suggested workaround. You will not have the fancy font during the boot process but you should when you drop down to a console :) Maybe put it in rc.local.

I will have to look into this a bit later today though. Maybe we should have a dig into your initramfs. 

I will also boot into Oneiric later as i am currently in Lucid. I will try it on my Oneiric install to make sure it's not a quirk on your install. Either way, that may tell us a lot.

**EDIT: **Please repost a *bump* in this thread so it appears in my subscribed threads section otherwise i will have to dig though my folders looking for this thread.

Kind regards

---

### Post by zia.newversion on 2011-11-08
> **matt_symes said:**
> 
That was going to be my suggested workaround. You will not have the fancy font during the boot process but you should when you drop down to a console :) Maybe put it in rc.local.
I tried running just a setupcon on tty1 and set the output to verbose. It appears that access is denied on a LOT of things and tty2-6 still remain unconfigured (because of access issues).
I cannot put *just* setupcon in my startup scripts because it won't do what I desire even after comlpete boot-up. If I could, I would put it with a preceding sudo, but it will stop and require my password (if it indeed cares to do so, but it would just ignore it or crash - likely the first one). And I don't want to put it in my startup scripts because (1) it's another one of those sleazy workarounds and not genuinely impressive (2) it doesn't fulfil the intended purpose anyway since the boot-process will still have that freaky default font.

> **matt_symes said:**
> I will have to look into this a bit later today though. Maybe we should have a dig into your initramfs.

Just keep giving me the commands to execute and I'll provide you the outputs of those. I appreciate it very much, by the way. 

> **matt_symes said:**
> I will also boot into Oneiric later as i am currently in Lucid. I will try it on my Oneiric install to make sure it's not a quirk on your install. Either way, that may tell us a lot.
I was so annoyed I reinstalled Ubuntu from scratch. Downloaded a new image. Performed checksum once again. Burnt the ISO (last time I used a USB). Formatted the root partition with UBCD (I could do it in the Ubuntu setup, but I thought... I really don't know what I thought). Sat through installation without blinking (metaphorically - I blinked, but very little). And phew, tail of the dog doesn't come out of the twist! The problem persists.

I had installed Propriety ATI drivers last time. I thought maybe it was an issue of hardware, like maybe the drivers didn't support the fonts (like they don't support widescreen plymouth or widescreen framebuffer). So I went through the dpkg-reconfigure process and all the customary diagnostics like cat-ing the console-setup file and everything else, without installing fglrx and after install fglrx... The problem persists!

> **matt_symes said:**
> **EDIT: **Please repost a *bump* in this thread so it appears in my subscribed threads section otherwise i will have to dig though my folders looking for this thread.

Sure thing. Guess I did a little more than just bump. :p
Have a nice time. And don't have all the fun. Gimme some work to do as well. :D JK, thanks a lot for the support.

---

### Post by TechZilla on 2011-11-09
I just read this, while looking for a similar thing, 
Here is what Ubuntu used to do.

Grub -> initramfs -> init.d/console-setup

The font was set at init.d. Basically if you disabled any splash, you would see the distinctive change when the font loaded.  But it would be set for all terminals.

You can workaround with, setupcon in /etc/rc.local, and you will see the same effect.  although to correctly replicate it you would want to fix the real upstart script, as rc.local executes at every run level change.   However, you at least have your console-setup on all tty's.  I would guess the old setup stopped working with the transition to upstart. I personally have noticed it broken, for the past few releases. 

I would love to have the terminus font set, from Grub2 onward.  In Grub2, I understand how it would be done.  However, I have no idea how this could be done with initramfs.  Which is what I want to figure out.

---

### Post by zia.newversion on 2011-11-09
> **TechZilla said:**
> I just read this, while looking for a similar thing, 
Here is what Ubuntu used to do.

Grub -> initramfs -> init.d/console-setup

The font was set at init.d. Basically if you disabled any splash, you would see the distinctive change when the font loaded.  But it would be set for all terminals.

You can workaround with, setupcon in /etc/rc.local, and you will see the same effect.  although to correctly replicate it you would want to fix the real upstart script, as rc.local executes at every run level change.   However, you at least have your console-setup on all tty's.  I would guess the old setup stopped working with the transition to upstart. I personally have noticed it broken, for the past few releases. 

I would love to have the terminus font set, from Grub2 onward.  In Grub2, I understand how it would be done.  However, I have no idea how this could be done with initramfs.  Which is what I want to figure out.
Thanks a lot for the reply.
I will try the rc.local method.

But just like you, I wish I could change it throughout!
Although it is just another workaround, but could it be done by renaming terminus font file to the default system font filename, and then rebuilding initramfs?

Also, if you, or anyone else could give me a small tour of what role kernel, initramfs, init.d etc play in the Linux boot process? Perhaps you could give me such a link.
I know what a kernel is... Little bit! But I would like to study in detail how the Linux kernel works. One way is to read the source code. I call myself a programmer but in reality, I'm just a novice. I mainly work with embedded systems and that too, related to Microchip PIC processors and development systems. So, reading the code will take a lot of time, unless there is a wiki or perhaps a book, which would explain the most complex parts of the code; then it'd be easier and a lot less headache and a lot more fun.

That was out of context, but I'm sure there is a simple way we could get what we want (change the default system font to Terminus), we just need to look through it a little more!

---

### Post by matt_symes on 2011-11-09
Hi

Adding setupcon to rc.local method worked in my Oneiric install (well actually it' Precise but i have not updated it for a while).

Here is my rc.local file.
```

matthew@matthew-Aspire-7540:~$ cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

setupcon

exit 0
matthew@matthew-Aspire-7540:~$ 

```

Here is my /etc/default/console-setup file
```

matthew@matthew-Aspire-7540:~$ cat /etc/default/console-setup 
# Change to "yes" and setupcon will explain what is being doing
VERBOSE_OUTPUT="no"

# Setup these consoles.  Most people do not need to change this.
ACTIVE_CONSOLES="/dev/tty[1-6]"

# Put here your encoding.  Valid charmaps are: UTF-8 ARMSCII-8 CP1251
# CP1255 CP1256 GEORGIAN-ACADEMY GEORGIAN-PS IBM1133 ISIRI-3342
# ISO-8859-1 ISO-8859-2 ISO-8859-3 ISO-8859-4 ISO-8859-5 ISO-8859-6
# ISO-8859-7 ISO-8859-8 ISO-8859-9 ISO-8859-10 ISO-8859-11 ISO-8859-13
# ISO-8859-14 ISO-8859-15 ISO-8859-16 KOI8-R KOI8-U TIS-620 VISCII
CHARMAP="UTF-8"

# The codeset determines which symbols are supported by the font.
# Valid codesets are: Arabic Armenian CyrAsia CyrKoi CyrSlav Ethiopian
# Georgian Greek Hebrew Lao Lat15 Lat2 Lat38 Lat7 Thai Uni1 Uni2 Uni3
# Vietnamese.  Read README.fonts for explanation.
CODESET="Uni2"

# Valid font faces are: VGA (sizes 8, 14 and 16), Terminus (sizes
# 12x6, 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBold (sizes
# 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBoldVGA (sizes 14
# and 16) and Fixed (sizes 13, 14, 15, 16 and 18).  Only when
# CODESET=Ethiopian: Goha (sizes 12, 14 and 16) and 
# GohaClassic (sizes 12, 14 and 16).
# Set FONTFACE and FONTSIZE to empty strings if you want setupcon to
# set up the keyboard but to leave the console font unchanged.
FONTFACE="TerminusBold"
FONTSIZE="20x10"

# You can also directly specify nonstandard font or console map to load.
# Use space as separator if you want to load more than one font.
# You can use FONT_MAP in order to specify the Unicode map of the font
# in case the font doesn't have it embedded.

# FONT='lat9w-08.psf.gz /usr/local/share/braillefonts/brl-08.psf'
# FONT_MAP=/usr/share/consoletrans/lat9u.uni
# CONSOLE_MAP=/usr/local/share/consoletrans/my_special_encoding.acm

# You can also specify a screen size that setupcon will enforce.  This can not
# exceed what the current screen resolution can display according to the size of
# the loaded font.
#
# SCREEN_WIDTH=80
# SCREEN_HEIGHT=25

if [ -f /etc/default/keyboard ]; then
    . /etc/default/keyboard
fi

```

At the LightDM login screen i dropped down to tty1 and the font had been change to TerminusBold.

*sudo dpkg-reconfigure console-setup *did not work on my laptop either so there is a problem there.

I have to find a power supply and when i do i will investigate.

Kind regards.

---

### Post by matt_symes on 2011-11-09
Hi

> **TechZilla said:**
> I just read this, while looking for a similar thing, 
Here is what Ubuntu used to do.

Grub -> initramfs -> init.d/console-setup

The font was set at init.d. Basically if you disabled any splash, you would see the distinctive change when the font loaded.  But it would be set for all terminals.

You can workaround with, setupcon in /etc/rc.local, and you will see the same effect.  although to correctly replicate it you would want to fix the real upstart script, as rc.local executes at every run level change.   However, you at least have your console-setup on all tty's.  I would guess the old setup stopped working with the transition to upstart. I personally have noticed it broken, for the past few releases. 

I would love to have the terminus font set, from Grub2 onward.  In Grub2, I understand how it would be done.  However, I have no idea how this could be done with initramfs.  Which is what I want to figure out.

This is a good post :D  Thankyou for posting this. I missed it before writing my last response.

Maybe we can edit one of initramfs' start up scripts.

Need to find a power supply fast :(

Kind regards

---

### Post by matt_symes on 2011-11-09
Hi

I have been doing a little routing around in the initramfs archives for both 10.04 and 11.10.

This is one things i have noticed

On 10.04.

```

matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_uncompressed$ find . -name console_setup
./scripts/init-top/console_setup
./scripts/panic/console_setup
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_uncompressed$ 
```11.10.

```

matthew@matthew-Aspire-7540:~/initramfs_uncompressed/11.10_uncompressed$ find . -name console_setup
./scripts/panic/console_setup
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/11.10_uncompressed$
```init-top is one of the steps called in the initramfs boot sequence.

From```
man initramfs-tools
```> init-top

the scripts in this directory are the first scripts to be executed after sysfs and procfs have been mounted.  It also runs the udev hook for populat&#8208;ing the /dev tree (udev will keep running until init-bottom).Both archives contain the font *(i think i may have chosen 2 different fonts but they are both not the default)* and the default configuration file.

For 10.04

```
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_uncompressed$ find . -name console-setup
./etc/console-setup
./etc/default/console-setup
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_uncompressed$ls etc/console-setup
cached.kmap.gz  Lat15-TerminusBold16.psf
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_ucompressed$
```For 11.10

```

matthew@matthew-Aspire-7540:~/initramfs_uncompressed/11.10_uncompressed$ find . -name console-setup
./etc/console-setup
./etc/default/console-setup
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/11.10_uncompressed$ls etc/console-setup/
cached.kmap.gz  Uni2-TerminusBold20x10.psf
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/11.10_uncompressed$ 
```The file* console-setup* is slightly different between 10.04 and 11.10 but nothing that should cause the issue.

Assuming *console_setup* works pretty much the same between 10.04 and 11.10 and assuming that console_setup is the script that actually set the font for the consoles - i have not looked at the script yet - then the problem may be that the script *console_setup* is not the in the directory *scripts/init-top/* in the 11.10 initramfs archive.

More investigation is needed but what are your thoughts so far.

Understand that i may be going on a wild goose chase here as well ;)

Kind regards

---

### Post by matt_symes on 2011-11-09
Hi

I have started looking at the file console_setup

Here are the differences between 10.04's panic and init-top scripts

```

matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_uncompressed$ diff scripts/init-top/console_setup scripts/panic/console_setup 
4d3
< OPTION=FRAMEBUFFER
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_uncompressed$
```Here are the differences between 10.04's panic and 11.04's panic console_setup scripts
```

matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_uncompressed$ diff ../11.10_uncompressed/scripts/panic/console_setup scripts/panic/console_setup 
17d16
< [ -r /etc/default/console-setup ] || exit 0
matthew@matthew-Aspire-7540:~/initramfs_uncompressed/10.04_uncompressed$ 
```The differences are small.

As for the script itself, here is a snippet.

```
for i in 1 2 3 4 5 6; do
        [ -c /dev/tty$i ] || mknod /dev/tty$i c 4 $i
done

for console in $ACTIVE_CONSOLES; do
        [ -w $console ] || continue

        <snip>

        if [ "$FONT" ]; then
                FONT="/etc/console-setup/${FONT##*/}"
                FONT="${FONT%.gz}"
        else
                FONT="/etc/console-setup/$CODESET-$FONTFACE$FONTSIZE.psf"
        fi
        if [ -f "$FONT" ]; then
                if type consolechars >/dev/null 2>&1; then
                        eval consolechars -v --tty=$console -f "$FONT" $verbose
                elif type setfont >/dev/null 2>&1; then
                        eval setfont -v -C $console "$FONT" $verbose
                fi
        fi

        if [ "$ACM" ]; then
                ACM="/etc/console-setup/${ACM##*/}"
                ACM="${ACM%.gz}"
        else
                ACM="/etc/console-setup/$CHARMAP.acm"
        fi
        if [ -f "$ACM" ]; then
                if type consolechars >/dev/null 2>&1; then
                        eval consolechars -v --tty=$console --acm "$ACM" \
                                $verbose
                elif type setfont >/dev/null 2>&1; then
                        eval setfont -v -C "$console" -m "$ACM" $verbose
                fi
        fi

        <snip>
done

```It makes tty nodes under /dev and then tries to set a font for each tty. 

I assume these nodes are  the final nodes attached to / along with /proc and /sys.

I may try to rebuild 11.10's initramfs with this file by hand and drop it into /boot. I have old kernels so if there is a problem i can boot into one of them.

I still don't know if this is the right approach though.

Kind regards

---

### Post by zia.newversion on 2011-11-09
Hi, Matt...

I'm very very sorry. I couldn't reply for quite some time.

What happened was, I diverted my attention to getting Terminus Bold on GRUB as well and ended up destroying GRUB. Didn't know where I had put my Live CD and didn't have a Live USB, so couldn't boot the computer. I just repaired my system by reinstalling GRUB on hda. :)

Ok... You have posted so much in just a one and a half day that I can't even read through it completely! :p I tried the rc.local method and it works just like you mentioned. At the login screen, I go to tty1 and the console is in Terminus Bold...

However, **I noticed that there are two rc.local files!** There is one at /etc/rc.local and another one at /etc/init.d/rc.local. The one in /etc did nothing by default (just exit 0 and some jibber jabber on the top). The one in /etc/init.d has a little script already present in it... Since I don't know bash any further than echo, I can't decipher what it actually does. But I think that the rc.local in /etc calls this one up (or vice versa)... In any case, you put setupcon in either one and it works fine...

But then again, it is just that by default the system did not care to setup consoles while booting up. Now we are explicitly telling it to read the console-setup and update the console look according to that. That works, but doesn't feel genuine...

The later explorations that you did are nice efforts, but I fail to see what they are converging towards... I can see that there are differences in the scripts of 10.04 and 10.11, but can't make out what those differences signify. I read the script, and I can make out only as much as you already explained. Should we file a bug? :p

One last thing. I was trying to adopt a new perspective and I thought, if the GRUB font is changed , since it is GRUB that boots up the kernel, it should pass the font on as well. I do vaguely remember an instance where I tried to change the GRUB font (it was Maverick I think) and messed it up. As a result, when booting, the system showed the same messed up font that GRUB was using. I think if we change the GRUB font to TerminusBold, it may be passed on to kernel and automatically become the default font for all the ttys. Do you know how to do that?

---

### Post by matt_symes on 2011-11-10
Hi

I've messed up GRUB may times so i know what that's like. :D
> 
But then again, it is just that by default the system did not care to  setup consoles while booting up. Now we are explicitly telling it to  read the console-setup and update the console look according to that.  That works, but doesn't feel genuine...It is a perfectly valid solution and is what the /etc/rc.local file is for. It is called after all other systemV scripts to set up any options one may need late into the boot process. You want the font set early in the boot process and not late and this is why it's not the best solution for you.

> The later explorations that you did are nice efforts, but I fail to see  what they are converging towards... I can see that there are differences  in the scripts of 10.04 and 10.11, but can't make out what those  differences signify. I read the script, and I can make out only as much  as you already explained. Should we file a bug? :razz:In <11.10 a script was included in the initramfs archive that looks like it changed the font. This is not in present in 11.10 and may, and i definitely say may, be part of the problem as before *dkpg-reconfigure console-setup* recreated the initramfs file. This is why i am looking at that because in  <11.10 the font changed.

Maybe a bug report later as i am still trying to understand the boot process from grub to initramfs and tty creation.

> 
One last thing. I was trying to adopt a new perspective and I thought,  if the GRUB font is changed , since it is GRUB that boots up the kernel,  it should pass the font on as well. I do vaguely remember an instance  where I tried to change the GRUB font (it was Maverick I think) and  messed it up. As a result, when booting, the system showed the same  messed up font that GRUB was using. I think if we change the GRUB font  to TerminusBold, it may be passed on to kernel and automatically become  the default font for all the ttys. Do you know how to do that?This may work but, at the moment, i fail to see how setting the font on GRUB would affect all the ttys as opposed to only the one grub uses. I may be wrong here though.

To change the grub font, check this out.

[http://askubuntu.com/questions/11846/changing-the-default-grub-font](http://askubuntu.com/questions/11846/changing-the-default-grub-font)

Understand, i do not currently know the solution but i am trying to work through the problem. It's a case of working through the problem and trying to find a solution.

I will recreate 11.10's initramfs archive with the script in etc/init-top and see what happens.

Kind regards

---

### Post by zia.newversion on 2011-11-10
> **matt_symes said:**
> Hi
To change the grub font, check this out.

[http://askubuntu.com/questions/11846/changing-the-default-grub-font](http://askubuntu.com/questions/11846/changing-the-default-grub-font)


I've been through that askUbuntu post. I tried applying it to Uni2-TerminusBold32x16.psf.gz but grub-mkfont would return an error!

Do you some other way, which allows converting or passing the psf font to GRUB?

---

### Post by matt_symes on 2011-11-10
Hi

> **zia.newversion said:**
> I've been through that askUbuntu post. I tried applying it to Uni2-TerminusBold32x16.psf.gz but grub-mkfont would return an error!

Do you some other way, which allows converting or passing the psf font to GRUB?

It would seem that grub uses pf2 fonts. These are bitmap fonts. Consoles use psf fonts.

I don't know a way to convert them. Have a look on Google. I will at some point myself.

Anyway, i have found out how to get the fonts into initramfs.

In /usr/share/initramfs-tools there are hooks and scripts for console_setup. This is the script that changes the fonts for the tty's.

Console_setup is dependent on framebuffer and both are dependent on the option FRAMEBUFFER.

If FRAMEBUFFER is not defined then the framebuffer and console_setup scripts are not added to the initramfs archive.

So to get it included in the initramfs archive, set up your /etc/default/console-setup file with the font you want to use. Make sure the font is in /etc/console-setup.

Open a terminal and type
```

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/config_fb
```Then update the initramfs using

```
sudo update-initramfs -u
```Reboot your PC.

You can also use that echo command above to set the FRAMEBUFFER option and then

```
sudo dpkg-reconfigure console-setup
```


Kind regards

---

