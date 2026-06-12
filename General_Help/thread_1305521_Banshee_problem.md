---
title: "Banshee problem"
date: 2009-10-29
forum: General Help
---

### Post by ahowie111 on 2009-10-29
okay i just upgraded to 9.10which is awesome.. i was using banshee to manage my music on my ipod and my G1 with no problem before.. but now when i plug my ipod in..banshees starts up but it does not show up in the list on the left like it did before..  any ideas?

---

### Post by mas1234 on 2009-11-01
Me too... disappointing.  Any resolution?

---

### Post by zwyber on 2009-11-01
I have the same problem, and after some research I know the problem. In ubuntu 9.10 they have been cleaning up some old deprecated libaries. The library that more or less connects Banshee and your iPod is called podsleuth. This library doesn't work properly anymore.

So basicly for now, no iPod + Banshee. Many other solutions won't work either, because they too depend on podsleuth.

My solution is to run 9.04 in a VirtualBox and use that to sync my iPod. BTW make sure you don't get the OpenSource version of Sun VirtualBox, because it doesn't have the USB drivers. Download it from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads). Or follow the guide here.

1. Add the repository:
System > Software Sources > Sources > Add Source : 

```
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

```

2. Add key"
Start up a Terminal > ```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

3. Update & Install
In the terminal
```
sudo apt-get update
sudo apt-get install virtualbox-3.0
```

---

### Post by mas1234 on 2009-11-15
Any updates here?  I would like to upgrade, but for now, I reinstalled 9.04 and am using that.  Don't want to get into virtual box at this point just to facilitate music.  I would rather skip 9.10 and continue using 9.04 which for me appears to be more stable anyway.  

Thanks for any updates on the issue though... anyone?

---

### Post by devehf on 2009-11-16
This is terrible news. I was trying to find an alternative to Amarok 2.2 because there are so many deficiencies:
1) Can't drag and drop files from the current playlist to saved playlists.
2) Can't manage files in the library on disk
3) Can't easily filter recently added music
etc.

I was starting to like banshee until I found that I couldn't sync my pod. Bummer.

---

