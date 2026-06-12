---
title: "Desktop Build (mainly for minecraft)"
date: 2012-04-29
forum: General Help
---

### Post by hw00d on 2012-04-29
Hello all!

My wife and I are considering selling our laptops and buying/buidling a desktop.

I want to build a strictly ubuntu machine. The only game I really care to run is minecraft, so it doesn't need to be a monster, however, I would like to have the power for compiz visual effects because my wife will love it. We're aiming to keep the build sub-$600.

I'm not here to ask for a build, although any advice would be appreciated. What I'm looking for is any list of parts that are (for the most part) out-of-the-box compatible with linux.

Thanks!

---

### Post by gordintoronto on 2012-04-29
At the moment, it seems to be simpler if you avoid UEFI motherboards and hard drives larger than 2 TB. Both of those are not absolute restrictions, they just add some complexity to installing.

In my opinion, a current, fairly low-end ($50-$100) Nvidia video card works well. If there is any chance you will want to play high-end Windows games, you might want to spend more.

For motherboards, I generally log on to Newegg, look at the feedback, and select any comments which include the words Linux or Ubuntu. Same thing with Wireless adapters. My current motherboard is from Gigabyte, and I'm very happy with it and the Phenom II X2 CPU. The system will be three years old this summer.

Memory has become very cheap, so you might go with 8 GB, even though you don't need it now.

You might want to log on to the PCMech web site, where most of the discussion is about computer builds.

Good luck!

---

### Post by pbrane on 2012-04-29
nVidia for graphics and intel if you want wireless. Intel wireless drivers are in the kernel and work on boot. I second what **gordintoronto** said.

 Although running minecraft and compositing seems to have issues. Even with compiz I experience minecraft "freezing" sometimes. If I hit ESC and wait eventually I can get back to a screen I can quit from.

I have a laptop (Dell Inspiron 1720) on which I have never run windows. F12 out of the box to boot and install ubuntu. Everything worked out of the box except for the broadcom wireless, which I replaced with an Intel 3945. Installed nVidia drivers from x-swat ppa, playing mincraft everyday plus other OpenGL games, very smooth.

---

### Post by Veikk0 on 2012-04-29
I agree with the above comments but would like to add that you'll probably be better off with a dual-core CPU than a quad-core or greater. The reason for this is that Minecraft only uses one CPU core; with a dual-core processor you'll get more performance per core than with a quad-core in the same price range.

---

### Post by peterthinking on 2012-04-30
I built a desktop machine specifically for minecraft. (server)

Everything was good to go right out of the box with Linux

Keep in mind this is overkill but I paid about $600 for it which was your budget.

Ubuntu 12.04 64 bit os (Free!)
EVGA video card GeForce GT520 2048 MB DDR3 ($69)
ASUS P8P67-M motherboard with the REV 3.0 P67 B3 Revision ($124)
i5 2500K ($209 you can get an i3 for $129 to save some money the i5 just idles)
Western Digital Caviar Blue 500 GB sata hard drive (already had it but $79)
Velocity IWC-583 case with 500W power supply ($79)
16 Gigs of Ram (4 sticks of 4Gigs each) Kingston HyperX DDR3 1600 CL9 240 pin ($124 for all 16 gigs)
keyboard (already had it)
mouse (already had it)
BIG SCREEN TV!!! (already had it)

I run a server on this and play on the server at the same time on the same box
I have a craft bukkit server and I cranked up the ram to a crazy amount
500Wats is more than enough and I've had no problems overheating even with stock fans and going 24/7 for months.

This is my craftbukkit.sh file....
....................................................
 #!/bin/sh
 BINDIR=/home/peter/Desktop/server
 cd ""
 java -Xmx12G -Xms12G -jar craftbukkit.jar
 EOF
 chmod +x craftbukkit.sh
................................................
I couldn't be happier with it!

To get the ASUS board to boot from the ubuntu cd you have to press delete when it's booting to get into the bios. slide the dvd drive picture at the bottom to the left to change boot order.

Portforwarding to get the server going was a pain but just running the minecraft.jar file you don't need to go through that. Download it, right click on it make it executable in the permissions tab, right click it again and select open with JDK7 (make default)

other than the clean install I added JDK6 and JDK7 and ubuntu restricted extras from the Ubuntu software center.

When I installed 12.04 I selected download updates and codecs while installing.
then I ran update manager and restarted.

You can skimp on the ram (4 gigs instead of 16 ), processor (i3 instead of i5) and scavenge a few things like case (with at least 400 watts Power supply) mouse keyboard hard drive (any smaller sata drive) and monitor to make this come in well under $450
It would still make a good server even cut down to a $450 machine.
Keep the ASUS motherboard and EVGA video card and stick to Western Digital for the drive...it will still be Linux friendly!

Good luck on your build

---

### Post by peterthinking on 2012-04-30
Oh yeah, and the two Bukkit plugins you must have for a public server are "Grief Prevention" and "Light Weight Chest (also known as LWC)" without them you'll be constantly cleaning lava and water grief and theft.

I have other plugins but it's what I consider the bare minimum

: )

---

