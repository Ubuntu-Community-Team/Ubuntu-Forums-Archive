---
title: "The Application &quot;gnome-panel&quot; has quit unexpectly."
date: 2005-02-10
forum: General Help
---

### Post by Seiken on 2005-02-10
Hi Everyone,

Former Windows user here... got tired of XP dying on me, so I'm trying Ubuntu with the Live CD.

I've tried starting with the default options, with ACPI, and by copying to RAM first. If I copy to RAM first, it doesn't boot at all.

With the other 2 options, as soon as Gnome starts, I get the following message:

[I]Error

The Application "gnome-panel" has quit unexpectedly.

You can inform the developers of what happened to help them
fix it. Or you can restart the application right now.

'Restart Application'     'Close'     'Inform Developers'[/I]

"Restart Application" does nothing, and "Inform Developers" is a little too complicated for me at this point. I did search through it as far as I knew how, but didn't see my problem listed there.

So since gnome-panel doesn't get to start, I have no panel at all. No toolbars anywhere, just "cdrom" and "ramdisk" on my desktop. If I want to run Firefox, I have to either find the binary or an html file on the cdrom.

Any suggestions?

Thanks,
Seiken

---

### Post by Seiken on 2005-02-10
if I run gnome-plan from /user/bin, I get the same error.

---

### Post by Seiken on 2005-02-11
Could someone at least point me in the direction of where some CD burning software might be on the Live CD so I can backup my other partitions?

Thank.

---

### Post by Seiken on 2005-02-13
Is it possible I just did a bad burn? Would that do it?

---

### Post by zanee on 2005-02-25
I get the same problem.. This is annoying and has killed my desktop essentially. There are no debugging symbols. So I can't debug this

[Switching to Thread 16384 (LWP 11287)]
0x0000002a99221790 in strlen () from /lib/libc.so.6

Is all i'm able to get. This is my work desktop thats screwed.. So i've been screwing aroudn with this for the last 3-4 hours.. Not good.

---

### Post by eldrich_rebello on 2005-02-25
try acpi off.what about failsafe?results?i'd say ditch the live cd,make a spare partition and do an install!

---

### Post by moon2js on 2005-05-03
My gnome-panel also tends to unexpectantedly quit at startup as well, and I'm not running a live CD, rather it's a regular almost fresh installation of hoary. It's quite a frustrating because as soon as I hit the "close" button, the same error message comes back up. If I hit the "restart application" button, it will tell me that an instance of gnome-panel is already running and then go back to the same "The Application "gnome-panel" has quit unexpectedly" error cycle.

I'm not incredibly experienced in the world of gnome but because it locks me into this dialog with the cycling error message, my system is effectively useless and I had to kill the x server to get out.

I have since come home, and it boot up without that error at startup so I don't know what to make of it. Is it because I was trying to do wifi? Here at home, I have a wired connection, but I don't see how my networking could have an effect on my panel...

---

### Post by joaoeb on 2005-06-04
[QUOTE=moon2js]My gnome-panel also tends to unexpectantedly quit at startup as well, and I'm not running a live CD, rather it's a regular almost fresh installation of hoary. It's quite a frustrating because as soon as I hit the "close" button, the same error message comes back up. If I hit the "restart application" button, it will tell me that an instance of gnome-panel is already running and then go back to the same "The Application "gnome-panel" has quit unexpectedly" error cycle.

I'm not incredibly experienced in the world of gnome but because it locks me into this dialog with the cycling error message, my system is effectively useless and I had to kill the x server to get out.

I have since come home, and it boot up without that error at startup so I don't know what to make of it. Is it because I was trying to do wifi? Here at home, I have a wired connection, but I don't see how my networking could have an effect on my panel...[/QUOTE]

 I had the same problem. Solved by deleting the .recently-used folder in my home directory:

rm -R .recently-used 

Don't panic, it will come back :)

My case was a parse error, caused by some strage character in a filename from a windows share...
 :roll:

---

### Post by ipguru99 on 2005-06-06
I love this distro!... and this forum.  This 'gnome-panel' is gone message totally threw me.  I have been trying all kinds of things... then I think, 'hey, go back to ubuntuforums.org... they have always had the answer so far...'

And here it was again.

Thanks to everyone who shares HOW they fixed it!!

---

### Post by asarwate on 2005-06-10
Removing .recently-used didn't actually solve the problem for me.

I tried reinstalling gnome-panel (and all of gnome actually) and that also didn't help.  Other things that quit unexpectedly are nautilus, the volume applet (or any other applet), the virtual desktop manager, etc.

One other thing that fails the the right-click on the mouse -- normally it pops up a window so I can get a terminal, etc, but in the process of restarting gnome-panel it kills that behavior for some reason.

Anyone else have a different fix?

---

### Post by xbaez on 2005-06-27
If you are going to leave Ubuntu because of this messy Gnome gnome-panel program, I suggest this:

1) Synaptic
2) install 'kubuntu-desktop'

KDE is amazing, I'm trying GNome for 2 reasons
1) Most tutorials and everything is written for Gnmoe, so I'd just like to give it a shot since Ubuntu promotes it so much
2) I think that in my house (celeron 1.8 ghz, laptop) were Window$ XP takes FOREVER to load  and KDE isn't as faster as in my office computer, Gnome will perform better

If I don't find a solution soon I migth just end using Xfce or something really light

That's cool about Linux, you get to chose between three displays managers, so don't you leave Ubuntu for this!

Regards

Xavier

---

### Post by xbaez on 2005-09-28
I am running gnome and it works ok
but I have one problem
whenever I click ALT+F2, gnome-panel produces an error
How can I fix this? Any ideas?
I tried removing the .recently-used file with no luck

---

### Post by Biagio on 2005-10-21
[QUOTE=joaoeb]I had the same problem. Solved by deleting the .recently-used folder in my home directory:

rm -R .recently-used 

Don't panic, it will come back :)

My case was a parse error, caused by some strage character in a filename from a windows share...
 :roll:[/QUOTE]
Thank's a lot...... for all!
;)

---

### Post by Grafster on 2005-10-29
I have the same problem. Its a big deal. I've managed to (with much errors and restarting the damn thing over and over again) get most everything back the way it was before but I still can't see the programs that are running.

What is the "show currently running applications" thing called?
Is this actually not a problem in KDE or was that just distro pimping? (I know gnome and kde aren't distros but... whatever... its all the same to newbies)

(sorry using Breezy ... didn't realize this was originally a warty problem. Shame this is still an issue after all these upgrades.)

---

### Post by limmy on 2006-10-22
> **Grafster said:**
> What is the "show currently running applications" thing called?

This happened to me. Adding "Window List" to the panel got me the "show currently running applications" back.

---

### Post by chocbar31 on 2006-10-23
> **xbaez said:**
> If you are going to leave Ubuntu because of this messy Gnome gnome-panel program, I suggest this:

1) Synaptic
2) install 'kubuntu-desktop'

KDE is amazing, I'm trying GNome for 2 reasons
1) Most tutorials and everything is written for Gnmoe, so I'd just like to give it a shot since Ubuntu promotes it so much
2) I think that in my house (celeron 1.8 ghz, laptop) were Window$ XP takes FOREVER to load  and KDE isn't as faster as in my office computer, Gnome will perform better

If I don't find a solution soon I migth just end using Xfce or something really light

That's cool about Linux, you get to chose between three displays managers, so don't you leave Ubuntu for this!

Regards

Xavier


Actually, this morning this worked for me.

sudo aptitude install ubuntu-desktop

Fixed my gnome panel...saw this in another post!

Seems I deleted a needed file while removing some gstreamer plugins. I guess this is also why Automatix2 will not remove these plugins once it installs them.

---

