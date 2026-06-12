---
title: "Problem with scanner/movie player"
date: 2009-10-28
forum: General Help
---

### Post by Mikew123 on 2009-10-28
Hi

I'm supplying a machine to a client and have installed Ubuntu 9.04

There are two problems that I need a little help with.

The printer/scanner is an Epson Stylus SX400.
The printer is detected and has no problems whatsoever.
However when I open XSane I get the message that no "devices are available".
The help screen basically says that there really is no supported device attached.
The help screen also tells me to look at man sane-dll and man sane-"backendname".
When I type these commands into terminal I am told that there are no manual entries for both commands.
Looking in Synaptic I see that libsane and sane-utils are installed.
Do I need to install sane who's description is "scanner graphical frontends".
Or does anyone know of an alternative program that will recognise the scanner part of the unit.

The second problem is that the machine will not play dvd's.
This is driving me to distraction as I'm using the same OS as the clients machine and the following have been installed on both machines.

libdvdread4
libdvdnav4
libdvdcss2

I can play dvd's, the client's machine can not.
When I try to play a dvd on the client's machine using Movie Player I get a message telling me it needs to search for a suitable plug and the software to play this type of file is not installed.
When I do a search I get another message saying that "No packages with the requested plugins found". The requested plugins are: DVD source.

Before posting this I have opened Synaptic on my machine and on the client's machine, entered "dvd source" into the Quick search box and installed everything that was on my machine on the client's machine and I still get the same errors.
Am I having a stupid moment here and overlooking something simple.

Also, where I have used double quotes I have not used them in any string apart from the man sane-"backendname" command that had them on the help file.

Hopefully someone can point me in the right direction to solve these problems.

Mikew

---

