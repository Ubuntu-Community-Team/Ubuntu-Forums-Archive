---
title: "Installation not Showing Anything"
date: 2010-05-08
forum: General Help
---

### Post by bumcheekcity on 2010-05-08
I've got a laptop on which I want to install Ubuntu. I've downloaded the disc, burnt it (no errors, verified) and it boots up (with the CD in), shows a short BIOS-style copyright notice, then just a black screen with white text flashing across the screen a thousand times faster than I can read it. If I press a key, the background changes purple, then back to black if I press another key.

I can't even SEE the installer. It's kind of like what happens if you set an old CRT monitor to a resolution it can't handle - but the laptop is an LCD that does 1280x800 maximum. What's going on?

The installation of WinXP that it currently has works perfectly.

---

### Post by bumcheekcity on 2010-05-08
A quick update, I left it on the black-text-scrolling screen for 2 mins and came back to it beginning to install, seemingly. I shall try installing it alongside WinXP and see where I get.

---

### Post by colorlessprism on 2010-05-08
ive noticed lately people's md5's have not been matching up. i had to download 10.04 three times before the checksums matched. if your using XP (or any other windows operating system) you need to use a  special program,[ winMD5Sum]("http://www.nullriver.com/products/winmd5sum") is open source and calculates the MD5 checksum of a file or an ISO image. if you have verified its integrity you might try booting from the CD and test its  integrity.

md5 is one of the most common signature to make sure that a  file that you have downloaded is not corrupt. once you have downloaded the the ISO, use winMd5Sum to get the checksum of the file on your  computer. hen make sure that the checksums match. if they do, then your file is exactly the same on your computer as it was/is on the server. tt is a very good idea to  run an md5 hash comparison check when you have a file like an operating  system install CD that has to be 100% correct.

[http://releases.ubuntu.com/10.04/MD5SUMS:](http://releases.ubuntu.com/10.04/MD5SUMS:)
a54366aa72d6b576ee8fc0215f8a13b9 *ubuntu-10.04-alternate-amd64.iso
5b2dadacfd692b4f2d5c7cf034539262 *ubuntu-10.04-alternate-i386.iso
3e0f72becd63cad79bf784ac2b34b448 *ubuntu-10.04-desktop-amd64.iso
d044a2a0c8103fc3e5b7e18b0f7de1c8 *ubuntu-10.04-desktop-i386.iso
0b0e0d36050d9980ec995262eb9f2e6b *ubuntu-10.04-netbook-armel+dove.img
9e0d6ac7b69bb7912d49369a6807e39d *ubuntu-10.04-netbook-armel+imx51.img
712277c7868ab374c4d3c73cff1d95cb *ubuntu-10.04-netbook-i386.iso
8ee25c78f4c66610b6872a05ee9ad81b *ubuntu-10.04-server-amd64.iso
15342636441181f7a19c65984b44e24c *ubuntu-10.04-server-i386.iso
e81f931b1de017520f6d4aa4f78c5c8b *wubi.exe

---

### Post by bumcheekcity on 2010-05-08
Hm. It seems to be working now, if i just ignore this weird effect. I have a SiS 671MX and can't find the drivers for it though, so I can see the screen, but it's only 800x600. It's a pain in the bum, anyone know where I find drivers?

The MD5 is D044A2A0C8103FC3E5B7E18B0F7DE1C8 which is correct for the x86 desktop.

---

