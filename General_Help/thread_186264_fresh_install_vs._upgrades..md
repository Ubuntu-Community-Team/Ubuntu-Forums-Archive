---
title: "fresh install vs. upgrades."
date: 2006-06-01
forum: General Help
---

### Post by pedwards on 2006-06-01
so ive been using dapper for 3 months now (upgrade from Breezy)  and im contemplating killing my SWEET compiz / full costum setup desktop and install from the fresh iso. 
ive kept my system up do date so my repositories concurrent. 
Are there any advantages to dumping my breezy=>Dapper  and load up a fresh Dapper?

I am no stranger to reinstalling its my favorite way to fix a problem i dont want to waste time troubleshooting.

---

### Post by turbojugend_gr on 2006-06-01
I had my reinstall done, pretty much ok, less than an hour to have my system ready, no need to say that the things you need to customize are SO SO little!!!

Great work by the devs, do not re-isntall if you have absolutelly no issue, but if you have one I am prettt sure that the Final release will fix it fine, all mines gone away and the only way to remember is to look for them in my TOMBOY notes (i brought them along from breezy)

---

### Post by pedwards on 2006-06-01
thanks for the advise

---

### Post by Rackerz on 2006-06-01
I did a fresh install, well worth doing ;).

---

### Post by tha_rainman on 2006-06-01
[QUOTE=Rackerz]I did a fresh install, well worth doing ;).[/QUOTE]

Don't mean to be offensive, but *why* is it worth doing? It may be easy to do as turbojugend_gr said but is there any other reason?

---

### Post by ericesque on 2006-06-01
I don't think there is any reason unless you simply want a fresh install.  To my understanding, updating will give you the same system as a fresh install-- except a fresh install might be less fragmented, but you'll lose any configuration you've done.  Sounds like a trade off.  If it were up to me, I'd just update.  If you decide to reinstall down the line, so be it.

---

### Post by magomago on 2006-06-01
[QUOTE=Rackerz]I did a fresh install, well worth doing ;).[/QUOTE]
Unless you fubared your setup I don't see the reason...

I went from Hoary to Breezy through an update but it reallly mesed up a lot of things...hence I fresh installed
But early on I jumped Breezy to go to the Dapper at Flight 5....and I easily updated my way through.  

If you were using the Dapper Beta, stick with it...bercause its the same thing

If you were using Breezy and dist ugraded (Assuming you backed al lyour info up) and had MANY problems like I did then fresh install

either way...try to update first because its less of a hassle...


Btw to the person who said "Fresh reinstall to any problem"...that really makes no sense, and probably lessens your knowledge about the computer.  Things in Linux are meant to be documented, not so we have some obscure windows error that makes no sense so reformatting is the only way...

The only way I'd agree with a straight format is if your box's security was compromised.

---

### Post by blakamin on 2006-06-01
I had Dapper RC on the 25 and only upgraded pretty much open office!!!:rolleyes:

(maybe a couple of other files)
But I didn't want to play with my 6 email accounts and non-dhcp networking again

---

### Post by rcarring on 2006-06-01
The OOo upgrades are legendary, every day for almost a week, it was like 100mb download of updates, and there among them was OOo. I am convinced that one download was done simply to get the menu item name changed from OpenOffice Writer to OpenOffice Word Processor (ubuntu12 revision).

I had bad times with my Breezy to Dapper upgrade, with init files doing weird shit and so on, so I took the view of a fresh install, plus it gave me a chance to see how quickly I could get it all setup.

---

### Post by joshrobinson on 2006-06-01
if you have no problems updates are fine, and after the updates if there is no problems you are all good.. some of the dapper updates screwed up my touchpad on my laptop, and a clean install fixed the problem

so i would only do a clean install if something is wrong, or you are bored and want to do it for the hell of it :mrgreen:

---

### Post by pedwards on 2006-06-02
hey all i just finished my fresh install and the only real trade off i accopmlished was alot more hd space.   

but the satisfaction of seeing dapper boot up from nothing was amazing, 
its nice to see a finished product by the ubuntu team and a clean polished desktop. 

oh and by the way magomago learn to take a joke,

---

### Post by sedatg on 2006-06-02
i did a fresh install.

don't quite know what was wrong with my previous installs but the following things have changed:
- hibernation started working (with stock drivers) !
- much much much much much snappier desktop
- couldn't logout and log back in before, magically solved now
- had stale items in my menu (of apps i removed), now it's clean
- got rid of all kde stuff i had to install to fulfill dependencies

everything works out of the box now, only thing left to do is:
- get n run easyubuntu
- get n run diskmounter
- get my fat32 partition with all my data to be used as /home (need some help here, somebody help me out please ! )

on a sidenote though:
- i did manage to get the live-cd installer to crash several times:
switched back and forth between gparted and the final step in the install process a dozen times, as it wouldnt recognize the changes i made, so i couldn't choose my mount points as i intended to... solved this by blanking the linux partitions and let the remaining space be divided by the install itself (resized later by running gparted from the live-cd ;) )

brgds

---

### Post by ericesque on 2006-06-02
it should be as simple as going into  System>Administration>Disks 

*enter password
*select partitions tab
*select the fat32 partition
*click change (next to access path)
*use the left hand panel to navigate to your home folder
*click ok

double check by going back where you set the path to make sure it sticks.  If that doesn't work, start a thread.

---

### Post by RAOF on 2006-06-02
[QUOTE=sedatg]...
- get my fat32 partition with all my data to be used as /home (need some help here, somebody help me out please ! )
...[/QUOTE]
Did this work before?  It's a terrible idea - FAT just doesn't support all the features that linux programs will take for granted.  It doesn't support file permissions **at all**, so I **know** that this will break at least SSH & GPG, 'cause they all want to write files to /home with very specific permissions, and won't work if the files don't have those permissions.

You could mount your FAT drive somewhere under /home (like /home/shared, or something), or even under your own home directory (/home/chris/fatdrive) or whatever.  But it's a bad plan to have it as your /home (or any other important directory).

---

### Post by sedatg on 2006-06-02
hijacking this thread (work in progress) :p

i currently dual-boot between xp and dapper.
for the curious, need xp for: swishmax (or flashmx), dreamweaver, utorrent (not a single finished torrent manager program on linux besides azureus which dapper can't handle well due to some bugs), cs:s and playlist support for ipod (thx to winamp 5.22).

ALL of my data is kept on this particular fat32 partition, and my documents is redirected to the root of this partition too.
i want my dapper setup to be as similar as possible to my xp setup. i don't really mind if my config settings are stored in hidden folders on my linux partition (this won't eat too much space after all), but it sure would be nice as it can be considered a (lousy) backup.
what i absolutely want is the following. the /home folder is ubiquitous in dapper, and nearly all programs expect to store their data in there. this results in almost all save dialogs to start in /home. the idea is to  avoid as many mouse clicks as possible (having to navigate through a lot of folders every singly time you want to save or open a file is just plain stupid, IF it can be done in a better way), because that's the whole idea of storing everything in home right?

GPG and SSH not working is too bad, but xp also absolutely has to be able to acces all my date easily, so need a shared partition in the most simple way possible (which i figured a fat32 partition was)... i absolutely want to avoid that extra folder i have to click on in above posted solutions.

welcome any feedback, suggestions or advice.

brgds

---

### Post by pedwards on 2006-06-02
the wiki has EXCELENT documentation on what your trying to do. 
it introduces the fstab function. 
i found it easier to just use the fat drive as an extra drive mounted in /media/ 
it appears on the desktop so you dont have to worry about having hidden folders for your linux profiles.

---

### Post by dglock on 2006-06-02
I am still running beta 3 on this comp, what repositores do i need to update to the final release? When i try to do a dist upgrade it shows no packages to upgrade, that makes me think i need some different repositories.

don

---

### Post by pedwards on 2006-06-02
gksudo "update manager -r"
try that it should give you the newest release 
the one i used to update from breezy to dapper 3 months ago was -d for develpment this one is -r for release.

although i would recomment a fresh install if you want all the goodies. it it isnt too much of a hassle to get all your stuff back.  Network manager worked out of the box, and my hibernation/suspend is much more responsive.

---

