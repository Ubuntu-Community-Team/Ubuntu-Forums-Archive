---
title: "Problems with packages in Kubuntu"
date: 2009-11-06
forum: General Help
---

### Post by Ouguiya on 2009-11-06
Hello everyone!

First of all a big thanks to all who read this and were involved in making (k)ubuntu what it is. It really is great, especially in version 9.10.

Now, as with every fresh install, there are a few problems here and there who need to be sorted out.

One of which I have no idea what I am doing wrong. The situation is as follows: Back in the day when KDE 4.0 and 4.1 were not that great, I stuck to ubuntu for the time being. Since I am a natural science student, the Debian Science packages came in really handy. In ubuntu, this would install me a huge load of software designed only for science.

Now that I am back to kubuntu, something strange is going on: Selecting the Debian science packages, (Like "Science-Chemistry" and so on), shows me that they don't depend on anything. Installing them also installs nothing at all. So, I am left wondering: Where are the science packages?

It's a bit strange in and of itself, since using ubuntu x64, (I tried it), downloading all that science stuff works beautifully. In kubuntu x64, this doesn't work.


If anyone could tell me what I am doing wrong or what I need to change to have access to those "meta"-packages, I'd be very grateful.

Yours,

Ouguiya

---

### Post by kellemes on 2009-11-06
I assume you're using the standard *buntu repositories and not some Debian-repository?
Because I see [science-chemistry is available]("http://packages.ubuntu.com/karmic/science-chemistry") for Karmic and should be installable without issues.
Have you tries this from terminal?
```
sudo apt-get install science-chemistry
```

---

### Post by Ouguiya on 2009-11-06
Hello there! Thanks for the reply.

Well, I didn't change anything in the sources section, so I am assuming that after a fresh install, I am using the standard repositories.

As I mentioned, the strange thing is that in ubuntu, using synpatic package manager, it installs without problem. however, on the same machine, using Kubuntu and Kpackagkit, the installation fails, and the package manager installs nothing at all.

I have to admit that I haven't tried the console command for it, but installing everything from console is a bit problematic, especially since I installed many packages, and now do not know what was correctly installed and what wasn't...

Thanks for the advice in any case.

Yours,

Ouguiya

---

### Post by Ouguiya on 2009-11-07
-Bump-

Anyone out there who has more thoughts on this? Please...?

Yours,

Ouguiya

---

