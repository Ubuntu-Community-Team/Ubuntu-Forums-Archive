---
title: "iphone 3gs sync with ubuntu?"
date: 2009-09-08
forum: General Help
---

### Post by dgould0622 on 2009-09-08
Does anyone know how to sync an iphone 3gs with ubuntu 9.04? i installed itunes from wine and it runs somewhat fine but my phone isnt recognized when i plug it in. any suggestions?

---

### Post by dgould0622 on 2009-09-08
bump

---

### Post by Lyerae on 2009-09-08
I was just about to post the same thing.
I really need a program to sync my iPod Touch (3.0)...

---

### Post by falconindy on 2009-09-08
There is linux based ipod/iphone software out there. However, according to [this](https://help.ubuntu.com/community/PortableDevices/iPod), syncing an iPhone is ugly as you have to SSH into the device via wifi.

---

### Post by lildigiman on 2009-09-08
please don't bump unless its been 24 hours since initial post.

As far as the iPhone 3g, you need to jailbreak it, because the USB connection is encrypted.

[http://ubuntuforums.org/showthread.php?t=861681](http://ubuntuforums.org/showthread.php?t=861681)

that may help.

---

### Post by Marlonsm on 2009-09-08
Ubuntu is able to sync with iPhone, the problem is: Apple doesn't want it to happen.
So you either jailbreak or use Windows or OSX (could be on a virtual machine) to do it.

---

### Post by Lyerae on 2009-09-08
We have to jailbreak....?
Great, now I need to convince my parent's to let me...

---

### Post by alejaaandro on 2009-09-08
even after jailbreaking it it's kinda too much of a fuss (talking about itouch, but it's almost the same), so if you have a mac of win available (dual boot or something) that would be better..
not sure if vm works.. i remember trying it some time ago, had to tweak something (which i believe i found in a forum of virtualbox) and got it, but for some reason (can't really remember) i wasn't satisfied and tried the ssh solution..

bad thing, after every major upgrade of the ipod, you'll probably won't be able to sync, until a solution is found again cause usually apple tries to make it harder.. i believe there's no way to sync if you have firmware 3.x, but i might be mistaken.. i remember there is some good documentation in help.ubuntu... just make sure it's not outdated (referring to previous firmware)

---

### Post by Lyerae on 2009-09-08
Ugh....
I really, *really* don't want to have to boot into Windows just to sync. I switched to Ubuntu to get away from Windows...

If I find a way to jailbreak on 3.0, what else do I need to do?
Do I just need a sync program, or what?

---

### Post by alejaaandro on 2009-09-09
install open ssh on your ipod/iphone, ssh to it, install a program to mount your ipod to your filesystem using ssh, use gtkpod or amarok to sync.. 

this is really a resume, not full instructions.. you should google it, you'll find full and good how to's.. 

i haven't done if for i while cause my bro bought a mac and i use that to sync, but from what i remember, you could only sync music.. no pics, not sure about videos, no apps..
there might be are workarounds though.. in the installer (like synaptic for jailbroken ipods) i remember i saw mplayer, so if you put the videos in the correct folder, i guess you could play them (but not from the original ipod's video player).. apps are installed by putting them in the correct folder too, so that can be done..

virtual box might have been fixed too.. it's been a couple of years since i tried it..

EDIT: [here you go]("https://help.ubuntu.com/community/PortableDevices/iPhone")

read the whole thing first, so you don't mess up
> As of now (22nd of June 2009), there is no alternative to iTunes when it comes to syncing with an iPod Touch or iPhone with Firmware 3.0
so, syncing with the original database is not possible, but you might be able to upload music to your ipod and play it with other music players installed from the "installer".. note that (i think) this has drawbacks: you'll see your music as files and not as a library you can browse on genre/artist/album, or view artwork..
i know this sucks.. send an email to apple to complain, though they'll probably ignore you..

---

### Post by alejaaandro on 2010-01-19
it's been a while since ipod touch and iphones, even with 3.x firmware, are able to sync from linux and quite easily using the cable and not through wifi.. This is thanks to ifuse..

> It's possible now (Decembre 28th, 2009), instructions are provided on these sites: [http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux-part-2/)

[http://www.mexlinux.com/how-to-sync-music-between-iphone-and-ubuntu/](http://www.mexlinux.com/how-to-sync-music-between-iphone-and-ubuntu/)

[http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html](http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html)



---

