---
title: "Recover Programs After Re-Install With Seperate Home Partition"
date: 2009-12-25
forum: General Help
---

### Post by peejaroni on 2009-12-25
Hey everyone, 
So my installation got weird/corrupted/something bad happened, so I re-installed. Being the good Ubuntu user that I am, I obviously had a separate home partition, so all my data was safe. The re-install just finished, and all my files are still here, and I have all my preferences for the default applications, and the new ones I installed. However, all the additional programs I installed aren't here. Since I wasn't planning on re-installing until I couldn't boot anymore, I wasn't able to create a list of all the programs I had, is there a way I can easily re-install them all from the data in the saved home partition, or will I need to do them all one by one?
Thanks!

---

### Post by taurus on 2009-12-25
When you install additional apps on your machine, chances are they will be installed in /usr/bin so if you do a reinstall with your machine, you need to install those apps again.

---

### Post by peejaroni on 2009-12-25
Thanks for the quick reply, 
I know that all my settings will stay the same, but there is no shortcut command that will go through my home folder, or some archive that sits in it, and re-install everything I used to have without me having to remember what they were?

---

### Post by Strongman332 on 2009-12-25
I know that isn't helping but searching Google for another problem I have seen something that could be your solution. it produced a terminal command that you could use to reinstall your programs.
so the solution does exist

---

### Post by stinkeye on 2009-12-26
I don't think you can get a list now because all your downloaded deb files are stored in /var/cache/apt/archives
but for next time I would look at [_[COLOR="DarkRed"]APTonCD[/COLOR]_]("https://help.ubuntu.com/community/APTonCD")

---

