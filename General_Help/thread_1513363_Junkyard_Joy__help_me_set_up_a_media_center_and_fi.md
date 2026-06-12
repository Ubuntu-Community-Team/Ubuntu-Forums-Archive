---
title: "Junkyard Joy:  help me set up a media center and file server!"
date: 2010-06-19
forum: General Help
---

### Post by hoboken on 2010-06-19
Hey all. I recently picked up a surprisingly good computer off the streets. specs: 3ghz P4, 1gb ram, 200gb HD, 6xusb2.0, 2xfirewire, svideo and composite video out, two(!) DVD drives, digital audio i/o, 5.1 out, RCA out.

I'd like to do the following with it:
[LIST]
[*] fileserver, for streaming music. needs to be mountable as a drive in order to be read by foobar (clients will be running windows)
[*] media center for watching movies. will be hooked up directly to a TV. (XMBC?)
[*] torrent box. will be on 24/7, and torrents will be managed remotely. I don't want to touch the computer except to watch films.
[/LIST]

OS will be Ubuntu server unless you have a better suggestion. I'm also wondering how to set up the file server (especially important is that it be mountable as a drive in windows 7) and how to set up remote torrenting (also managed from a win7 box).

Thanks!

---

### Post by Joe of loath on 2010-06-19
Firstly, nice find! I wish I knew where to look for this kind of thing, I check skips (dumpsters) when I walk past, but never find a thing.

Since you want to use it as a media center, it's probably best to start with ubuntu desktop. Anyway.

Fileserver - Does it have to serve windows boxes, or just *nix? I setup an NFS box on my network and I'm VERY pleased with the speeds, almost 4x faster than samba. Also incredibly easy to set up. EDIT: Just saw you wanted to use it with windows, you'll have to use samba I'm afraid. There's lots more info out there on samba though.

Media center - I'm afraid someone else will have to recommend something here, I haven't got a clue.

Torrents - Transmission has a web interface, I'd suggest you use that.

---

### Post by hoboken on 2010-06-19
hey Joe, thanks for the reply. I found the computer at the doorstep of my apartment block with a sticker boasting "it works!". Another guy was already eyeballing when I got there so I just whizzed past, grabbed the computer and went inside. Huzzah!

Are you sure there's no way of mounting NFS on windows? I've been lead to believe there is. 

I have the media center side of things covered. XMBC. I guess I'll need a GUI though, shall I go for gnome or XFCE? This box can probably handle gnome fine...

Thanks for the transmission tipoff, I'll look into it.

---

### Post by Joe of loath on 2010-06-19
Wow, lucky. Nice of the original owner to sticker it XD (Love the avatar BTW!)

Now you mention it, I think there is. It might even be native in win7, I shall have to check.

Gnome. Xubuntu uses the same amount of memory at idle as Ubuntu, and Gnome has more features.

Oh, it's way prettier too.

---

### Post by Smart Viking on 2010-06-19
> **Joe of loath said:**
>  
Oh, it's way prettier too.

No way man, xfce4 is much prettier than gnome. :)

---

### Post by hoboken on 2010-06-19
Agreed, <3 gnome. What theme are you using? My favourites are by a guy on gnome-look called Lyrae, everything he designs is stunning. Give it a look. 

I found this article which is incredibly helpful.
[http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)

So, I'm set! I'll update this thread if I run into any trouble. Thanks Joe.

---

### Post by Joe of loath on 2010-06-19
My theme's called 'aquadreams'. I installed it from a theme pack, can't remember where I got the pack from.

No problem, just someone who's been learning trying to pass that knowledge along!

---

