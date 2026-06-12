---
title: "Virgin Media Player on Linux stopped playing"
date: 2011-12-02
forum: General Help
---

### Post by claire14 on 2011-12-02
hi does anyone know why the virgin media player has recently stopped playing on Ubuntu 10.10

all i get from virgin is they do not support linux 
but it played on my laptop for over 9 months
i know i could dual boot but some reason partition's wont mount i'll make a thread for that later :)
thankyou if anyone can help  :)

---

### Post by nothingspecial on 2011-12-02
I don't have virgin broadband so I can't have a look, but are you sure this isn't just a flash issue?

Do iplayer and youtube etc work?

---

### Post by claire14 on 2011-12-02
yeah everything else plays and i reset flash-aid

---

### Post by nothingspecial on 2011-12-02
Do you know what virgin media use?

When they say they don't support linux that doesn't necessarily mean that it won't work, it's just that they don't pay people to know how to fix it.

---

### Post by claire14 on 2011-12-02
i'll ask them and post any answer i get on here :)
virgin media player was fine for the 9 months i could get on it , 
even channel 5 player is ok on ubuntu

---

### Post by claire14 on 2011-12-07
> **nothingspecial said:**
> Do you know what virgin media use?

When they say they don't support linux that doesn't necessarily mean that it won't work, it's just that they don't pay people to know how to fix it.

hi its Flash 10.1 they said for the virgin media player

---

### Post by nothingspecial on 2011-12-08
Have you tried the flashaid firefox plugin?

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by claire14 on 2011-12-08
> **nothingspecial said:**
> Have you tried the flashaid firefox plugin?

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

hi i have flashaid installed , could it be a firefox update thats stopped it and if it is how do i go to a lower version of firefox
i have firefox 7.01 files and firefox 3.6.15 and maybe some other lower versions

also how do i post screenshots on here so i can make a post asking for help on partitions as it wont mount/unmount partitions , i might have to dual boot to get virgin media player back , i don't want to do that i like Linux :)

Fixed it  :) 

thank you everyone for your help  :)

---

### Post by Another Monkey on 2012-04-03
Could you (or anyone) please explain how to fix/workaround this?

I'm on Ubuntu 10.10 64bit
Firefox 11
Flash 11.2

To get around the OS detection I tried using "User Agent Switcher", and whilst that did work the Virgin site can't "initialise [my] device" (whatever that means).

I have tried rolling back to Flash 10.1, that didn't help.

I also installed "Flash-Aid", but can't see how that's of any benefit.

Looking at the site from an other OS, it's just a basic Flash player, nothing crazy to why they insist on block a GNU/Linux OS beats the heck out of me.

---

### Post by Another Monkey on 2012-04-05
In case anyone else is looking for help on this - don't.  Virgin Media has dropped all Linux support (Ubuntu, Android, everything).

See [this Virgin Media forum posting]("http://community.virginmedia.com/t5/General-broadband-questions/VM-Player-in-Linux/m-p/1129449#M30774") for details.

And all this from an Ubuntu mirror!

---

### Post by Another Monkey on 2012-04-06
And here is the complete solution:

Much thanks go to ApollosAntiGrav for this.

How to get VMPLayer working under Linux

[LIST=1]
[*] Install [PlayOnLinux]("http://www.playonlinux.com")
[*] Execute "playonlinux" from the command line (no quotes).
[*] Install Firefox.
[*] Install Flash.
[*] Run Firefox.
[*] Goto the url "about:config" (no quotes)
[*] Search for "dom.ip" (no quotes) and check that both the boolean values are "false"
[*] If you have to change a value, restart the browser
[*] Goto "www.youtube.com" (no quotes) to check that flash does work
[*] Goto "www.virginmedia.com/player" and sign-in
[*] Enjoy (see note) and this includes Sky Anytime (once device is registered)!
[/LIST]

Note: PlayOnLinux installs Win 1.3 in the background.  If you see video corruption (black/flashing blocks) install a more recent version of Wine (at the time of writing, 1.4 is the latest stable, available via [Wine Team ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa") or your distro's equivalent).  Then open PlayOnLinux and configure the Firefox item to use the "System" version.  Now when you run Firefox the video corruption should be gone.

Test System: Ubuntu 10.10, Core 2 Duo, 4Gib, nVidia GT240 1Gib

I did not manage to get it working on Wine 1.4 directly, I am not sure what PlayOnLinux does - but it works!

---

### Post by claire14 on 2012-04-07
thats how i got it to play video's , DRM sucks , 
a resource based economy will end DRM

---

