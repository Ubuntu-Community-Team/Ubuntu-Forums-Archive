---
title: "Migrating T-Bird in 10-04 - Help Pls!?!"
date: 2011-04-19
forum: General Help
---

### Post by DunZH on 2011-04-19
Hi All:

I am a nearly-intermediate user and I have had trouble before migrating T-Bird so I am being careful this time. But, I know most of the basic problems to watch out for.  I need to migrate from one 10.04 install to another. And, I have a current account on the second computer, that I am willing to trash if necessary.

Basically I have one question, other than could anyone send me to the definitive how-to to migrate thunderbird:

In the home directory, there are now two folders for T-Bird, and they both seem to have the same contents, but when I tried one time, I only moved one and my data was gone.

So what's up with that?  Can I just move both the folder contents into the existing profile folders and start it up?

Any help is appreciated.  I wish there was a clear guide on the mozilla website.

):P

---

### Post by indytim on 2011-04-19
It's been several months since I did it (Mint 8 Gnome -> Mint 10 Gnome).  Basically, **only for Thunderbird,** :

1.  Make a copy of your .thunderbird directory to a new name (this is the just-in-case option...):)

2.  Delete the destination .thunderbird directory.

3.  Copy the .thunderbird folder from your originating /home to your new home.

4.  Fire up Thunderbird and verify that all is happy again.  If so, delete the copy that you made.

Note of importance,  based on my recent experiences, this should work with Thunderbird.  It will NOT work with Firefox.  Mozilla has managed to totally thwart any attempts to do a reasonable move of Firefox and all of it's settings, passwords etc.  

Hope this helps,

-IndyTim / DataMan

---

### Post by DunZH on 2011-04-20
Thanks IndyTim, but I think that it won't work for 10.04 because there are two folders in the home directory.

However, as it turns out I no longer need to do this.  Heh. Sorry.

---

