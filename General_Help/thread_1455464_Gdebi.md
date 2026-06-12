---
title: "Gdebi"
date: 2010-04-16
forum: General Help
---

### Post by DeMus on 2010-04-16
In Gedbi, as soon as the installation starts, a window pops up with the bar saying how the installation is at the moment. In this window a tick box is placed to make the window close automatically. I always tick the tickbox but it won't remember that. The next time I have to do it again making it useless: I can also with a mouse click close the window by hand.
In Synaptic it works perfectly, but Gdebi doesn't seem to understand that.
Am I doing something wrong or is this a bug?

---

### Post by DeMus on 2010-04-17
> **DeMus said:**
> In Gedbi, as soon as the installation starts, a window pops up with the bar saying how the installation is at the moment. In this window a tick box is placed to make the window close automatically. I always tick the tickbox but it won't remember that. The next time I have to do it again making it useless: I can also with a mouse click close the window by hand.
In Synaptic it works perfectly, but Gdebi doesn't seem to understand that.
Am I doing something wrong or is this a bug?

Nobody? Am I the only one again?

---

### Post by wilee-nilee on 2010-04-17
I suspect since your installing a downloaded program rather then from apt-get or synaptic that it is program exclusive. I use gdebi but it has been awhile so I don't exactly remember if it holds that tick to close in place.

I think your correct now that I think about it.

---

### Post by uRock on 2010-04-17
DeMus, Sorry to hear, you are having these issues. From the looks of things, I am thinking something may be wrong with the image you burned. I've read that you have already reverted to Jaunty. If you have, then maybe give Lucid a try in a VBox, but download the Daily ISO instead of the beta2. If you don't have the resources or time, that is definitely understandable. I haven't been able to use GDebi yet, because the one program I use it for has no repo for Lucid yet. I have used my Synaptic a few times without the ticker giving me any problems.

Regards,
Ronnie

---

### Post by DeMus on 2010-07-24
After having played around with other distro's (Fedora 13, Suse 11.3, Mandriva 2010) I now am back using Ubuntu 10.04 Ultimate-Edition.
I used Hardy, I used Jaunty, I used Lucid, I used Lucid Ubuntu-Studio and Now the Ultimate-Edition and all of them have the same "bug" with the tickbox which does not want to remember it has been ticked.
It can't be that hard to put a memory into that box, can it? Well, obviously it is difficult because the bug is still there.
Who knows an answer which will help me?

---

### Post by mc4man on 2010-07-24
The problem is that checking that box is not stored anywhere, it only exists within that current Gdebi instance.
(you'll notice that if you ck. it and the re-install from that gdebi  instance the setting holds.

Some possible solutions

if you know python well enough** possibly** in one of the scripts the box could be set to be checked by default, that would resolve getting the progress box to disappear.

Gdebi-gtk  can also be 'set' to auto-close, except it can't till the progress dialogue closes first - so the above would be very beneficial there.

Without knowing how to do that (box checked by default), there is a way to have gdebi-gtk auto close both the progress box and itself - I don't have any issue having it do so, - though it is termed "dangerous". 
( I know what I'm using gdedi on and how to resolve any problems if they arise. (and have seen none..



The ideal method would be to have  the ck. box enabled by default, and then also have gdebi-gtk autoclose, but if you wish I'll tell you how to do the above (close out gdebi-gtk completely after installation is done.

Edit: While I didn't have any issues with the one way I saw, decided I didn't like it - basically having gdebi-gtk run as non-interactive and autoclose. Nothing to do with "dangerous", there is value to having it in interactive mode and having to click the install button.

So I've now got it running as usual (interactive), but after the install  both the progress box and gdebi close out automatically.

Still couldn't figure how to enable the checkbox by default, so took a guess at reversing what the box 'means', ie unchecked means autoclose

Maybe an improper way to do in a python script, want  to test on other install (did here in source, but may be able to just edit a file.
If it looks good will post - maybe someone who knows python can correct if need be

---

### Post by mc4man on 2010-07-24
**Edit: see post 10 for proper way - this is incorrect...!**

Well - seems to be working as I'd like - a normal interactive Gdebi that closes out automatically after the install.

Went ahead and did as an edit to GDebi.py in lucid (was on maverick before - same thing.

Note that not knowing python at all was just a guess...

So if you wish to try

Open GDebi.py in gedit as root with line #'s enabled  - the line I edited was 521  - marked in blue here

Orig.
> #Close if checkbox is selected
       [COLOR="Blue"] if self.checkbutton_autoclose.get_active():[/COLOR]
            self.on_button_deb_install_close_clicked(None)


Just changed active to inactive - 

```
#Close if checkbox is selected
        if self.checkbutton_autoclose.get_inactive():
            self.on_button_deb_install_close_clicked(None)
```

Saved and all seems well here (obviously don't ck. the box in gdebi, unchecked now means autoclose
Corrections if needed are certainly welcome


Note that Gdebi.py is seemingly in 2 locations, one visible the other not. (both can be opened from cli

I used this 
```
gksu gedit /usr/lib/python2.6/dist-packages/GDebi/GDebi.py
```

---

### Post by DeMus on 2010-07-24
mc4man,

This is it. Can you understand why this has been wrong for so many years? I changed the fie as you suggested and, of course, it works. Thank you so much.
It's not that I use it a lot, but it had been disturbing me from the start. I'll save your comment so I can use it again when I install a new OS.
Thanks again.

Btw, the way I use it is just clicking a .deb file so Gdebi gets started. Nothing fancy at all.

---

### Post by mc4man on 2010-07-25
> Can you understand why this has been wrong for so many years?

Not a clue. the default should be to close gdebi after using. the checkbox should be used to keep it, that single instance,  open.

(As seen there is no real use to keeping it open anyway, all you can do is re-install the .deb you just installed.

In a round about way that's what this edit does, what possessed them to set the default to keep gdebi open is beyond me.


(I'd think anyone who knows python could set the script straight - a default of close after install and if desired, a checkbox to keep that instance of gdebi open

(if gdebi updates then you'll probably need to re-edit, no big deal as you've seen

---

### Post by dodle on 2010-07-30
> **mc4man said:**
> Just changed active to inactive - 

```
#Close if checkbox is selected
        if self.checkbutton_autoclose.get_inactive():
            self.on_button_deb_install_close_clicked(None)
```

Note that this file can also be edited from "/usr/share/pyshared/GDebi/GDebi.py"

First of all, thank you for referring me to this line of code.  I never think to edit others' source files myself.  But this solution actually causes GDebi to crash:
> Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/GDebi/GDebi.py", line 521, in on_button_install_clicked
    if self.checkbutton_autoclose.get_inactive():
AttributeError: 'gtk.CheckButton' object has no attribute 'get_inactive'

You could use "if self.checkbutton_autoclose.blah():" and get the same effect.  That is why you see GDebi close down completely.  The proper way to do it is to edit the line to say this:
```
if self.checkbutton_autoclose.get_active() == False:
```
or:
```
 if not self.checkbutton_autoclose.get_active():
```
Either way is correct.

A better way is to add this line (the line in blue) to the code, after the line that says "SimpleGtkbuilderApp.__init__()" (which resides on lines 73 and 74 on my system, so after line 74):
```
        SimpleGtkbuilderApp.__init__(
            self, path=datadir+"/gdebi.ui", domain="gdebi")
        [color=blue]self.checkbutton_autoclose.set_active(True)[/color]
        # use a nicer default icon
        icons = gtk.icon_theme_get_default()
```

**Make sure that the indentation matches the line below (8 spaces), otherwise GDebi will not run.  Python is sensitive to indentation.**

This sets the check box to "checked" by default and cleanly closes the dialog, but leaves the main GDebi window open after install is complete.  There should be a clean way to close the main window as well.  If I figure it out I will post it here.

---

### Post by mc4man on 2010-07-30
> A better way is to add this line ... 

Excellent - I figured someone you knew python could do properly -( didn't realise it was crashing, packages were installed fine.

Really seems that this is the way it should be, can't see any reason to keep that dialoge box open.

> There should be a clean way to close the main window as well

Actually* for myself* also can't see any reason to keep Gdebi itself open after the package install  - pretty much nothing can be done with that instance but a re-install.

So here edited the gdebi-gtk in the source to set autoclose true as default (in addition to your new line) and rebuilt (*though the file  is also available to edit* in /usr/bin
Do you see any issue there?

 ```
parser.add_option("--auto-close", "",
                      action="store_true", default=True,
                      help=_("Auto close when the install is finished"))
```

---

### Post by dodle on 2010-07-31
> **mc4man said:**
> So here edited the gdebi-gtk in the source to set autoclose true as default (in addition to your new line) and rebuilt (*though the file  is also available to edit* in /usr/bin
Do you see any issue there?

 ```
parser.add_option("--auto-close", "",
                      action="store_true", default=True,
                      help=_("Auto close when the install is finished"))
```

Nice!  It looks like it is closing down nice and clean.  The only problem now is that even if the check box is not checked, gdebi-gtk still shuts down after the install.  It's not a big deal for me, I like it shutting down afterwards.

---

### Post by mc4man on 2010-07-31
> It's not a big deal for me, I like it shutting down afterwards

As mentioned i also can't see any reason for keeping gdebi open - the whole deal with the checkbox is even more pointless unless it was intended for gdebi autoclose


I think if the orig. default had been to autoclose both and the checkbox used to keep the progress box open, well, I guess that would've made a little sense 

( I have learned that the assumption of -  if a parameter is invalid I'd get an error message is a rather poor one, certainly with a python script.

---

### Post by DeMus on 2010-07-31
Thanks guys. I did notice Gdebi closing down completely with the first change in the program, but had no idea it was crashing.
I used the change in line 74 now and will see if that works like I hope it works.
Thanks again.

---

### Post by dodle on 2010-07-31
It looks like they are working on a fixed release here:  [https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/376966](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/376966)
> Okay I have linked a branch which fixes the problem. Not only does it remember your selection, it also uses Synaptic's config so that the checkbox is consistent between both apps.

---

### Post by DeMus on 2010-07-31
> **dodle said:**
> It looks like they are working on a fixed release here:  [https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/376966](https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/376966)

Finally. I was wondering if I was the only one who was having this feature, but now it seems it is a bug and it gets fixed.
Perfect.

---

### Post by mc4man on 2010-07-31
I'll let you know - am on maverick where the fix will be released.

Edit: so it looks like by default gdebi will stay open - and the ck. box will control the 'progress box' and 'details'(terminal).

---

### Post by filbo on 2010-10-11
> **mc4man said:**
> Not a clue. the default should be to close gdebi after using. the checkbox should be used to keep it, that single instance,  open.

(As seen there is no real use to keeping it open anyway, all you can do is re-install the .deb you just installed.

In a round about way that's what this edit does, what possessed them to set the default to keep gdebi open is beyond me.

Strong disagree.  Here's what I just posted into [LP #604610]("https://bugs.launchpad.net/ubuntu/+source/gdebi/+bug/604610"):

[QUOTE=me in LP #604610]

Doug McMahon wrote:

> The true bug is that the default for gdebi should be to autoclose and the the option should be to keep the current instance open. (noting that there is almost nothing to be done with the current instance after install other than re-install the .deb that was just installed.

I watch the terminal to make sure all goes well; I often catch problems that way. Defaulting to "close" would make it difficult to do this consistently. For short installs I might not even be able to click quickly enough to win the race.

Please *don't* "fix" this by permanently defaulting to "close". Then instead of a minor inconvenience for many, it becomes a usability disaster for the few. I realize terminal output is logged somewhere so it isn't quite catastrophic, but if the terminal is unreliable because it disappears, you might as well just remove it completely. Which is not what I want.

Most users do not apply this level of vigilence and truly *would* like the installer window to go away ASAP. Different users have different desires, or the checkbox wouldn't need to exist in the first place!

So please fix it to remember the user's desired setting.[/QUOTE]

---

### Post by filbo on 2010-10-11
It's been fixed in Maverick by equating the gdebi-gtk setting to a similar setting in Synaptic.  I *think* this will address my concern since I'll want the same behavior from Synaptic; but I haven't played with it enough yet to be sure.

---

### Post by mc4man on 2010-10-11
> . I think this will address my concern since I'll want the same behavior from Synaptic; but I haven't played with it enough yet to be sure.
It should and also suit those who preferred it to close without having to always ck. the box. (myself always have synaptic show in a terminal

The default now is to autoclose, as it is in synaptic. You can change that in synaptic or otherwise choose to keep any single instance of gdebi-gtk open by unchecking the box.
(this is what it should have always been, close the progress box by default, choose to keep open if desired

In any event the default for local or online .debs has been changed to software center though it can be set back
By the time software center even opens, gdebi has already finished..

---

### Post by filbo on 2010-10-11
> **mc4man said:**
> The default now is to autoclose, as it is in synaptic. You can change that in synaptic or otherwise choose to keep any single instance of gdebi-gtk open by unchecking the box.
(this is what it should have always been, close the progress box by default, choose to keep open if desired

That default is only valid, "what it should always have been", if the program remembers your previous choice.  Always defaulting to close means you get in races where you *can't* prevent it from closing before a small install finishes.

I feel similarly about the "show me download details" in these various installers.  I want the detailed download progress displayed, always, and I always want to approve moving on to the next step after a download.  Why?  Because sometimes downloads go wrong in a manner that is apparent to me as the viewer, but not to the software.  It proceeds and goes wrong without having given me an opportunity to stop it.

I most especially feel that way about full release upgrades (10.04 -> 10.10).  I resent that I have to tell it "go ahead and upgrade" before downloads have been done.  Downloads take hours, I can't monitor the whole thing, and I want to make sure everything is good before the upgrade itself starts up.

I believe (didn't take notes) that during this particular upgrade there *was* a waystation between download & install.  It asked me about a bunch of packages it was going to uninstall (no longer needed or obsolete), I **think** before actually doing the install.  But I would have experienced much less anxiety if I'd known in advance that it was going to pause there.

---

