---
title: "Downgrade Firefox back to 3.0"
date: 2009-09-04
forum: General Help
---

### Post by TheIdiotThatIsMe on 2009-09-04
Hi guys,

I recently "upgraded" my Firefox to 3.5 in 9.04, and ended up with something called Shiretoko. I'm guessing it's the release name or prerelease name of 3.5. Anyways, it seems to have removed the Firefox branding and disabled my Ubuntu add-ons, and replaced my 3.0 install, and I'm not really to in to it. Is there a way to downgrade back to 3.0?

---

### Post by x33a on 2009-09-04
```
sudo aptitude remove firefox-3.5
sudo aptitude install firefox-3.0
```

---

### Post by Vaphell on 2009-09-05
look for 3.0 in synaptic and install it
besides did it replace completely? run terminal and write firefox[Tab][Tab]
it will list every firefox executable present in the system
in my case i had 3 separate for 3.0, 3.5 and 3.6a in my 8.04

---

### Post by starcraft.man on 2009-09-05
3.5 is final and released now. The package doesn't upgrade your existing install of 3.0, it installs along side (in all cases I've seen). If you go to Applications > Internet > Firefox you'll be able to launch it manually. The package is named firefox-3.0 as opposed to firefox-3.5 for the newer version. 

3.5 didn't remove branding, it didn't come with it. I'm not a licensing expert but as it's been for a while I think, Ubuntu only ever applies branding to firefox version that came default not to later releases. As to add ons, it would only disable addons if they were not updated for use with new firefox. If the maintainer of the addons haven't bothered to do so by now, I'd question the addon and his commitment to it. 

3.5 is a nice update, and I suggest ya stick it out a bit longer, it's generally faster and better. If not, just launch 3.0 from menu or in alt + F2 by typing firefox-3.0 . If it did get uninstalled, use above means to locate and install package.

And yes, Shiretoko is simply a code name for development.

---

### Post by TheIdiotThatIsMe on 2009-09-05
Thanks a lot guys!

I have to say, it did install side by side, both 3.0 and 3.5 are installed. Unfortunately for some reason if I try open 3.0 while 3.5 is open, it just opens another instance of 3.5. If I try to open 3.0 while 3.5 is closed, it crashes with:

```
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 578 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by lovinglinux on 2009-09-05
> **TheIdiotThatIsMe said:**
> Thanks a lot guys!

I have to say, it did install side by side, both 3.0 and 3.5 are installed. Unfortunately for some reason if I try open 3.0 while 3.5 is open, it just opens another instance of 3.5. If I try to open 3.0 while 3.5 is closed, it crashes with:

```
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 578 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

To launch FF 3.0 with Firefox 3.5 still opened run this:

```
firefox-3.0 -no-remote
```

---

