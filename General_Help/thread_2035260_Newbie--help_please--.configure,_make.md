---
title: "Newbie--help please--.\configure, make????"
date: 2012-07-30
forum: General Help
---

### Post by Redneckokie on 2012-07-30
I am newbie to Ubuntu. 
I download a music player.  In the install is says type .\configue, then make and then make install.
Where do I type this??  I'm kinda confused here, I'm used to just clicking and it installs!!
Any help would be great!
Thanks!

---

### Post by miegiel on 2012-07-30
> **Redneckokie said:**
> I am newbie to Ubuntu. 
I download a music player.  In the install is says type .\configue, then make and then make install.
Where do I type this??  I'm kinda confused here, I'm used to just clicking and it installs!!
Any help would be great!
Thanks!

In short: DON'T DO IT!

Get one of the music players from the ubuntu software center (aka repository). There are plenty to choose from and chances are the one you downloaded is in there too, packaged and ready to install.

In the linux world we use centralized repositories with software, it's tested and alot more secure then downloading stuff from "somewhere". And almost everything you need is in there. No need to get your software "the windows way".

btw. Welcome to ubuntu forums :D

ps. my personal favorite is gmusicbrowser

---

### Post by Kundan Negi on 2012-08-02
Hey according to my knowledge there is no command .\configure. It would be ./configure/. You should make install command as a root.

---

### Post by Dylan1473 on 2012-08-02
In case you just read that I'm going to add to what miegiel said and recommend you not do this. Even assuming you've found a safe source (and I'll give you the benefit of the doubt and assume you have, though it still probably wouldn't be as secure as using the repositores) what you're trying to do is compile from source and that's not a wise choice for newcomers. You might have to manually install numerous dependencies which might not be entirely clear, it could be difficult to uninstall afterwards if something goes wrong (and things can very easily go wrong, especially if you're new) and the whole process is just a lot more complicated and slower than using the software center or otherwise using the repositories.

What I recommend is either using the Ubuntu Software Center which includes a friendly graphical user interface and I assume several music player packages, or installing it through the terminal using sudo apt-get install [package name]. You might be able to find it with sudo apt-cache search [name of program]. The Ubuntu Software Center is probably the easiest way, though the second would probably be a bit faster. Alternatively, you could search for a .deb package for the same program online rather than a source package, that'll be much easier and safer to install (though not as safe as using the above two methods). It might also be possible to make your own .deb package but this is also not really for newcomers.

If you absolutely insist on compiling from source what you'll actually need to do is:

[LIST=1]
[*]Open a terminal then type ./configure
[*]If there are no error messages at the end type make
[*]If there are no error messages at the end type sudo make install
[/LIST]
That will probably get the package working assuming it compiles without errors*.


*It probably won't.

---

### Post by audiomick on 2012-08-02
Tell us which player it is. If your not sure yourself, I reckon someone would be willing to have a quick look  and see if it is available via the software centre.

I would also advise not trying to compile something yourself. Don't try and do it all at once. Use the system for a while and get used to it. Unless, of course, you are past all that and are wanting to try compiling something from source just for the sake of it... ;)

---

