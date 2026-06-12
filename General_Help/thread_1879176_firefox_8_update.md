---
title: "firefox 8 update"
date: 2011-11-11
forum: General Help
---

### Post by linuxaddix on 2011-11-11
okay firefox 8 has been out for a few days and i wanna upgrade it.by that i mean not the beta version or nightly build that i keep running into while searching google.i want the actual ff8.if i download it i can access it by clicking the firefox icon.there is no ppa for it cause the web says there will be an auto update.when will that be.

---

### Post by An Sanct on 2011-11-11
Firefox checks for updates every time you run it, so the updates are automatic.

You can also click Help -> About [build name], where you see your Firefox update status, if there is an update, it will download and install after you restart firefox.

---

### Post by vasa1 on 2011-11-11
> **linuxaddix said:**
> okay firefox 8 has been out for a few days and i wanna upgrade it.....when will that be.

You'll know through update manager. You don't have to do anything else.

---

### Post by BillyBoa on 2011-11-11
I don't know if you want this

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```

Install the Mozilla PPA and see if you get Firefox 8 earlier.

---

### Post by mikewhatever on 2011-11-11
Vasa1 is right. As soon as FF8 is ready in the repositories, you'll get a notification. It's not ready just yet.

The 'ppa:mozillateam/firefox-stable' doesn't include packages for Ubuntu 11.10, besides, FF8 is not there yet.

---

### Post by linuxaddix on 2011-11-11
@Billyboa: does it make the actual ff8?
cause in your post it says "'i dont know if you want this?"

---

### Post by vasa1 on 2011-11-11
Even I would like to get the latest Fx8 but not to the extent of getting it via the ppa suggested above.

Is there a particular reason why you need it ASAP? I'd rather that the people who are working on it do a thorough job (on the integration with Unity) and not a rushed one.

---

### Post by pqwoerituytrueiwoq on 2011-11-11
if you do not feel like waiting on a ppa update
this [script]("http://ubuntuforums.org/attachment.php?attachmentid=206986&stc=1&d=1321067252") will set it up for you (Do NOT run as root)
to remove it
```
rm -r ~/.firefox;rm Desktop/firefox.desktop
```

also works with other version of firefox just edit line 2 with the desired firefox version number

---

### Post by linuxaddix on 2011-11-11
no particular reason i just like to keep everything up to date

---

### Post by linuxaddix on 2011-11-12
@ pq:didnt work but thanks anyway

---

### Post by linuxaddix on 2011-11-12
also at billyboa:
that also didnt work,now getting errors while updating.now time to do a quick fix

---

### Post by pqwoerituytrueiwoq on 2011-11-12
can you eliberate didnt work?
open terminal and run it with sh
[FONT=Courier New]sh ~/Downloads/install\ firefox.sh[/FONT]

---

### Post by linuxaddix on 2011-11-14
thanks pq that did it.one last question:i now have the ff8 and ff7 how do i remove ff7 and how do i add the new ff8 to my favorites bar in gnome 3?

---

### Post by pqwoerituytrueiwoq on 2011-11-16
i would not remove ff7
not sure how to add launchers in unity, sorry

that is meant to me a system safe way to use any version of firefox and not break the os
to replace ff7 you just need to update your launchers i am still using gnome2 here

---

### Post by dniMretsaM on 2011-11-16
I would just stick it out 'till the 8.0.1 upstream release. The update bugs that are holding it back will be fixed and it will be in the repos within two days.

---

### Post by linuxaddix on 2011-11-16
its gnome 3 btw.i found the package but dont know how to build it.

---

### Post by Nuafite on 2011-11-17
Good idea to wait for 8.01. Firefox 8 was in the Update Manager this morning so I updated. Big mistake. I see from the Software center that what went wrong on me is **8.0+build1-0ubuntu0.10.10.1~mfs2 (firefox)** - I'm still on 10.10.

Accessing any website froze Firefox. I tried rebooting, same thing. Tried uninstalling extensions, no joy. 

I'm involved in some serious work for which I need Firefox and the Zotero extension so in desperation I uninstalled Firefox in the Software Center, and downloaded 8 from the Mozilla site. That works absolutely fine, but I have to launch it from Opt each time - neither gnome-shell or terminal knows anything about it. 

Maybe it's okay for 11.04 and 11.10. 

Just thought I'd put it on the record and if anyone knows how to get the launcher working after a manual download I'd be grateful.

---

### Post by Vaphell on 2011-11-17
create bin directory in your home and symlink firefox binary there. Ubuntu detects that dir and adds it to PATH variable when you log in. Or symlink it to /usr/bin. You would be able to run firefox in terminal without jumping through the hoops

launcher thing - go to /usr/share/applications and create/edit .desktop file for firefox. It is pretty straightforward, you'll figure it out (i'd advise creating normal launcher via gui but i don't know anything about gnome-shell).

---

### Post by Nuafite on 2011-11-17
Many thanks, Vaphell. I took up your symlink suggestion and was delighted when Terminal launched Firefox. 

Not so delighted when it started freezing again. I think I'll have to uninstall 8.0+build1-0ubuntu0.10.10.1~mfs2 (firefox), reinstall the manual download from Mozilla and symlink that, if that makes sense. 

Your second suggestion for the launch wasn't so straightforward, oddly, for me.  I'm spoiled by the Software Center and forget a lot of simple things. I know gnome-shell is complicating matters but I'm reluctant to uninstall it. Thanks again.

---

### Post by Vaphell on 2011-11-17
did you check if ff with fresh profile does that too? move/rename your .mozilla folder and run ff.

launchers are described in .desktop files, in /usr/share/applications there is a bunch of them and the executable file to be run is defined in Exec= line.
**Exec=/opt/firefox/firefox %u** would probably do the trick.

---

### Post by Nuafite on 2011-11-17
> **Vaphell said:**
> did you check if ff with fresh profile does that too? move/rename your .mozilla folder and run ff.
Yes, I'm afraid the fresh profile does.  I tried renaming the .mozilla folder and that seemed to make it worse, if anything. 

> 
launchers are described in .desktop files, in /usr/share/applications there is a bunch of them and the executable file to be run is defined in Exec= line.
**Exec=/opt/firefox/firefox %u** would probably do the trick.

Too tired to work this out tonight. I saw all the files in /usr/share/applications but I don't know how to create an executable file here (not sure if I'm making sense), so I don't know where to put **Exec=/opt/firefox/firefox %u** - though I did edit Preferred Applications to make Firefox default. 

Thanks very much for your time and consideration. Goodnight and sleep well.

---

### Post by 73ckn797 on 2011-11-17
> **BillyBoa said:**
> I don't know if you want this

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```Install the Mozilla PPA and see if you get Firefox 8 earlier.

This keeps FF up to date. It will come up as updates, like all other regular updates.

---

### Post by dniMretsaM on 2011-11-17
^^Only for 10.04 and 10.10.

---

### Post by linuxaddix on 2011-11-18
> **73ckn797 said:**
> This keeps FF up to date. It will come up as updates, like all other regular updates.

this updates it to the canonical beta version.looking how to install the actual version 8.0.1
i keep reading that the update will be available in update manager but no updates yet.

---

### Post by Nuafite on 2011-11-18
> **Vaphell said:**
> 
launcher thing - go to /usr/share/applications and create/edit .desktop file for firefox. It is pretty straightforward, you'll figure it out (i'd advise creating normal launcher via gui but i don't know anything about gnome-shell).

Just to update, @Vaphell, I noticed that when I launched Firefox 8 from Terminal, it froze, but when I double-clicked on firefox in opt, it was fine. Don't ask me why. So I gave up on the idea of creating a launcher icon in Gnome-Shell Activities, and created a launcher on the Desktop. I hadn't been able to do that before but I was accessing the Desktop from Gnome-Shell Activities. 

Not the most elegant of solutions, but I'll take time out to upgrade to Ubuntu 11.10 over the next few weeks and install Gnome-Shell 3 over that.  Meantime all is well :D and I can get on with my work. 

Thanks again.

---

