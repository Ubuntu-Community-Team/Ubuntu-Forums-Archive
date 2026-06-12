---
title: "Creating .package Files"
date: 2011-03-21
forum: General Help
---

### Post by Daniel5 on 2011-03-21
Hello fellow Ubuntian!

I've been scooting around Google to try and figure out how to create .package files. Apparently their created by a utility (which is already installed on my PC) called 'autopackage'. I've been to their website ([www.autopackage.org]("http://www.autopackage.org")) but I can't find anything on how to actually create the .package files.

Can anyone shed some light unto this?

---

### Post by WorMzy on 2011-03-21
This any use to you?

[http://autopackage.org/docs/devguide/ch02s02.html](http://autopackage.org/docs/devguide/ch02s02.html)

---

### Post by Daniel5 on 2011-03-21
> **WorMzy said:**
> This any use to you?

[http://autopackage.org/docs/devguide/ch02s02.html](http://autopackage.org/docs/devguide/ch02s02.html)

Ah thanks! I guess I didn't search the site thoroughly enough. Lastly it says I need to use 'makepackage' to actually create the file. But again my inferior searching skills have yielded nothing. Can ye aid thou in his pursuit of his quest?

---

### Post by WorMzy on 2011-03-21
[http://autopackage.org/docs/devguide/ch02s04.html](http://autopackage.org/docs/devguide/ch02s04.html)

?


I've never used the application in question (although it bears a striking resemblance to AUR packages on Arch Linux), so I'll just link you to the documentation's index: [http://autopackage.org/docs/devguide/index.html](http://autopackage.org/docs/devguide/index.html)

Hopefully reading through that will answer most of your questions. :)

---

### Post by Daniel5 on 2011-03-21
> **WorMzy said:**
> [http://autopackage.org/docs/devguide/ch02s04.html](http://autopackage.org/docs/devguide/ch02s04.html)

?


I've never used the application in question (although it bears a striking resemblance to AUR packages on Arch Linux), so I'll just link you to the documentation's index: [http://autopackage.org/docs/devguide/index.html](http://autopackage.org/docs/devguide/index.html)

Hopefully reading through that will answer most of your questions. :)

The problem is I can't actually find the 'makepackage' utility. The 'autopackage' was already installed (perhaps by default). It's not in the repos and I can't find it via Google. So I'd get 'command not found' if I typed 'makepackage' into Terminal. Could thou aid me in finding it?

** I've found _[this](http://stuff.mit.edu/afs/sipb/project/wine/dosdevices/z:/mit/linux/devel/makepackage/)_ I've made the bin executable and executed it from Terminal but can't seem to figure it out now.

---

### Post by WorMzy on 2011-03-21
The main website says that the project has merged with Listaller, but as far as I can tell, that project only has one executable, called lipa.

My [repo hunting]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=contents&keywords=makepackage") hasn't yielded anything either, so basically, I don't think I can help you.

If you want to try installing Listaller, there's instructions here: [http://listaller.nlinux.org/oldpage/getlistaller.html](http://listaller.nlinux.org/oldpage/getlistaller.html)

Maybe the lipa command works in a similar way to makepackage?

---

