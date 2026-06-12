---
title: "k9copy 2.3.6 still can't do Disney movies?"
date: 2010-11-11
forum: General Help
---

### Post by BuddyThirteen on 2010-11-11
I've tried pretty much every DVD ripping program available, DVD::Rip, DVD95converter, DVD Movie Backup. My favorite backup program is k9copy (easiest to use and has all the features I need). But no matter what I try, certain Disney movies just won't backup. Specifically, at the moment, many of the Miyazaki/Studio Ghibli films.

After selecting the disc, the program either crashes out immediately, or it starts filling up the memory, slowing everything down, until finally it crashes. I thought updating to the newest version would maybe help (not even available through standard "Update Manager", had to find it myself), but the same problems occur.
 I'm currently trying with ddrescue, hoping that works. But I don't really like the idea of using a series of programs to get the output I want.

Is there a program that can backup, compress, and convert a Disney movie into a playable/burnable ISO file? Because these films are Japanese, and I use them to help me practice, I would definitely prefer something that can output normal switchable subtitles and audio (as opposed to an MPG or AVI that just has the one audio track).

Fairly novice-y, so step-by-step would be best, thanks!

---

### Post by houseworkshy on 2010-11-11
I can't swear to this but for encripted dvds one generally need to install ( and it is in the repositories ) libdvdcss, install via synaptic as there is more than one version and you can read the descriptions there.

---

### Post by BuddyThirteen on 2010-11-11
> **houseworkshy said:**
> I can't swear to this but for encripted dvds one generally need to install ( and it is in the repositories ) libdvdcss, install via synaptic as there is more than one version and you can read the descriptions there.
I've got all that. Everything runs and plays just fine. I can watch the movies in VLC if I want, but I really want to make backup copies (so the originals don't get all scratched up by the young'ns). Most movies work fine, but Disney-branded Miyazaki refuses to work.

---

### Post by alphaamanitin on 2010-11-11
I don't believe it has a Linux option but I think DVDFab should solve your problems.  YAY for fair use.  I don't expect we will have the right to make back-up copies for much longer though, not the way the corporations have been destroying fair use.

Also, have you tried to make and .iso out of them with the dd command?  Not sure it will work though.

AlphaA

---

### Post by BuddyThirteen on 2010-11-11
Okay, well ddrescue did seem to work. It copied the entire thing flawlessly. The ISO file is full size, though, so no burning to a single layer disc. I'm now going to try to use k9copy to create a compressed ISO (preferably with just the movie title (which is Title 51--because one form of obfuscation is never enough)). Hopefully it'll work. If the copy is *too* faithful, it will also have copied the problems.

Many of these aren't new movies, though. When is k9copy going to be able to handle these Disney discs?

[edit]: Nope. Didn't work. The ISO copy that was created is just as uncopyable. Memory overflow almost instantly. And playing the ISO as is would be fine, I guess, but it hangs at every chapter change. And I'd really rather burn it.

---

### Post by colin.p on 2010-11-11
That is the only reason I still have a dual-boot with win. There is no "reliable" way to copy (backup) commercial DVD's in linux, at least that I have been able to find. Until then, I will have to boot into win to copy a DVD, which is becoming more of a rarity these days. Unless someone comes out with a linux version of our favorite copy program, or it works as good in wine I suppose.

---

### Post by BuddyThirteen on 2010-11-11
I used to dual-boot, but I sorta borked the bootloader during the upgrade to 10.10, and since Dell, in its infinite wisdom, no longer includes Windows install discs, I sorta just had to wipe the drive and install Ubuntu entirely. (Tried tons of things to fix the problem first, nothing took.) So far, no regrets. Everything is getting to the point where I'm just as productive now as I was before. Other than this minor problem. But I suppose I can just take those rare DVD's that won't backup easily and try it on my (Windows7) laptop with DVDFab or somesuch. Alas.

---

### Post by rianocerous on 2010-12-28
While I definitely wish there were a better option (and strangely, some Disney DVD's seem to work for me ok, while some do not), if you haven't tried it, DVDFAB does run pretty well through Wine.  

I've used it successfully several times.  Try it, and you may not need to dual boot

---

