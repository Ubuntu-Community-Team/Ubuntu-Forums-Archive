---
title: "Bug beats linux   help!"
date: 2010-03-02
forum: General Help
---

### Post by mjad on 2010-03-02
I got a bug in Ubuntu
Nothing would remove it
Used a clean disk to destroy everything on the hard drive
reinstalled clean ubuntu disk
STILL THERE!
Spreads to Mandrake on eec pc   and live Slax, live ubuntu, 

The bug  makes the mouse malfunction, unrequested programs start then mouse just freezes on screen
on eec pc just stoped the mouse pointer working totally (after using a usb stick from laptop with the problem
keeyboard commands (alt 'x' etc still work)

Im not a geek, I need a simple answer of where this bug is and how to get rid of it

I understand hard drive and simple terms 
HELP

---

### Post by bodhi.zazen on 2010-03-02
I moved this from security to general help.

Hard to tell from your description, but my guess is a hardware problem.

---

### Post by cdenley on 2010-03-02
> **mjad said:**
> 
Used a clean disk to destroy everything on the hard drive
reinstalled clean ubuntu disk
STILL THERE!


Well then it isn't some sort of malware, unless you did something to infect it after reinstalling. Do you have another mouse you can try? Do you have the same issue while running a livecd?

---

### Post by steveneddy on 2010-03-02
Are we talking about an external mouse connected via a USB stick? 

or the touch pad on a laptop?

If laptop, post specs and model number if available.

What version(s) of Ubuntu are you using/trying?

How did you install Ubuntu? CD - USB - Network

If a wireless mouse, have you tried changing the batteries?

Have you tried other wireless mice or even a wired mouse of some sort?

---

### Post by mjad on 2010-03-02
mouse pluged into usb was not recognised
live cd makes the same problem

---

### Post by bodhi.zazen on 2010-03-02
> **mjad said:**
> mouse pluged into usb was not recognised
live cd makes the same problem

Most likely a hardware problem, can you try a different mouse.

---

### Post by mjad on 2010-03-02
> **steveneddy said:**
> Are we talking about an external mouse connected via a USB stick? 

or the touch pad on a laptop?

If laptop, post specs and model number if available.

What version(s) of Ubuntu are you using/trying?

How did you install Ubuntu? CD - USB - Network

If a wireless mouse, have you tried changing the batteries?

Have you tried other wireless mice or even a wired mouse of some sort?
touch pad
laptop e machines d620
it tranfered to an eec pc netbook via a usb stick
ubuntu version 9.10
installed via cd
touch pad and usb mouse tried but was not recognised

---

### Post by mjad on 2010-03-02
> **bodhi.zazen said:**
> Most likely a hardware problem, can you try a different mouse.
if its hardware why would it transfer to another computer via a usb stick?

---

### Post by bodhi.zazen on 2010-03-02
> **mjad said:**
> if its hardware why would it transfer to another computer via a usb stick?

I do not know the cause of your problem from the description you posted. When one has a problem across multiple operating systems and multiple live CD I tend to feel it is somehow hardware related.

---

### Post by timsdeepsky on 2010-03-02
Corrupted download??....Hardware??....

---

### Post by cdenley on 2010-03-03
Many touch pads use a tap-click. This means if you touch the touch-pad too hard while attempting to move the cursor, it can register as a click. I seriously doubt there is any malware which interferes with the use of your cursor. You're almost certainly mistaken about it being a "bug" transferred via removable storage. I agree it is almost certainly a hardware problem or simply a touchpad configuration which makes it difficult to use.

---

### Post by mjad on 2010-03-03
> **cdenley said:**
> Many touch pads use a tap-click. This means if you touch the touch-pad too hard while attempting to move the cursor, it can register as a click. I seriously doubt there is any malware which interferes with the use of your cursor. You're almost certainly mistaken about it being a "bug" transferred via removable storage. I agree it is almost certainly a hardware problem or simply a touchpad configuration which makes it difficult to use.
I take your point but 
1. I don't have to touch the touch pad for the problem to start with windows popping up all over the place
2 whilst i would agree it might be hard ware that dosen't explain why when i used a usb stick to transfer files to another computer the mouse froze on the other computer and hasn't worked since

---

### Post by mjad on 2010-03-03
in general to the suggestion that it is a hardware problem:

why does it spread from one computer to another?
I transferred a file from the ubuntu computer to one using mandrake and as soon as done (via a clean usb stick) the mouse no longer worked on the second computer and hasn't done scice.

---

### Post by cdenley on 2010-03-03
> **mjad said:**
> in general to the suggestion that it is a hardware problem:

why does it spread from one computer to another?
I transferred a file from the ubuntu computer to one using mandrake and as soon as done (via a clean usb stick) the mouse no longer worked on the second computer and hasn't done scice.

So on one computer, you have windows popping up? Are these browser windows? Applications? Which application? Was there anything open or running.

On your second computer, if your mouse stopped working after using a usb storage drive, that sounds like an entirely different problem to me.

---

### Post by mjad on 2010-03-03
its like the mouse travels all over the screen and cliks programs into operation without me doing anything.  it seems fairly random. it can be calander, write, terminal, almost anything after which the computer just locks. If I restart it will go a while and then start again. It does this on hd ubuntu, live ubuntu and live slax.

---

### Post by deadlockedgamer on 2010-03-03
lol only thing I can think of is the prank usb thing on think geek that randomly moves your mouse. Maybe the usb drive is defective or the pc you are transferring form has a bad usb port?

---

### Post by robert shearer on 2010-03-03
Are you at your workplace ??

Look around you for the colleague trying not to laugh.

Are you at home ? Alone ?
Unplug your network connection awhile and see if the mouse behaves.

Post back you findings

---

### Post by mjad on 2010-03-03
no network connection and sadly no one laughing at this this end
unless you mean the inteernet

---

### Post by sandyd on 2010-03-03
ive encountered this problem before, after thumping my touchpad in fustration after one of my bug patches fried my own system. It moved by itself. It clicked by itself. and it was a pain in the rear. It turned up being permantly damaged :(

you might want to try this.

add this to xorg.conf
```

Section "InputDevice"

Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "on"
Option "MaxTapTime" "0"
EndSection

```then open up gnome-mouse-properties

disable the touchpad.
see if that helps.

---

### Post by robert shearer on 2010-03-03
> **mjad said:**
> no network connection and sadly no one laughing at this this end
unless you mean the inteernet

 I meant that it sounds like someone playing a prank using a swapped mouse (colleague) or someone controlling your desktop remotely (unplug network cable . yes = the internet).





Sometimes stepping back for the big view can help hence my post.

The mouse behavior is so odd and across so many different hardwares, reinstalls and distros that outside influence seems much more likely than  malware.

> 2 whilst i would agree it might be hard ware that dosen't explain why when i used a usb stick to **transfer files** to another computer the mouse froze on the other computer and hasn't worked since

What were the files you transfered ??

As two machines are involved have you by chance tried to set up filesharing on them recently??

Have you tried another mouse ? If the one you are using has a cable fault/short and you have been moving it between machines then this could be causing hardware failures.

---

### Post by mjad on 2010-03-04
thanks to Carlee and Robert.
its 6 am here and ive been up all night working on other things
so after a long sleep I will get back to you
have a nice day while I sleep

---

### Post by mjad on 2010-03-07
this seems very close to my problem.
as i am an absolute beginner:
how do I find xorg.conf
then if i manage this where do i find gnome mouse properties
can the above cause further problems and if so can I reverse it
finally is there any way that this problem can be caused by running a program or file
I think this started after I played a film loaned by a friend that he got from the internet and saved on dvd

---

### Post by deadlockedgamer on 2010-04-25
the xorg.conf may not exist and need to be created depending on which ubuntu you are using, what version are you running? The mouse preference is system-preference-mouse on your menus! :)

---

