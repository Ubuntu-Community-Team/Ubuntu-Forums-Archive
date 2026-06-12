---
title: "Music tag type"
date: 2006-02-16
forum: General Help
---

### Post by idtt2s on 2006-02-16
What is the type of the tags produced by Amarok?

I edited tags of some songs in Amarok for Chinese, and they appear very oddly on my MP3 player.

---

### Post by z-vet on 2006-02-17
amaroK works with both ID3V1 and ID3V2 tags. I think you have some encoding problem. Maybe [EasyTag](http://easytag.sourceforge.net/) will help you to get tags with right encoding. And look in amaroK's settings, there is an option to change tags' encoding too. And, at last, maybe your device have problems with encoding? It happened to me too with russian tags on my mp3 player.

---

### Post by idtt2s on 2006-02-17
I used to use EasyTag under Gnome, which didn't work.

How did you get your MP3 player to work? Please note that my MP3 player can definitely display Chinese.

---

### Post by z-vet on 2006-02-17
Well, my mp3 player was just standard USB device, i connected it to computer and it was recognized as mass-storage USB device with vfat filesystem. New amaroK have a built-in support for these. But it never worked good with tags encoding different from standard iso-8859-1, even utf-8 caused problems and wasn't displayed correctly. 
And for EasyTag...what do you mean by "didn't work"? I used this app under various *nixes, even FreeBSD, and never had a problem with it.

---

### Post by idtt2s on 2006-02-17
EasyTag would write a tag, I would open the file in Banshee, but it doesn't display correctly.

---

### Post by z-vet on 2006-02-17
You need to check which encoding you use when write tags. And which encoding your music apps use to read tags, because if your tags are written in utf-8, and your player thinks that they are iso-8859-1, you've get a bunch of crap instead of info. Keep in mind that iso-8859-1 is a standard encoding for ID3 tags. It's confusing, i know, but once you set it up properly you will have no problems with it.

---

### Post by idtt2s on 2006-02-17
I write them using UTF-8 in EasyTag then open them in Banshee, but they're still messed up. In fact, even if I edit them in Banshee then reload, it's changes to something odd  as well.

---

### Post by binarymelon on 2006-02-18
That's an issue with the banshee that is in the default breezy repositories.  You can download an updated version from the apt.filefind.net repo.  Add the following to your /etc/apt/sources.list:

```
deb http://apt.filefind.net/ breezy main contrib non-free
```

And then run the following commands:

```
sudo apt-get update
sudo apt-get upgrade
```

But use this at your own risk.  Their are still some major issues with that version of banshee.  Although I'm hoping for an upgrade in the next week or so.

---

### Post by idtt2s on 2006-02-18
I've solved the problem for my MP3 player by using Chinese Simplified Mode and encoding the files using a Chinese encoding (GB2312). But apparently this still confuses Banshee, even the new one. So what can I do to let Banshee recognize the new encoding?

---

