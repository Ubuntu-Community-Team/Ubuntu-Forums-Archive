---
title: "Command Line Switches for Startup Applications"
date: 2010-03-26
forum: General Help
---

### Post by stevepaul on 2010-03-26
I've just installed 9.10 (AMD) and have added Chrome to my Startup Applications ...

In my Windows install I have a couple of Command Line Switches ...

I'm sure when I was messing with 9.04 last November there was something somewhere that allowed you to customise the Startup Application ...

I can't find this option anywhere, does it still exist as a GUI or do I have to do something else now...

---

### Post by prodigy_ on 2010-03-26
When you want to find out what switches are available: ```
<command_that_starts_an_application> --help
``` usually does the trick.

---

### Post by gordintoronto on 2010-03-26
Preferences/Startup Applications.

---

### Post by stevepaul on 2010-03-26
@gord

Thanks, I know where that is, but there is nothing to allow you to add command line switches ...

If I remember right, originally you could also indicate whether the  application was to be maximised or not ...

Where has this options dialogue box gone ...

---

### Post by prodigy_ on 2010-03-26
Ok, an example:

You want to open a terminal window every time you log in. Also you want it to load a specific profile, specified in a CL switch "--window-with-profile.

Then you go to System/Preferences/Startup Applications and add a new item:

Name: <anything_you_want>
Command: gnome-terminal --window-with-profile=foo
Comment: <anything_you_want>

You can use the same method for any other application. Is that what you're looking for?

---

### Post by stevepaul on 2010-03-26
@prodigy

Yes it is (sort of) but there used to be a dialogue box that 'popped' up, just can't remember where it was or how you get to it ...

It made life so much easier ...

---

