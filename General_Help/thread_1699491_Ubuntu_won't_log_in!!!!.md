---
title: "Ubuntu won't log in!!!!"
date: 2011-03-03
forum: General Help
---

### Post by HE_Serenade on 2011-03-03
All right! let's see.... URGENTLY NEED HELP!!!!!!!!!!!!!!!!!!!

OK... This post is a part from [THIS ONE]("http://ubuntuforums.org/showthread.php?t=1698482")... As I didn't get any replies, I decided to post this one in this "General Help" side... I dunno if this is OK but I'm desperated!

I've messed it up REALLY aweful this time!

Ok... Trying to set this "Cyborg R.A.T. 3" mouse into ubuntu I tried to do something  for my own...(bad idea :( ) after reading A LOT of forums and searching through  Google, I decided to make modifications inside a folder called  "/usr/lib/X11/xorg.conf.d" <------ this xorg is a FOLDER, not a gedit  file (at least I see it like this) 

Anyways, this folder contains some gedit files... ".conf" files that  seemed to be X sections to make peripherals (input thingys) work in Ubuntu. so I  ran a code:
     ```
gksu gedit /usr/lib/X11/xorg.conf.d/10-mouse.conf 
```And pasted this inside:

```
Section "InputClass"   
    Identifier "Mouse Remap"   
    MatchProduct "Saitek Cyborg R.A.T.3 Mouse"   
    MatchDevicePath "/dev/input/event*"   
    Option "ButtonMapping" "1 2 3 4 5 6 7 0 0 0 0 0 0 0" 
EndSection
```Then I saved and decided to restart my PC to see what happens... and SHT HAPPENS! :'( 

It doesn't log into ubuntu!!!!!... it freezes in the purple ubuntu loader!!!!!...  I tried to access a "recovery mode" partition with GRUB and it loads A  LOT of info to conclude after a while with:

"Gave up waiting for a root device" (this surrounded by a lot of other info)

and it finishes with:

(initramfs) <----- here I can type stuff but its not a "terminal"

I've been looking all over the internet for a solution for this but I don't seem to find it... I've seen things like this, but NOT EXACTLY this... I've already tried a couple (deleting the "search" line pressing "e" in grub", deleting the "quiet" word, changing some stuff in the "root=", etc...)

So the thing is.... I need your help to either access to my folders to  delete that .conf file I created or just log into ubuntu normaly to do  the same. I'm sure that's the file that's messing all up so I just need  to rm it.

Any suggestions???

Thanx anyways....
 


....and forgive my stupidity! :oops:

I shouldn't try to do these things just because I see them logic!

---

### Post by davidmohammed on 2011-03-03
suggest boot from a live CD - you'll be able to see your hard-drive from there.  You can then undo your change before rebooting.

---

### Post by HE_Serenade on 2011-03-03
Do I need a 10.04 Live CD to do this.... right now I just have a 7.10 live CD and i couldn't access the my HD.... probably version uncompatibility?

---

### Post by davidmohammed on 2011-03-03
its likely you are using an ext4 filesystem - so the v7 ubuntu will not work.  Yes you'll need a 10.04 CD.

---

