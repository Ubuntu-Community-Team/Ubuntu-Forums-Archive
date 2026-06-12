---
title: "FooBillard no longer opens"
date: 2011-10-19
forum: General Help
---

### Post by donmarco5 on 2011-10-19
After updating Ubuntu 10.04 on 10-18-2011, Foobillard  does not open.  Foobillard worked on my computers for years until yesterday.  Is there a way to fix this problem?  Thank you for your responses.

---

### Post by hal8000 on 2011-10-19
Can you be more specific about your update?

Which version where you using before and which version did you update to?

Start foobilliard from the terminal and post the output of:

foobilliard

This may reveal extra info about the problem.

---

### Post by donmarco5 on 2011-10-19
Thank you for responding.  I am using kernel 2.6.32-34 on an up to date installation of Ubuntu 10.04.  The output from Foobillard run in the terminal is:

usage: foobillard [--option [<arg>]]
  options:
--player1 <arg>
     arg=ai|human set player1 ai/human
--player2 <arg>
     arg=ai|human set player2 ai/human
--p1 <arg>
     arg=ai|human set player1 ai/human
--p2 <arg>
     arg=ai|human set player2 ai/human
--name1 <arg>
     set name of player1
--name2 <arg>
     set name of player2
--8ball 
     8ball pool game
--9ball 
     9ball pool game
--carambol 
     carambol billard game
--snooker 
     snooker billard game
--tablecolor <arg>
     table color in C-style hex notation <0xrrggbb>
--edgecolor <arg>
     edge color in C-style hex notation <0xrrggbb>
--framecolor <arg>
     frame color in C-style hex notation <0xrrggbb>
--chromeblue 
     blue table with chrome edges
--goldgreen 
     green table with gold edges
--goldred 
     red table with gold edges
--blackwhite 
     balck table with white frame
--blackbeige 
     beige table with balck metal
--tablesize <arg>
     table size (length) in foot (default=7.0)
--lensflare 
     turn on lensfare
--nolensflare 
     turn off lensfare
--poslight 
     use positional light
--dirlight 
     use directional light
--ai1err <arg>
     to err is artificial (player1 error 0..1)
--ai2err <arg>
     to err is artificial (player2 error 0..1)
--balldetail <arg>
     set ball detail l[ow] m[edium] h[igh] or v[eryhigh]
--rgstereo 
     start in stereo mode (red-green(cyan))
--rgaim <arg>
     arg=left|right|middle for aiming eye position
--hostaddr <arg>
     arg=IP-address for TCP/IP connection
--portnum <arg>
     arg=port# for TCP/IP connection
--geometry <arg>
     <width>x<height> window geometry
--fullscreen 
     play in fullscreen mode
--freemove <arg>
     arg=on|off free move in external view mode
--cuberef <arg>
     arg=on|off rendered cubemep reflections
--cuberes <arg>
     arg=<texture size for cuberef> (must be power of 2)
--bumpref <arg>
     arg=on|off bumpmap reflections of edges
--bumpwood <arg>
     arg=on|off bumpmap of wood covers
--balltraces <arg>
     arg=on|off trace lines of balls
--gamemode <arg>
     arg=match|training|tournament
--fresnel <arg>
     arg=on|off fresnel ball reflections
--avatar <arg>
     arg=on|off enable/disable avatar
--tourfast <arg>
     arg=1.0..10.0 AI fast motion ratio for tournament
--clothtex <arg>
     arg=on|off for table detail map
--help 
     this help
the color <0xrrggbb> means one byte for each red, green, blue

main:rgstereo=0X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  18
  Current serial number in output stream:  18

I update Ubuntu every day but I am not sure which updates I received on 10-18-2011.   Foobillard worked on 10-17-2011.  Please let me know what other information you need.  Thank you.

---

### Post by donmarco5 on 2011-10-20
:D After updating Ubuntu 10.04 with Update Manager today, foobillard opens and works correctly once again.  I think that today's update of xserver-xorg-core and xserver-common to version 2:1.76-2ubuntu7.9 fixed the opengl problem that prevented foobillard from opening yesterday.  Thank you Ubuntu.  I consider this problem as solved.

---

