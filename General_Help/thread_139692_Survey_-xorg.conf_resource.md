---
title: "Survey -xorg.conf resource"
date: 2006-03-04
forum: General Help
---

### Post by Prospero2006 on 2006-03-04
I was thinking about putting together a website that would allow folks to upload, search for, and download working xorg.conf files. With as many different configurations as there are out there, it might be a handy resource for folks.

Two questions:
       -Should I take the time to develop it? 
       -How should I organize listings do you think?

                 -Thanks, 
                     Pros

---

### Post by incubus on 2006-03-04
pros,

The big problem, as you know, is that xorg.conf will vary significantly computer to computer. Although you may advise otherwise, many people will simply replace their file, break X, and freak out. For example, resolution modes and refresh rates will typically be different for different installations.

I strongly agree that a centralized source of information is very useful. Neat instructions on how to install nvidia, ati, and other drivers, as well as other fine adjustments would encourage more people to try.

How about a Wiki?

incubus

---

### Post by Prospero2006 on 2006-03-04
That's actually exactly the kind of feedback I was looking for.
I just know that setting up my dual-head was a real pain to get right.

Here's a question:
   -If I order a nice shiny 21 inch monitor, is it possible I'll destroy the thing
    with bad xorg.conf settings? (How can I make sure I won't burn
    a new monitor.)


                  Thanks, 
                    Pros

---

### Post by incubus on 2006-03-04
Dear Pros,

I know exactly how you feel. Although google is helpful, distros may have different configs because of different versions of drivers.

What may be easier to do is to work on Ubuntu's Wiki and include the information/experience we have gathered, starting with your dual-head.

Regarding your concern, yes, forcing the monitor to use wrong refresh rates can cause actual damage (not explode, but reduce durability in the long run). Most of the times this won't happen as xorg.conf is typically set to conservative rates. To be sure, you should always check your monitor's manual, this information is there.

So you could start a "tips and tricks" or wiki entry and show people what you had to do to make it work. Just check to see if someone hasn't done this already.

incubus

---

### Post by Prospero2006 on 2006-03-04
I have to say, inc, you're a pessimist.
I've got 2 or three old monitors sitting in my garage right now. 
I'm going to put your 'they won't explode' philosophy to the test. 


I'll let you know!

Pros

---

### Post by incubus on 2006-03-04
Yep! Be sure to have a fire extinguisher around! ;)

Sorry for sounding pessimistic. The intention was the opposite, I meant to support your idea. Just pointed something that could give you some complaints in the future. 

I don't believe you're gonna fry any monitors around (newer ones have protection mechanisms). But I think people will copy 'n paste xorg.confs without reading your instructions, see X failing, and write you a furious email.

I may be (and I hope I am) totally wrong. This is just my opinion. Wait for feedback from other people.

By the way, check this out:
[http://linuxgazette.net/124/smith.html]("http://linuxgazette.net/124/smith.html")

incubus

---

### Post by Prospero2006 on 2006-03-05
Aha, 

You misunderstood me.
I didn't mean to imply that you were pessimistic about the xorg repository. 
I think you're right.

I meant to imply that you were pessimistic about the idea that a man can't
set a monitor on fire from the command line. 

There is no try. Only do.

Pros

---

### Post by az on 2006-03-05
Editing the file by hand is not the way to go.  If there are customisations to be made, that is a package management thing.  There should be some scripts in the xorg package for this and a frontend to those scripts.

---

### Post by incubus on 2006-03-05
Oh, yes, absolutely. I'm definitely pessimistic about that, no doubt about it. :) 

I agree with azz that we should invest some time creating scripts or even GUIs to make the process easier. I love tweaking these things by hand, but I aknowledge that this kind of attitude will only keep people away from Linux.

GUIs and scripts, however, require much coordination and programming skills. Prospero's idea is easy to implement and anybody with some experience can contribute.

I wonder what proportion of new comers are aware of Ubuntu Official Wiki. This page, in my opinion, is a little messy in some parts too.

incubus

---

