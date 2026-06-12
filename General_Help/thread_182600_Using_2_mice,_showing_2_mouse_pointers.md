---
title: "Using 2 mice, showing 2 mouse pointers?"
date: 2006-05-26
forum: General Help
---

### Post by peaceful_dragon on 2006-05-26
This is a pretty weird request, I'll have to admit, but here goes.

I work in software development, and my co-workers and I are debugging side-by-side a lot of the time.

To facilitate this, I've actually set up two sets of keyboard and mice at my station. It prevents us from having to shuffle seats all the time. This by itself is already helping a lot.

Now here's the kicker. Is it possible to somehow get TWO mouse pointers to appear on the screen? Right now both mice control the same pointer, which means we basically have to tell each other "okay, you have the mouse" all the time.

It would be a HUGE productivity boost if I could control my set of input tools independently from his. Then I could (say) edit code, while he (say) debugs in a debugger, at the same time.

Any ideas?

---

### Post by gumbald on 2006-05-26
But you could only have one active application...? You can still only work one at a time. It is a rather weird request! :)

---

### Post by tribaal on 2006-05-26
Hum, I just bumbed into your post, and actually we would also benefit a lot from this kind of setup at work.
So no idea on how to make it work, but I'll be looking into this as well.

You're not alone! :)

- trib'

---

### Post by peaceful_dragon on 2006-05-31
[QUOTE=gumbald]But you could only have one active application...? You can still only work one at a time. It is a rather weird request! :)[/QUOTE]

Actually, what I *would* like is to have two active applications!

---

### Post by gumbald on 2006-05-31
What's the gain doing this? I'm still confused: how would this benefit you over having two computers with screens next to each other? You can still access the same files as each other...

---

### Post by peaceful_dragon on 2006-06-01
[QUOTE=gumbald]What's the gain doing this? I'm still confused: how would this benefit you over having two computers with screens next to each other? You can still access the same files as each other...[/QUOTE]

Well, if I have a debugger paused at a particularly difficult condition (maybe after an hour or two of execution time), I wouldn't want my colleague to have to run the darn thing again on his machine, right?

And, if we're debugging interactively with each other, instead of using my FINGER to point at something, I can use my (other) mouse and drag it around without having to tell him "Wait, I need the mouse".

---

### Post by gumbald on 2006-06-01
So if you are both looking at the same thing, why two active applications?

---

### Post by lledurt on 2007-07-12
I would like to do this too.  Have you anyone figured it out.  I want to cut with one had and paste with the other.  I have a large desktop and I think I can be much more productive with this.
P.J.

---

### Post by bodhi.zazen on 2007-07-12
1. Back up xorg.conf.

2. Edit xorg.conf to include :

A unique section for each mouse ( I advise 1 USB and 1 serial)

Section "InputDevice"
    Identifier "Mouse0"
    Driver  "mouse"
    Option "Protocol"    "IMPS/2"
    Option "Device"      "/dev/input/mice"
    Option "Button"      "5"
    Option "ZAxisMapping" "4 5"
    Option "SendCoreEvents"  "yes"
EndSection

Section "InputDevice"
    Identifier "Mouse1"
    Driver  "mouse"
    Option "Protocol"    "IMPS/2"
    Option "Device"      "/dev/input/mice"
    Option "Button"      "5"
    Option "ZAxisMapping" "4 5"
    Option "SendCoreEvents"  "yes"
EndSection

**Adjust to your mouse settings, do not copy and paste those sections** ;)



Next, in the Section "ServerLayout", add these lines :

        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Mouse1" "SendCoreEvents"

OR, if that fails, use "AlwaysCore" (Remove "SendCoreEvents")

InputDevice "Mouse1" "AlwaysCore"

---

### Post by asmoore82 on 2007-07-13
^^ All that is to successfully share one pointer between 2 or more mice.
Which is fairly automagic across the board these days.

Sorry dude, I too would appreciate a "Dual Pointer" ability, but it's not yet possible...
[http://www.freedesktop.org/wiki/MultiplePointers](http://www.freedesktop.org/wiki/MultiplePointers)

Adam sM

---

### Post by dagnabit dang doohickey on 2007-07-13
[MPX - The Multi-Pointer X Server]("http://wearables.unisa.edu.au/mpx/")

[This is a recent video of MPX]("http://www.youtube.com/watch?v=0MUOn_nJmRA") in action on YouTube.

---

### Post by djester on 2007-07-17
Just a note.  Instead of setting up two keyboards and mice.  I use Synergy ([http://synergy2.sourceforge.net](http://synergy2.sourceforge.net)) only I set up a server on both my computer and my co-workers computer, and a client on both that way we can use eachothers desktops from our same mouse and keyboard.

Though it might help a bit.

---

### Post by vector1 on 2007-09-11
i am a drafter.. i have one monitor on my side of
my desk and one monitor on the front side so when
the architect or engineer comes in to see what i'm
doing they don't have to breath down my neck..
they are seeing the same thing on the screen as i
see.. but obviously they sometimes need to POINT
to something on the screen.. how are they going to
do this without their own independant mouse pointer? right now i DO have two mice.. but they
both operate ONE pointer and it gets confusing when
i am moving my pointer and all-of-a-sudden the 
pointer starts moving in a different direction if
they don't TELL me they are about to move it.. but
if they had their OWN pointer (different shaped)
they could point at things and i could continue
working and could see what they were pointing at
without disturbing MY pointer.. must be 
someone out there that can understand this..
(everyone so far keeps saying it don't make sense
to them)

---

### Post by ewloe on 2007-09-11
I understand your problem but unfortunately I have no solution.

try rewording your problem it may help you come up with a solution, like

I want my client/co-worker to be able to point to areas of my screen with out it affecting my mouse controls. 

that as I understand is your problem maybe the solution is not two mice they could be another way but what that is I don't know.

A simple solution although not very professional looking is to divide the screen into a grid and they could refer to a grid reference instead of pointing. which has just given me an idea although I would not know how to program it but here it is.

on your clients screen you have a grid or they have a touch screen like you get on PDAs if they want to refer to something they either touch it with a light pen or type in a grid reference then on your screen that area would flash in some way to get your attention.  

hope this is of some help just thinking on my feet here but I would love to here if you find a solution.

---

### Post by scalawag on 2007-09-11
I can understand fully the want, if not need, for this feature.  The MPX site referenced above has a link to download a live-cd version, I'm at work at the moment, but will try this later on and report back if I have any success with it.

I've got a coupld of applications I'd like to utilize a feature such as this for.  One is I have a touch display I plan on mounting directly in front of my monitor (cutting a square out of the work surface and litterally mounting the device like a portion of the table,)  I'd like to use this as a seperate disply with seperate controls but running off the same box.  This display will have multiple purposes, but among them will be a seperate display to monitor security, network traffic, etc keeping my working display clear of this clutter.  Another feature is to use this display as a litteral drawing board, keeping reference images and data displayed on my main monitor so I merely have to glance up then continue with what I am doing, no need to minimize reference pages or change to an alternate workspace, it'll be right there in front of me.

Will be some time before I get the second display, get it installed, and configure it, so, will not be able to relay my findings for a while.  I will try to let you all know how the live-cd works for me though.

---

### Post by vector1 on 2007-09-12
thanks ewloe.. 
here is my re-wording like you suggested..
it really is important to get the wording right
because i may need it on a long journey
looking for a solution because i really do
need this..

i am a drafter.. i have one monitor on my side of
my desk and one monitor on the front side so when
the architect or engineer comes in to see what i'm
doing they don't have to breath down my neck..
they are seeing the same thing on the screen as i
see.. but sometimes they need to POINT to something
on the screen.. if they WERE breathing down my neck
they would reach over my shoulder and POINT with their
FINGER- and this is why i like the second monitor..
BUT- as it is now they have to use a second mouse
that controls the pointer just like my mouse does and 
it gets confusing when we pull the pointer away from
each other.. what i need is something that will place
a second pointer (different shape) on the screen that
moves independently from my mouse pointer and be 
controlled by them..

i can disable both buttons and wheel on that second
mouse- just have it move a pointer or big dot or something..

i have had many people tell me this cannot be done- but
i really need it.. does anyone have any ideas?

i'm hoping this makes it clear..

---

### Post by ewloe on 2007-09-12
don't know if this is possible but if you dont want the othe pointer to have any other function than to point then this must be worth trying

you would have to get it made though

get two clear LED screens the same size as your monitors one screen as pressure points on it that relate to flashing leds on the other screen, when your client presses their screen the corresponding area on your screen flashes (well it would actually be in the led screen) but if configured correctly it would work, I know you can get clear led screens cos I use to have a watch made from one.

hope this helps or gives you further ideas that might work.

good luck

---

### Post by hessiess on 2007-09-12
not exactily the same, but i think ti would be good to have multiple controles, for example, multiplyer gaming on split screen/ multiple monitors using 2 separate keybords and mice, or outher controal divice. i think the only way to do this on a pc at the moment is via a network using 2 computers

---

### Post by vector1 on 2007-09-13
thanks again ewloe for trying to help me..

i think the wording of this problem is very important before i 
go on an internet wide hunt for a solution..

here is another re-wording:

i am a drafter.. i have one monitor on my side of
my desk and one monitor on the front side showing the 
exact same thing.. so when the architect or engineer 
comes in to see what i'm doing they don't have to breath
down my neck looking and pointing at my computer screen..

i also have TWO mice connected to my one computer so
both move the one pointer showing on the two screens..

the only problem is that we both try to move the
pointer at the same time and we never know which one
of us has control..

what i need is something that will place a second
pointer (different shape) on the screens that move 
independently from the primary pointer and primary
mouse..

i don't want the second mouse pointer to have any
functionality other than to move a cursor for 
pointing.. (i can disable the buttons on the mouse)

i'm using Windows XP sp2

any ideas or referrals to web sites or email addresses?

---

### Post by bodhi.zazen on 2007-09-13
I think we all understand what you want, two independent mice with two independent mouse pointers on the screen.

It is a cool idea, but no one knows how to do that.

---

### Post by Xavier Oddmon on 2007-09-16
@Vector 1
You say you're using windows XP? I have a really cool program called "GlovePIE", which is glove programmable input emulator. It supports everything from wiimotes to rowing machine inputs, and it can do this kind of thing (that's why i got it).

it's really simple to configure, you'd simply put something like this in the box:

```

if !(keyboard.shift) //press shift if the program hijacks your mouse.
   cursor1.visible = true
   cursor2.visible = true
   cursor1.x = cursor1.x+delta(mouse1.x)
   cursor1.y = cursor1.x+delta(mouse1.y)
   cursor1.LeftButton = mouse1.LeftButton
   cursor1.MiddleButton = mouse1.MiddleButton
   cursor1.RightButton = mouse1.RightButton
   cursor2.x = cursor1.x+delta(mouse2.x)
   cursor2.y = cursor1.x+delta(mouse2.y)
   //note i didn't include the input for the second mouse, so it can be used a a pointer.
endif

```


hit run, and what do you know, two mice

(you may want to write your own code, I'm in ubuntu right now, and glovepie is useless in wine. this code wasn't tested at all, just came off the top of my head.)

this is probably the greatest software i've downloaded for windows, i can play games like trackmania with a wiimote.

---

### Post by lledurt on 2007-11-12
I had a different thread on this,  

[http://ubuntuforums.org/showthread.php?p=3009086#post3009086](http://ubuntuforums.org/showthread.php?p=3009086#post3009086)

and someone suggested a product called MPX.

It was beyond my ability (or time constraints) to get it working on my ubuntu, but you might want to give it a try.  I ran the live cd and the demo worked.

[http://wearables.unisa.edu.au/mpx/](http://wearables.unisa.edu.au/mpx/)

P.J.

---

### Post by djbsteart1 on 2008-01-08
surely dual apps can be done with dual monitors?

---

### Post by nmz787 on 2008-04-21
I wrote up this MPX howto for Gutsy 7.10

[http://jisag.rit.edu/MPX/mpxhowto.html](http://jisag.rit.edu/MPX/mpxhowto.html)

---

### Post by brnetonboy on 2008-06-10
> **nmz787 said:**
> I wrote up this MPX howto for Gutsy 7.10

[http://jisag.rit.edu/MPX/mpxhowto.html](http://jisag.rit.edu/MPX/mpxhowto.html)

The link is broken! I am desperate for a MPX howto!

---

