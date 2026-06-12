---
title: "Changing the order of GRUB2 boot entries"
date: 2010-04-28
forum: General Help
---

### Post by fterh on 2010-04-28
Now it's:

Ubuntu
Memtest
Windows 7

I want:

Windows 7
Ubuntu
Memtest

How do I go about doing it? Do I rename "30_os-prober" in /etc/grub.d/ to "10_os-prober" and "10_linux" to "30_linux"?

---

### Post by oldfred on 2010-04-28
You can do something like that, just do not rename or use any of the existing numbers. 

But if all you want to do is have windows boot as the default:
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

If you save the file you create with the custom entry to, say, 06_custom, it will not be over written and will be at the beginning of your menu
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

or a new file that will be first in the menu
gksudo gedit /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom

---

### Post by welshmike on 2010-05-18
I've reviewed this thread but am no wiser how I change the order of GRUB2 boot entries for my multi boot Netbook.

Currently the boot screen shows:
[IMG]http://www.seniorcitizensparty.org.uk/grubsm.jpg[/IMG]

The last/bottom entry is for restoring the XP system and I want to make it the last but one entry and change its name to start with something like:
***** Beware. This restores XP to the factory setting ...

Please will the team advise.

Thanks in advance
Mike

---

### Post by drs305 on 2010-05-18
> **welshmike said:**
> I've reviewed this thread but am no wiser how I change the order of GRUB2 boot entries for my multi boot Netbook.

Currently the boot screen shows:
[IMG]http://www.seniorcitizensparty.org.uk/grubsm.jpg[/IMG]

The last/bottom entry is for restoring the XP system and I want to make it the last but one entry and change its name to start with something like:
***** Beware. This restores XP to the factory setting ...

Please will the team advise.

Thanks in advance
Mike

To change the name without creating a custom menu, you can modify the instructions in Section 4 of my Grub 2 Title Tweaks thread:
[http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602")

Backup and then open /etc/grub.d/30_os-prober as root:
```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober_orig
sudo chmod -x /etc/grub.d/30_os-prober_orig  # Added so this script isn't run during updates.
gksu gedit /etc/grub.d/30_os-prober
```

Find this section:

> 
for OS in ${OSPROBED} ; do
DEVICE="`echo ${OS} | cut -d ':' -f 1`"
LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
BOOT="`echo ${OS} | cut -d ':' -f 4`"

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

# Added to rename Windows Recovery
if [ "$LONGNAME" = "[COLOR="Red"]**Windows NT/2000/XP**[/COLOR]" ] && [ "${DEVICE}" = "/dev/sda2" ] ; then
[COLOR="Red"]LONGNAME[/COLOR]="***** Beware. This restores XP to the factory setting ..."
fi
# End Added


This should rename any menuentry that would have been named as shown in your attachment AND found on sda2. Make sure the text in bold is exactly what is displayed in your menu.

Save the file and run "sudo update-grub".

There are no doubt other ways to accomplish the same thing. See the linked post for other examples, such as completely hiding this option.

Run it, if it needs tweaking, tell me how you would like to change it.

---

### Post by welshmike on 2010-05-18
drs305

Many thanks for your prompt reply and coding.

I made a backup of 30_os-prober , added you coding to the original, did sudo update-grub which ran with a syntax error which I corrected in 30_os-prober and then ran sudo update-grub without error.
When I re-booted, the last four lines of the GRUB list appeared as: 
Microsoft Windows XP Home Edition on /dev/sda1)
Windows NT/2000/XP (on /dev/sda2)
Microsoft Windows XP Home Edition on /dev/sda1)
Windows NT/2000/XP (on /dev/sda2)

I have attached a copy of my 30_os-prober (as a .txt file).

Mike
P.S. Slaps own wrist. Now to do my homework and read your thread [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by drs305 on 2010-05-18
No worries. I'm not good at making scripts without a working copy of the file and I'm not on a dual-boot machine, so give me a bit and I should be able to use the one you provided and make it do what you want.

Having a copy of the grub.cfg file would help as I can't access your screenshot any longer.

Added:
I think I found the problem - fat fingers. Try changing the area in red in the above post.

---

### Post by welshmike on 2010-05-18
Apologies for delayed reply.

The lines now read;

# Added to rename Windows Recovery
if [ "${LONGNAME}" = "WINDOWS NT/2000/XP" ] && [ "${DEVICE}" = "/dev/sda2" ]; then
LONGNAME="***** Beware. Restores XP to the factory setting."
fi
# End Added

Here's a copy of my terminal session (So I believe that the situation will be unchanged for boot time).
mike@mike-netbook:~$ gksu sudo gedit /etc/grub.d/30_os-prober
mike@mike-netbook:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2
done
mike@mike-netbook:~$

---

### Post by angry_johnnie on 2010-05-18
why not just edit /boot/grub/grub.cfg?

i mean, as long as you only change the order of the menu entries, it's ok.

sure, you'll have to do it with each new kernel, but i still think it's a lot easier than doing it the 'right' way.

i've done it since day one, because i like custom entries, and i've never had a problem.

but then again, if you really want to learn grub2, i guess the 'right' way is fine. :p

---

### Post by Norm24 on 2010-05-18
How about using Start-Up Manager?Works for me.

---

### Post by drs305 on 2010-05-18
johnnie (hope you aren't still angry),

I'd agree with you to a point but would pick the solution between editing the grub.cfg file and editing the scripts. The best compromise IMO is a making a custom menu. But you wouldn't learn or waste nearly as much time that way!  ;-)

---

