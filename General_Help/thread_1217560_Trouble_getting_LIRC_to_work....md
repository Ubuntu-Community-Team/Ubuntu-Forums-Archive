---
title: "Trouble getting LIRC to work..."
date: 2009-07-19
forum: General Help
---

### Post by dt1000 on 2009-07-19
Hello.
I've decided to try and set up an HTPC using UBUNTU.
This is the first time I've used the OS and so far my experience has been... frustrating. :)

Anyway, I've got video and audio *kinda* working, and I thought I would turn my hand to the IR Remote.

Now this actually worked AOK right out of the box! :)
This would have been awesome if the remote that came with my case wasn't so rubbish...
Having read up a bit on LIRC I thought I would set it up and have a fiddle to get my case's built-in USB IR detector working with a (lovely) Soundgraph iMon controller.

LIRC installed OK.
The Gnome Lirc Properties installed and is working OK.
My problem is this...

When I start LIRC Properties (System -> Administration ->  Infrared Remote Control) none of my settings are saved. I see this...

[IMG]http://img504.imageshack.us/img504/7499/screenshotremotecontrol.png[/IMG]


The configuration test works perfectly - all my button presses are detected.
So then I click on "Auto Detect" and the IR module in my Moncaso 312 case is instantly spotted - no problemo...

[IMG]http://img166.imageshack.us/img166/7499/screenshotremotecontrol.png[/IMG]

Then when I try and switch the remote control to my Soundgraph iMon (which is already on the list of supported remotes :)) and click "Close" nothing happens. That is to say that the iMon doesn't show up on the configuration test and the default controller still works. On reopening the config window, none of the changes have been saved.

Do I need to click on "Update"?
When I do everything progesses nicely until right at the end when I get this message...

[IMG]http://img529.imageshack.us/img529/3175/13866332.png[/IMG]

I get a similar message when I try and save  a custom config for the default remote...

[IMG]http://img36.imageshack.us/img36/9409/19992510.png[/IMG]

What am I doing wrong?
Do I need to install something extra?

Is it actually possible to get an alternate remote to work with the supplied receiver using LIRC?

Any help would be much appreciated!
Thanks,
Dan

---

### Post by michy99 on 2009-07-19
You may need to run the program as root so that it has the proper permission to save the settings. Start it from a terminal and precede the command with 'gksudo'```
gksudo somecommand
```

---

### Post by dt1000 on 2009-07-19
Thanks for the tip - I tired it out stiraght away.
Still no joy - exactly the same problems...

Any other ideas as to what might be wrong?

:)

---

### Post by dt1000 on 2009-07-27
Anyone? :(

---

