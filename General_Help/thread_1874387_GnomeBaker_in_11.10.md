---
title: "GnomeBaker in 11.10?"
date: 2011-11-03
forum: General Help
---

### Post by linuxaddix on 2011-11-03
i searched google and the software center and no pckage builds for gnomebaker in 11.10.why is that?gnomebaker is the most reliable burner in my opinion and i think it should automatically come with distros instead of brasero.brasero isnt that reliable.a lot of messed up cds happen with brasero.anyone know how to get it for 11.10?

---

### Post by linuxaddix on 2011-11-03
and as ive said....another cd bites the dust.brasero sukks

---

### Post by deserthowler on 2011-11-03
The gtk3 toolkit is still being developed and a lot of things haven't been ported to that toolkit yet and maybe will never be.  I use k3b and have since 5.10 (if I remember correctly).

Earl

---

### Post by linuxaddix on 2011-11-03
i found k3b a bit confusing with all the setting features.with gnome baker i just click away and it burns.all im trying to do is burn iso images.is it easy on there?

---

### Post by mikewhatever on 2011-11-03
Doesn't look like Gnome Baker is still active. According to its home page, the last release was from June 2008.

---

### Post by crdlb on 2011-11-03
gnomebaker was removed from debian because it is unmaintained and bitrotting: [https://launchpad.net/ubuntu/oneiric/+source/gnomebaker/0.6.4-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnomebaker/0.6.4-1ubuntu1)

You could try downloading the [Natty version]("https://launchpad.net/ubuntu/natty/+package/gnomebaker"). I can't promise it'll work.

---

### Post by viperdvman on 2011-11-03
Well that very much sucks. I use GnomeBaker for most of my burning needs in Ubuntu. Brasero, however, I've only had success burning with it when burning Linix distro isos to DVD's. With stuff like Data DVD's, I've turned a couple of DVD+R's into shiny coasters. So yeah, it sucks.

I haven't played with K3b enough yet, so I ought to try it out some more and get some experience with it.

---

### Post by linuxaddix on 2011-11-03
thats terrible.im surprised you got it working burning linux iso's i just burnt archbang with brasero and it was a total failure.im over brasero.im actually beginning to be over linux even though i love it.too much errors and stuff.thinking of going back to winblows 7.

---

### Post by viperdvman on 2011-11-03
Nah, don't leave Linux completely 'cause Brasero sucks and GnomeBaker isn't being updated. There are plenty of other choices out there, with K3b being the most popular. Check the repositories.

Yeah, I'm surprised too that I've had no problems burning Linux distro isos with Brasero, despite hearing and experiencing how much it sucks at burning everything else.

---

### Post by rtimai on 2011-11-03
davdo2004,

I appreciated your comment about K3B. It's the only burner application that I've had success with. The others wouldn't recognize that there was a blank CD in the drive for some reason. And I successfully burned my first DVD data disc with it. It does seem odd however that Ubuntu doesn't have a good native burner. 

rti

---

### Post by viperdvman on 2011-11-04
I agree. I (and a lot of people who've rated it on Ubuntu Software Center) think Canonical needs to ditch Brasero and adopt a better CD/DVD/BR burning app. K3b would be nice, but that's a KDE app (which works fine on GNOME/Xfce/LXDE).

---

### Post by deserthowler on 2011-11-05
> **linuxaddix said:**
> i found k3b a bit confusing with all the setting features.with gnome baker i just click away and it burns.all im trying to do is burn iso images.is it easy on there?

I don't know if it is easy or not as I've used it for so long.  I don't do settings; I burn things.  The settings confuse me too.  Use it for isos, music and data CDs and DVDs.  Maybe lose 2-3 CDs or DVDs in 100.

Earl

---

### Post by 3rdalbum on 2011-11-05
Brasero seems quite alright these days for me.

---

### Post by viperdvman on 2011-11-05
Like I said, I've had no problems burning ISOs of Linux Distros with Brasero. 

But twice, I've tried to burn Data DVD's (actually putting backup files on them) and have ended up with shiny coasters/christmas ornaments/rearview mirror decorations.

---

### Post by linuxaddix on 2011-11-05
got the k3b and it seems alright not too complicated but i havent tested out the burning yet.gonna compare the burn speeds cause gnomebaker burnt a 2gig iso for me in about 4 minutes gonna see if k3b is the same

---

### Post by 3rdalbum on 2011-11-05
> **linuxaddix said:**
> got the k3b and it seems alright not too complicated but i havent tested out the burning yet.gonna compare the burn speeds cause gnomebaker burnt a 2gig iso for me in about 4 minutes gonna see if k3b is the same

All Linux CD burning is done via the same backends. Doesn't matter if it's K3B, Gnomebaker or Brasero, the speed should be the same because it's always the same program doing the actual burning.

---

### Post by Perfect Storm on 2011-11-05
Give a NeroLinux a go, it never failed me. Though it aren't free and cost a couple of bucks ($19.95 to be exactly).

There's a 30-days trial to test it out: [http://www.nero.com/enu/downloads-linux4-trial.php](http://www.nero.com/enu/downloads-linux4-trial.php)

---

### Post by linuxaddix on 2011-11-06
actually i found brasero to be extremely slow with the burning process.what it takes for me to burn in gnomebaker doesnt even compare to brasero.4 minutes opposed to 16?do the math.gnomebaker is the best ive tried.so no it aint the same speed.
brasero does a lot of checksum image burning,which i know is important,but,extremely annoying.

---

### Post by jeremy on 2011-11-06
Xfburn works well in ubuntu 11,10

---

### Post by Rodney9 on 2011-11-06
Xfburn works well in Lubuntu 11.10

---

### Post by ubudog on 2011-11-06
+1 for k3b, pretty nice alternative.

---

### Post by linuxaddix on 2011-11-07
finally tried out k3b and i must say....im very impressed.just like gnomebakers speed 1.2gb in 4minutes38seconds.like ubudog said +1 for k3b.its excellent

---

### Post by tnt533 on 2011-11-07
> **3rdalbum said:**
> All Linux CD burning is done via the same backends. Doesn't matter if it's K3B, Gnomebaker or Brasero, the speed should be the same because it's always the same program doing the actual burning.

Then why, pray tell, will gnomebaker successfully burn an ISO of a movie that plays flawlessly in my DVD player but others will not on the same system, with the same iso file and the same media? It's killing me and, to be honest, may cause me to revert back to an older version of Ubuntu. I just tried building gnomebaker from source and the dependency errors are numerous. I'll keep at it and let you guys know if I can get it going.

I, for one, will miss gnomebaker greatly.

Edit: While I've tried k3b and other open products I've had no luck. I just installed Nero and, coupled with DeVeDe, created an ISO and burned to disc and low and behold it worked. I guess I won't miss gnomebaker so much after all.

---

### Post by linuxaddix on 2011-11-07
the k3b works perfectly.just as good as gnomebaker.and yes gnome baker will be greatly missed especially the sounds after creating the disc.but until they revive it im gonna stick with k3b

---

### Post by ubudog on 2011-11-07
> **linuxaddix said:**
> the k3b works perfectly.just as good as gnomebaker.and yes gnome baker will be greatly missed especially the sounds after creating the disc.but until they revive it im gonna stick with k3b

k3b can do sounds too!

---

### Post by linuxaddix on 2011-11-07
yeah i noticed but still miss gnomebakers sounds

---

