---
title: "Devede won't create iso"
date: 2010-04-19
forum: General Help
---

### Post by wharfrat1490 on 2010-04-19
Hello.  Thank you for taking the time to look at my post.

Suddenly, and without any warning at all, Devede will not create an iso.  I have the option checked for that to happen, but when I peek inside the folder, there's just compatible mpgs.  I tried selecting "only covert film filesto compliant MPEG files," to see if the buttons were somehow reversed, but to no avail.  I've searched this forum and Google for someone with the same problem; no luck.  I've also updated to make sure I'm running the most recent stable version.

I'm using 9.10 and GNOME 2.28.1, with Intel T8100 2.10 GHz dual core processor and 3.5 Gb RAM.  Dunno how much of that information is necessary...

---

### Post by nothingspecial on 2010-04-19
Try dd

```
dd if=input of=output
```

if means [COLOR="Red"]i[/COLOR]nput [COLOR="Red"]f[/COLOR]ile

of means [COLOR="Red"]o[/COLOR]put [COLOR="Red"]f[/COLOR]ile

So, probably

```
dd if=/dev/dvd/ of=file_name_you_want.iso
```

But your dvd drive may be mounted somewhere else.

---

### Post by wharfrat1490 on 2010-04-19
Thank you.

Could you be more specific about *use* dd?  I opened a terminal, typed ```
sudo dd
```, input my sudo pw at the prompt and my hdd just sits there and spins...

---

### Post by qyot27 on 2010-04-19
That would be
> dd --help
(generally speaking, *--help* is one of the most common ways to find the help of a program, along with *man [appname]*, or any variation on --help, like -h, --fullhelp, --longhelp, etc.)



But it seems as if there's a problem when it comes to devede trying to pass the folder(s) over to mkisofs, so you'd probably be best off looking at the help for it.  The only time I've ever tried using mkisofs directly was for authoring DVD-Audio discs, but the following (with some tweaking) should work:
```
mkisofs -o output.iso -V volume_label -dvd-video input_directory
```
(where volume_label is what name you want the OS to display as the disc name on insertion, and input_directory holds your VIDEO_TS folder)

---

### Post by nothingspecial on 2010-04-19
You need to tell ubuntu where the dvd dd is using is using if=

usually /dev/dvd/

And tell ubuntu what you want the dvd to be "ripped" to using of=

So "Hey, Ubuntu, I want to rip this dvd " ---- dd if=/dev/dvd

And "I want it to be an iso file with a certain name" ---- of=name.iso

So

```
dd if=/dev/dvd/ of=chosen_name.iso
```

You shouldn`t need sudo (but you might depending on the privaleges of your user).

This is a command line tool. Typing ```
sudo dd
``` will not make a fancy window appear.

---

### Post by nothingspecial on 2010-04-19
What do you want to do with the dvd?

There may be a better way.

---

### Post by wharfrat1490 on 2010-04-19
OK, after some research on dd, the problem (as usual) is me and my poor communication...

I'm trying to author a DVD from a couple AVIs on my hdd, not ripping an image *from* a disk.  I've used Devede successfully in the past to do just that and now it stubbornly refuses to work.  If it's not possible to correct the issue with Devede, suggestions for another utility (hopefully with GUI, I'm a n00b, ya know) would be appreciated. 

I just wanna get the dang thing burned off...

[edit]Shouldn't have replied without checking for new comments.  "Fancy window" - that's funny and I guess I had it coming.  I also should have read the help and probably posted in a better sub-forum.  I guess I'm just not with it today...

What I wanted to do with it was watch the DVD video on a stand-alone player with friends.[edit]

---

### Post by nothingspecial on 2010-04-19
> **wharfrat1490 said:**
> 

[edit]Shouldn't have replied without checking for new comments.  "Fancy window" - that's funny and I guess I had it coming.  I also should have read the help and probably posted in a better sub-forum.  I guess I'm just not with it today...
[edit]

Don`t worry about it. You are just unfortunate that a cli advocate answered you.

If I want to do something once or twice, I launch up a gui.

If I want to do something all the time, I (try to) write a script using cli tools, in my opinion, that is the advantage of linux.

Also, error messages are useful. Apart from the fact that it is easier to post "type this into your terminal", than "click here, then go to the top right and click the X button, then click this, and that ,etc, etc"

Have a look at the package tovid (cli), and more usefully in your case tovidgui - or I think, it may be called, todiscgui.

I hope they work.

Ain`t nothing wrong wanting to use a gui.

---

### Post by wharfrat1490 on 2010-04-19
Yes, I've found scripts to be quite an advantage.  I'm not quite up to writing them, but I copied one that recorded my favorite radio show nicely, until the station changed the format to something streamripper doesn't recognize.  The larger advantage though, for me (and quite possibly other disabled people living on Social Security), is price.  FOSS (OK, OK, with a proprietary codec or two...) enables me to do things I could never afford to on Windows or Mac.

I'm not entirely unfamiliar with the terminal; in fact, I thank Ubuntu and Linux for helping me overcome some command-line fear.  The biggest reason I didn't understand your response was that I didn't ask the right question.  I just expected the terminal to start spitting out some text after a moment or so, is all.  Thank you for being patient with me.

I think I'll just tunnel the mpgs to Windows and use DVDShrink or something.  I'm sorry if I've been any bother.

---

### Post by ron999 on 2010-04-19
..........

---

### Post by msd2008 on 2010-06-17
Have you managed to find an answer for this one.

I am having the same issue trying to convert my AVI's to an ISO (to burn to DVD). I have been using Devede for while now & it has been working fine.

I am running Ubuntu 10.04.

---

### Post by rbrick49 on 2010-08-16
hello folks my devede wont make iso also i am using ubuntu lucid must be a bug i got an error spumux bug it said I tried again no error but still no iso Iam going to try devede on kubuntu lucid and see what happens willl post outcome

---

