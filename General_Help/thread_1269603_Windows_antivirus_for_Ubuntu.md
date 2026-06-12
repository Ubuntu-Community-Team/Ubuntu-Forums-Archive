---
title: "Windows antivirus for Ubuntu?"
date: 2009-09-18
forum: General Help
---

### Post by Arazu on 2009-09-18
I like to fix my friends computers and I usually take their documents and settings and dump them to a CD or USB. Is there some way I can check that data on my Linux machine for Windows viruses? I'd like to make sure it's clean before I dump the data on a clean install.

---

### Post by NoaHall on 2009-09-18
clamav.

sudo apt-get install clamav

---

### Post by Soul-Sing on 2009-09-18
Bitdefender.

---

### Post by Arazu on 2009-09-18
Thanks to you both. I'm trying clamav simply because he posted it first. =)

He also posted a command including aptitude which tells me it's easy to install.

---

### Post by Soul-Sing on 2009-09-18
> **Arazu said:**
> Thanks to you both. I'm trying clamav simply because he posted it first. =)

He also posted a command including aptitude which tells me it's easy to install.

Sorry bout that. Here's a helpful linkage: [http://www.ubuntugeek.com/a-new-free-antivirus-for-unixlinux-platform-bitdefender-antivirus-scanner-for-unices.html](http://www.ubuntugeek.com/a-new-free-antivirus-for-unixlinux-platform-bitdefender-antivirus-scanner-for-unices.html)

---

### Post by Arazu on 2009-09-18
> **leoquant said:**
> Sorry bout that. Here's a helpful linkage: [http://www.ubuntugeek.com/a-new-free-antivirus-for-unixlinux-platform-bitdefender-antivirus-scanner-for-unices.html](http://www.ubuntugeek.com/a-new-free-antivirus-for-unixlinux-platform-bitdefender-antivirus-scanner-for-unices.html)
Thanks for the link. It seems the easy way isn't always the best. clamav is horrid to say the least.

---

### Post by NoaHall on 2009-09-18
Horrid? How? Because it doesn't have a gui? (or not much of one, anyway)

---

### Post by beastrace91 on 2009-09-18
Personally I am a large fan of [avast!](http://www.avast.com/eng/avast-for-linux-workstation.html) for use on both Winblows and Ubuntu to scan for viruses/malware. I use it quiet often on both and it works wonders.

~Jeff

---

### Post by openfly on 2009-09-18
Actually... you could use tripwire on windows shares.  If you do stuff like samba roaming profiles.

---

