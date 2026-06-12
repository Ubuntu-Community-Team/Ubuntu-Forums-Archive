---
title: "Grub2 Menu Question"
date: 2010-07-01
forum: General Help
---

### Post by Don1500 on 2010-07-01
While optimising my Grub menu it would be very convenient to be able to see the grub menu that will be shown at boot without having to re-boot all the time. Is there a way to get grub to print this menu to a text file during (or after) update-grub?

It looks like a print to file command could be added to 10_linux. I just don't know the language that well to add the correct commands to the script.
I know you can go to grub.cfg but that's too big to have hanging on the side of your screen as a reference. I want something that looks like this:```

Ubuntu, with Linux 2.6.32-23-generic-pae
Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)
Ubuntu, with Linux 2.6.32-22-generic-pae
Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Home Edition (on /dev/sda1)
Fedora (2.6.33.5-124.fc13.i686) (on /dev/sdb4)
Fedora (2.6.33.5-112.fc13.i686) (on /dev/sdb4)
```

This looks like the right place for the linux entries:```
linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
```
Before the first IF statement you would have to clear the old file.
After the FI statement you would printtofile {filename} '${title}' ${CLASS}
For Non-linux OS all that would be printed is ${CLASS}
(As you can see I don't know the language, but you can understand the concept)

---

### Post by Don1500 on 2010-07-01
bhump

---

### Post by Don1500 on 2010-07-02
I decided to use this as a learning experience to teach myself some scripting.
If anyone would want the answer to this send me a message, I'll show you how to do it.
Now I don't need to reboot to see the menu listing order (as made by update-grub).
Here's the result:
```

    Grub Menu Mirror
===========================================================================
Ubuntu 2.6.32-23-generic-pae', with Linux'
Ubuntu 2.6.32-23-generic-pae', with Linux (recovery mode)'
Ubuntu 2.6.32-22-generic-pae', with Linux'
Ubuntu 2.6.32-22-generic-pae', with Linux (recovery mode)'
Microsoft Windows XP Home Edition on /dev/sda1
Ubuntu 9.10 (9.10) on /dev/sdb3
Fedora release 13 (Goddard) on /dev/sdb4
```
while not 100% it is a fair representation. And it updates every time you run update-grub.

---

