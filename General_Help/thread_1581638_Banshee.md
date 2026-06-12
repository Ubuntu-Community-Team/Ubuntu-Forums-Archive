---
title: "Banshee"
date: 2010-09-25
forum: General Help
---

### Post by DeMus on 2010-09-25
Hi,
I use Banshee as music player and I am very pleased about it. It's a nice program which does what it should do (play music) and t has little resources which leaves me possibilities to do other stuff.
One question however:
In my long list of songs I have a lot of titles which have the code %20 in the name, representing the "space". I hate that.
Is there a way I can simply edit the list of entries and exchange %20 with "space" in one time? The alternative (changing each song one by one) does not sound very appealing.
Who can help me?

---

### Post by lykeion on 2010-09-25
Banshee uses the metadata (i.e ID3 tags for mp3 files) to set the titles. I guess if metadata is missing it uses the filename.
 Apparently there's a bug in Banshee so it fails to decode the filename URL before setting the name of the track. 
This has been fixed in v1.7.3 see [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/602201](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/602201)

So...you could either tag your music files - EasyTag is really handy for quickly tagging lots of files - or you could try to get a later version of Banshee. 
I'd suggest the first option, but if you'd like to try the other I could try to help you with that.

---

### Post by DeMus on 2010-09-25
> **lykeion said:**
> Banshee uses the metadata (i.e ID3 tags for mp3 files) to set the titles. I guess if metadata is missing it uses the filename.
 Apparently there's a bug in Banshee so it fails to decode the filename URL before setting the name of the track. 
This has been fixed in v1.7.3 see [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/602201](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/602201)

So...you could either tag your music files - EasyTag is really handy for quickly tagging lots of files - or you could try to get a later version of Banshee. 
I'd suggest the first option, but if you'd like to try the other I could try to help you with that.

I just added a PPA for Banshee but it also has the same 1.6.1 version of Banshee. Where did you find the 1.7.3 version?

I am now editing the tags using easytag, let's see what comes out of that.

---

### Post by lykeion on 2010-09-25
Hope the tag editing solves your problem.

Regarding getting a later version of from PPA, you'll also need to add the Banshee Daily Builds PPA. 
They recommend adding the Banshee PPA first, but you've already done that.

[https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

---

