---
title: "X Error of failed request:  BadLength (poly request too large or internal Xlib length"
date: 2011-10-19
forum: General Help
---

### Post by debug01 on 2011-10-19
Hello

My problem is this ...

Initially I could not detect an iPod in my laptop with ubuntu 10, so, I upgraded my system, however, I don't know which package I upgraded (by mistake) and now I can't execute programs that were previously compiled in g++ using OpenGL (gl, glu, glut)

>>g++ -o program programSource.c -lGL -lGLU -lglut

Before upgrading, programs that I had compiled I could perform and display them without problems, but now, I can't do anything, I get the following error when I invoked this programs from a terminal:

X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  27
  Current serial number in output stream:  27


I have no idea where to start looking, I read some forums that may be, my problem it's with my driver for my graphics card, but I don't know.

I really appreciate any kind of help.

P.D. Now, I can use my iPod :P

---

### Post by niroma on 2011-10-19
Hi,

No help but I also get this message after running the last updates (Ununtu 10.04):

X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  969
  Current serial number in output stream:  969

In my case it occurs when trying to start Google SketchUp via wine.

Have no idea what to do about it.

Regards
Niroma

---

### Post by Captain_Rage on 2011-10-19
I'm having similar issues, running the 32 bit version of Ubuntu 10.04. The machine is a Eee PC 901 (with an Intel integrated graphics card).

Nothing that uses OpenGL wants to start, it only gives different errors.
No Compiz, no glxgears, nothing. Even nothing at all happens if I boot into recovery mode and try to reconfigure xorg.conf.

In recovery mode this message shows:
"Ubuntu is running in low-graphics mode

Your screen, graphics card, and input settings could not be detected correctly.
You will need to configure these yourself."


First I thought my computer had run into trouble after I did a hard reset due to some applications hanging, but now I'm also starting to suspect that it could have been an upgrade that broke something (which appeared after my computer restarting).

EDIT: This seems to have been caused by faultry updates. The information in this thread should help:
[http://ubuntuforums.org/showthread.php?t=1864221&referrerid=1192031](http://ubuntuforums.org/showthread.php?t=1864221&referrerid=1192031)

---

### Post by sybille on 2011-10-19
Hi,

Could everyone who reported the problem in this thread go to the  following Launchpad bug and click at the top of the page to confirm that  the bug is affecting you?

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/877905)

Thanks!

Also, for people who are working around the problem by downgrading the  problematic packages - xserver-common and xserver-xorg-core - please  realize that the updated packages were for a security update. So it is  important for you to follow the issue closely and to make sure to  upgrade as soon as there are new, fixed packages if you must continue to  use the old, insecure versions.

---

### Post by debug01 on 2011-10-19
[FONT=Arial][SIZE=2][COLOR=#333333][FONT=arial]hello everyone

I solve my problem with the Captain_Rage's [/FONT][/COLOR][COLOR=#333333][FONT=arial]post [/FONT][/COLOR][COLOR=#333333][FONT=arial](thank you very much).

[/FONT][/COLOR][[COLOR=#333333][FONT=arial]http://ubuntuforums.org/showthread.php?t=1864221&referrerid=1192031[/FONT][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1864221&referrerid=1192031")

[COLOR=#333333][FONT=arial]I just had to downgrade my xserver ... The answer sponsored by "DeGrijze":[/FONT][/COLOR]

[/SIZE][/FONT] 				 				[FONT=Arial][SIZE=2]**Re: Lucid xserver update breaks "glxgears", etc.**[/SIZE][/FONT] 			
 			 			 		   		 		 		[FONT=Arial][SIZE=2]To fix this problem 4 now i just downgraded back 2 version be4 the downloaded and installed updates.

[/SIZE][/FONT]   	[FONT=Arial][SIZE=2]Code:[/SIZE][/FONT]
 	[FONT=Arial][SIZE=2]sudo aptitude install xserver-common=2:1.7.6-2ubuntu7[/SIZE][/FONT] 
[FONT=Arial][SIZE=2]and

[/SIZE][/FONT]   	[FONT=Arial][SIZE=2]Code:[/SIZE][/FONT]
 	[FONT=Arial][SIZE=2]sudo aptitude install xserver-xorg-core=2:1.7.6-2ubuntu7[/SIZE][/FONT] 
[FONT=Arial][SIZE=2]And after reboot all works again.[/SIZE][/FONT]

Thanks for everybody

---

### Post by pme 72 on 2011-10-19
A fix has been posted on the previously mentioned Launchpad page:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/877905)

It just involves running Update Manager. 

Seems to be working for me.

---

