---
title: "tweaks after 10.04 install with custom home partition"
date: 2010-05-11
forum: General Help
---

### Post by pearldrums on 2010-05-11
Hello, I have a few quick questions.

I just did a fresh install of 10.04, I have previously had karmic installed. For the first time ever I made a separate partition for "home" so that I could do a fresh install without needing to worry about my personal files such as music and pictures. I experienced a few surprises.

For starters, more settings were preserved that I thought would be. My gnome panel is exactly like I had it set in karmic. I would like to return to the default for Lucid and re-build from there. Can anyone help me with that? It seemed peculiar that this setting was preserved, so on a hunch I went to my rhythm box and was disappointed to see that I need to add all my music to it's library again, but I expected that.

Also, it would have carried over the default theme of "human" if it were installed I think, but it wasn't so it went to one of the simple themes. Which theme is standard for lucid? Is there a way to install the Human theme? 

Given that I'm a newbie to the whole separate home partition thing, are there any other things I might not have noticed that you can give me a heads up for?

Thanks a lot guys.

---

### Post by gvernold on 2010-05-11
Human Theme is in the repositories and can be installed using Synaptic Package Manager. Or type:

sudo apt-get install human-theme

at the command line.

As for the Gnome Panel take a look here:

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

And finally, some new versions of mail clients (notably Thunderbird) have a different folder hidden in your home directory in Lucid. This means that your mails and settings might not be there when you expect them to be. Fortunately it's not too hard to move your old mails over but I got caught out on this one when I installed Lucid.

As for other differences with the home partition I'm not sure but it certainly gives you the shakes when all your mail disappears.

---

### Post by pearldrums on 2010-05-11
sweet, thanks for the help. I use web based e-mail (for now) so I won't have any issues with that.

---

