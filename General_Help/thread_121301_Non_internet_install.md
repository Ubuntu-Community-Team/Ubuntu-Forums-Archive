---
title: "Non internet install"
date: 2006-01-24
forum: General Help
---

### Post by naitsabes on 2006-01-24
Hi, my Ubuntu box currently has no internet connection.  Is there a way that I can DL the files to my windows box and then install them onto the ubuntu box from a Flash Drive?  I guess what I'm asking is will it contaminate the files if it goes through Windows first, and is it okay if I zip the files into a package, because I really don't feel like lugging it up thirty stairs from the basement. ;)

---

### Post by stream303 on 2006-01-25
If it's only for occasional updates, I'd just buy a 75-foot run of cat-5 ethernet and toss it downstairs once in awhile... :)

Or maybe look into going wireless..

---

### Post by RAOF on 2006-01-25
Actually, there's apt-zip, I think.  Let me check...

Yeah, it looks like apt-zip is **exactly** what you want.  And it's in Universe. [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=apt-zip](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=apt-zip)

---

### Post by naitsabes on 2006-01-25
Thanks, but that's just the source.  What I meant was applications, like being able to download an apt-zip for wine etc. While I'm at it.  Is there any way to make the default size of the windows smaller, or just make the actual resolutino smaller than 680 by... (I forget what the other dimension was,)  on a very small monitor?

EDIT: Ah, I see that that was what I was looking for, however how about my second question?

EDIt 2: Hm, it seems to be a DEB file, which I have no idea what it is, care to explain anybody?

---

### Post by RAOF on 2006-01-25
[QUOTE=naitsabes]Thanks, but that's just the source.  What I meant was applications, like being able to download an apt-zip for wine etc. While I'm at it.  Is there any way to make the default size of the windows smaller, or just make the actual resolutino smaller than 680 by... (I forget what the other dimension was,)  on a very small monitor?

EDIT: Ah, I see that that was what I was looking for, however how about my second question?

EDIt 2: Hm, it seems to be a DEB file, which I have no idea what it is, care to explain anybody?[/QUOTE]
Well, if you have internet access you can just run "sudo apt-get install apt-zip", & that will download, install and set it up.

As you don't have an internet connection, you can download the deb, and then install it with "sudo dpkg --install <nameofthedeb>.deb"

And as for the second question, I don't think you can run a resolution smaller than 640x480

---

### Post by naitsabes on 2006-01-25
Hm, thanks.  The problem I had with the resolutiuon is that every time a new window is created, it appears to be bigger than the screen, and I really don't want to have to buy a new monitor.

---

