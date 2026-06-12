---
title: "resuming gnome bittorentdownloads"
date: 2006-06-14
forum: General Help
---

### Post by kroiz on 2006-06-14
I use gnome-btdownload as my bittorrent client.
I wish to know how to resume a connection after I close the gnome-btdownload window.
the way I usualy do it is I re-download and then the gnome-btdownload recognize there is already leftovers of previouse download and let me resume it.

---

### Post by joshrobinson on 2006-06-14
[QUOTE=kroiz]I use gnome-btdownload as my bittorrent client.
I wish to know how to resume a connection after I close the gnome-btdownload window.
the way I usualy do it is I re-download and then the gnome-btdownload recognize there is already leftovers of previouse download and let me resume it.[/QUOTE]


i would just use azureus... its alot better of a client.. its in the repo's if you enable the extra repo's

---

### Post by ato on 2006-06-14
Try "freeloader"
It's in the Universe repository

---

### Post by kroiz on 2006-06-14
why have 2 programs that do the same thing for me. I am sure it is possible with gnome-btdownload.

---

### Post by Ramses de Norre on 2006-06-14
What's wrong with the way you usually do? I just save my torrent files and reopen them, gnome-btdownload then asks me whether to continue or start again all over.

---

### Post by scxtt on 2006-06-14
yeah, you're not having any problems at all ... it's just "sync'ing" up w/ what you've already downloaded -- seeing where you left off so as not to overwrite or waste time getting data you already have ... i think gnome-btdownload is great - SO much easier than azureus ... nothing better than being able to download ~700mb isos (of FREE Linux distros) @ 500k/s ... :)

---

### Post by kroiz on 2006-06-15
when I open gnome-btdownload it ask for some meta file, what and where is that meta file?

the way i usualy do it is i need to find the link again which I first use from the internet. so I need to open firefox and go to the site with the link.

I wish I could just select the file I started to download as a meta file.

---

### Post by scxtt on 2006-06-15
all you need to do is KEEP the original torrent file (even if you close the download before it completes) and then click it again when you want to resume - and you can probably open gnome-btdownload then navigate to it w/ the same results ...

---

### Post by kroiz on 2006-06-15
[quote=scxtt]all you need to do is KEEP the original torrent file (even if you close the download before it completes) and then click it again when you want to resume - and you can probably open gnome-btdownload then navigate to it w/ the same results ...[/quote] 
oh I see, when I click the link, instead of using "open with" I will do "save".
not as elegant as I wished. but I guess that will do.
thanks scxtt, Ramses de Norre, joshrobinson and ato.

---

### Post by scxtt on 2006-06-15
[QUOTE=kroiz]oh I see, when I click the link, instead of using "open with" I will do "save".
not as elegant as I wished. but I guess that will do.[/QUOTE]i've never known of ANY bit-torrent program that doesn't require the .torrent to be on your machine (even if the program copies it to a /tmp dir. if you chose "open with") ...

---

### Post by kroiz on 2006-06-15
[quote=scxtt]i've never known of ANY bit-torrent program that doesn't require the .torrent to be on your machine (even if the program copies it to a /tmp dir. if you chose "open with") ...[/quote]

Well I have never seen a bit-torrent program that does not hold a list of downloads. 
I think that this is the reason that gnome-btdownload does not save the .torrent.

But I now think that it would be a nice feature of gnome-btdownload that upon closing the window, of an unfinished download, it will ask "Would you like to save the torrent meta file inorder to resume the download later?"

what do you think?
is it worth posting some were for a feature request?

---

### Post by scxtt on 2006-06-15
honestly, i think it's easier to do a "save file as" than request a "feature" like that ... not having it auto save torrents makes it so i don't have to "worry" about deleting them after i'm done ... to each his own, i guess ...

---

### Post by kroiz on 2006-06-15
[quote=scxtt]honestly, i think it's easier to do a "save file as" than request a "feature" like that ... not having it auto save torrents makes it so i don't have to "worry" about deleting them after i'm done ... to each his own, i guess ...[/quote]

I think gnome-btdownload could delete the .torrent when the file completed.

---

### Post by scxtt on 2006-06-15
[QUOTE=kroiz]I think gnome-btdownload could delete the .torrent when the file completed.[/QUOTE]riiiiiiiiiiiiight, hence my "to each his own comment" ...

:p

---

### Post by kroiz on 2006-06-15
[quote=scxtt]riiiiiiiiiiiiight, hence my "to each his own comment" ...

:p[/quote] 
I dont see where we dont agree. (sorry for double negative)
I too would not like to have to delete the file myself.
I think it must be done automaticly.

---

### Post by Nivekk on 2006-06-15
[QUOTE=scxtt]yeah, you're not having any problems at all ... it's just "sync'ing" up w/ what you've already downloaded -- seeing where you left off so as not to overwrite or waste time getting data you already have ... i think gnome-btdownload is great - SO much easier than azureus ... nothing better than being able to download ~700mb isos (of FREE Linux distros) @ 500k/s ... :)[/QUOTE]

I had completed 50% of a 6GB download using Bittorrent, and I was forced to restart my computer.  Upon restarting and restarting Bittorrent, I selected the same *.torrent file (in the same location as it had been) and then chose to contiune from the previous session when it prompted me, but it seems to be starting to download it ALL over again (0 of 6422 MB).... 

But I notice that even though I said to continue in the same saved location, it created a new directory (and thus started downloading from scratch).  Now, I would close Bittorrent and restart it, this time saying "no" to the -save-from-same-location prompt, and i manually chose to save it in the same directory, and I get an error "directory already exists" as if I cannot continue downloading it into that directory.

excuse my ignorance if the answer to my concern was in this thread; I looked but I really don't think it is really starting where it left off when it says 0 of 6422MB.

---

### Post by kroiz on 2006-06-16
[quote=Nivekk]
But I notice that even though I said to continue in the same saved location, it created a new directory (and thus started downloading from scratch).  Now, I would close Bittorrent and restart it, this time saying "no" to the -save-from-same-location prompt, and i manually chose to save it in the same directory, and I get an error "directory already exists" as if I cannot continue downloading it into that directory.

excuse my ignorance if the answer to my concern was in this thread; I looked but I really don't think it is really starting where it left off when it says 0 of 6422MB.[/quote]


the behaviour you describe does not sound like the bit-torrent client we discused in this thread, are you using gnome-btdownload?

I dont think gnome-btdownload have that "-save-from-same-location prompt" you descibe.

I suggest you start a new thread, to get the attantion you deserve.

---

### Post by Nivekk on 2006-06-22
Sorry for the delay... I ended up switching back into XP temporarily to just redownload all of it.

Honestly, I have no idea which BitTorrent I have... I am simply using what came with Breezy.  It exits if I don't provide a .torrent, and there are absolutely no options at all that I can change even when I am downloading.  

Nonetheless, I am certainly not going to use it anymore if I really can't resume anything.

---

### Post by scxtt on 2006-06-22
it resumes, i've resumed things more than a few times using the client that's installed in breezy by default ...

---

### Post by Nivekk on 2006-06-22
Well, I chose to resume after it asked me, but it started from 0 all over again.

---

### Post by kroiz on 2006-06-23
[quote=Nivekk]Well, I chose to resume after it asked me, but it started from 0 all over again.[/quote] 
I resumed many time and never had a problem.
maybe the part of the file you started to download got corrupted somehow.
or maybe you used a different user to resume and the program did not have the right permissions.

---

