---
title: "Gnome-Bittorrent (Continuing a Download)"
date: 2006-04-05
forum: General Help
---

### Post by nw15062 on 2006-04-05
[COLOR="DarkRed"][SIZE="3"][FONT="Arial Black"][CENTER]Continuing a download in **gnome-btdownload** When it refuses to?[/CENTER][/FONT][/SIZE][/COLOR]
[CENTER]
I was downloading a Rather Large File approximatly 4.5Gigs, I stopped Gnome-Bittorrent Downloader and closed the window when I started it up again, it  failed to recognize the existing downloaded file's and decided to start over again.

I understand that Gnome-Bittorrent keeps a cache file for download locations in the directory "**/home/$username/.gnome2/gnome-btdownload/cache**"

I tried to kickstart it by starting a new download instance, stopping it, then editing the perticular cache file to the previous location. I didnt expect this to work and sure enough it didnt.

I am posting this because I am  trying to find out if there is anyway I can force it to continue downloading the previous location, it is fustrating considering I had only 300megs out of 4.5 gigs.[/CENTER]

---

### Post by nw15062 on 2006-04-05
It Appears no one has a quick solution for this?

---

### Post by MetalMusicAddict on 2006-04-05
Use synaptic to get Bittornado and Bittornado-gui. Try to resume with that.

---

### Post by dudus on 2006-05-12
This seems to be a bug in gnome-btdownload. And I think it is about how it names the destination file.
To reproduce this bug try this:

1: get a torrent that has a space in the name.
2: try downloading this and you'll notice that it changes the space for a %20.
3: close and try to continue.
4: gnome-btdownload won't find the file as it looks for the space where it is a %20.

Thankfully I could manage to get over this bug. When you first start the download don't click in the torrent directly. Instead open gnome-btdownload using the terminal and then it asks for the path of the torrent file.
Than find the torrent file and it will start downloading this.
Now if you close and start again it will do it right.

Try renaming the names of both the torrentfile and the destination file to something simple, to keep your existing files and make it resume.

hope it helped

---

### Post by dudus on 2006-05-12
This seems to be a bug in gnome-btdownload. And I think it is about how it names the destination file.
To reproduce this bug try this:

1: get a torrent that has a space in the name.
2: try downloading this and you'll notice that it changes the space for a %20.
3: close and try to continue.
4: gnome-btdownload won't find the file as it looks for the space where it is a %20.

Thankfully I could manage to get over this bug. When you first start the download don't click in the torrent directly. Instead open gnome-btdownload using the terminal and then it asks for the path of the torrent file.
Than find the torrent file and it will start downloading this.
Now if you close and start again it will do it right.

Try renaming the names of both the torrentfile and the destination file to something simple, to keep your existing files and make it resume.

hope it helped

---

### Post by s_spiff on 2006-05-13
ok I'm as such a noob to this... but i had this problem too... i dunno  a work around.. but then..what u can do it.. download azereus... u shudnt have trouble with that.

---

### Post by Resurrection on 2006-05-13
Yeah I don't know a solution either, because I have only ever used Bittornado or Azureus.

I recommend trying Bittornado as suggested before.  You should be able to just restart the torrent from the same .torrent file you used before and it should auto resume.  Never had an issue with Bittornado not doing so.  Remember that it has to be the EXACT .torrent file you used before, not a different torrent for the same files.  Also, you may have to point Bittornado to the directory where you had previously downloaded part of your data to.

Bittornado is very lightweight, and stable.  Never had an issue with it crashing or messing up my torrents.  Not even on Windows.  Seriously never had a problem with it in 3 years of use.

Azureus, I am not as big a fan of.  Azureus has a much "happier, shinier" GUI than Bittornado and a ton more options, but it is also a resource hog in comparison.  I don't consider it as stable either.  But it is still a great program, it just loses to Bittornado in my opinion.

---

