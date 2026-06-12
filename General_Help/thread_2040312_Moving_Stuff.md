---
title: "Moving Stuff?"
date: 2012-08-10
forum: General Help
---

### Post by Akacheebe on 2012-08-10
OK so I'm switching back to Ubuntu 12.04 from Mint 12 and I need to find out how to save my favorites and other data from Firefox, Opera, Chrome and Filezilla.  I know it's possible to do this because I've done it on a Windowz system but searches here haven't given me what I need to do this?

Any help?

Thanks,

Akacheebe

---

### Post by GWBouge on 2012-08-10
Firefox and FileZilla save their stuff in hidden directories in your home folder.  So, check out ~/.mozilla and ~/.filezilla

I'm not sure about Chrome or Opera, but if you don't see something like ~/.opera and ~/.chrome, look in ~/.local/share or ~/.config

---

### Post by ads52 on 2012-08-12
I can only speak for Firefox, as my browsing needs are fairly primitive, where you can easily export your bookmarks as a single HTML file:

Bookmarks --> Show all Bookmarks --> Import and Backup --> Export Bookmarks to HTML

Is this sort of information what you are after?

---

### Post by CaptainMark on 2012-08-12
The best way would be to back up every hidden folder in your home directory. The simplest way to do this is open your home folder in a file browser press ctrl+h to view hidden folders and copy every folder beginning with a full stop to a usb stick, then on your new install copy them back asap, you should have all your preferences for most applications saved then

Edit: look here for help on creating a separate home partition when you install [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
It will save you the worry of faffing with copying data and configuration files on a reinstall and makes your data a little safer from corruption all in one fell swoop, there are very few downsides in my opinion

---

### Post by Akacheebe on 2012-08-16
Thanks ppl for the replies but it doesn't look like there's an easy way to do this without a bunch of command line stuff, which I know very little about.  

Hate to say this but in Windows I just copy the stuff, ie, favorites, cookies, and sometimes the folder from the Program Files menu, etc on to a flash drive then copy and paste it into the new load.  Can't do that with Linux, or at least I haven't found a simple way to do it.  

Guess I'll just stumble along and do everything over again.  

Thanks again.

Akacheebe

---

### Post by unevenflow on 2012-08-16
Hey, yes you can
in your home folder hit Cntrl+H then copy paste everything into your flash drive and after reinstalation open your flash drive and again hit Cntrl+H and copy paste everything to your new home and you're done but i strongly suggest this time to follow
> Edit: look here for help on creating a separate home partition when you install [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
It will save you the worry of faffing with copying data and configuration files on a reinstall and makes your data a little safer from corruption all in one fell swoop, there are very few downsides in my opinion as CaptainMark suggested.
cheers

 Edit: you may also check /opt and see if there is sth there by using
```
gksudo nautilus
```

---

### Post by ads52 on 2012-08-16
> **Akacheebe said:**
> .  Hate to say this but in Windows I just copy the stuff, ie, favorites, cookies, and sometimes the folder from the Program Files menu, etc on to a flash drive then copy and paste it into the new load.  Can't do that with Linux, or at least I haven't found a simple way to do it. 

Won't take long to get used to the Linux way. Don't forget that the file structure and permissions are what makes Linux so secure, Windows is very 'open' and suffers because of this.

---

### Post by Khal1d on 2012-08-16
I vote copy/paste the home folder.

It cures most of my needs... :O

---

