---
title: "No Tracks listed in Amarok Local Collection"
date: 2010-07-12
forum: General Help
---

### Post by Jeffa on 2010-07-12
Hello, 

I'm having a little trouble getting my music tracks to display in Amarok's Local Collection. I've gone to Settings>Configure Amarok>Collection and checked the directory that contains my music. I then clicked the "fully rescan entire collection" and amarok appears to scan the collection. But when it finishes, nothing appears in my Local Collection. If I go to "Files" instead, I am able to navigate to individual mp3's and play them without issue. I have installed all the required restricted extras and xine backends, so again the mp3's play fine. I just can't get them to appear in the "Local Collection". The files are located on a RAID 5 array with a hardware raid controller, but I don't see how that would make a difference. I point amarok to the mount point (media/sdb1/music). but I get nothing. Any ideas as to why I can't get my music to appear in the "Local Music>Local Collection"? 

Thanks community!

---

### Post by shnuggles on 2010-07-12
I'm having the same trouble. Amarok worked fine and my collection all appeared, but after upgrading to ubuntu 10.04, Amarok won't detect anything. Everything plays fine if I manually add it. I've also tried the steps mentioned by Jeffa. Not a serious problem but annoying for sure.

---

### Post by s_shuffle on 2010-07-13
Hi I've just ""resolved this"" by going to the Amarok  site and added their repository and updated the application. When I launched the first time after the update it took a bit longer start ( probably an Db update ?? ) but My local files are now showing in amarok...
Thanks
tchau

---

### Post by Jeffa on 2010-07-13
I can't seem to find the repositories on amarok's website. Could you share that information? 

Thanks.

---

### Post by Jeffa on 2010-07-13
OK, I finally got this working. Here's what I did:


From [this site]("http://ubuntudoctor.com/content/video/06/Amarok-2.3.1-Installation-on-Ubuntu-10.04"), I entered the following into a terminal:

To Install the PPA:
```
sudo add-apt-repository ppa:kubuntu-ppa/backports
```

Then to upgrade:
```
sudo apt-get update && sudo apt-get upgrade
```

That finally upgraded amarok to 2.3.1. That has fixed the two bugs of being able to see my collection in "Local Collection" and amarok shuts down properly. 

Hope this helps everyone.

---

### Post by orthopod on 2010-07-15
Thanks - I was having the same problem, and this was the only solution that worked for me.

---

### Post by malspa on 2010-07-22
@Jeffa -- thanks for the tip!  I was having the same problems in Mint 9 (Isadora).  Used this solution and it solved both problems here, too.

---

### Post by variona on 2010-07-22
Found on launchpad: The problem with Amarok's collection is also solved if you install mysql-sever-core-5.1
HTH
variona

---

### Post by malspa on 2010-07-22
> **variona said:**
> Found on launchpad: The problem with Amarok's collection is also solved if you install mysql-sever-core-5.1
HTH
variona

Ah!  Well, after doing the fixes mentioned here, mysql-server-core-5.1 is still not installed, but everything's working fine.  I wonder if I should install it.

---

### Post by hollowhead on 2010-07-31
Thanks that's solved that problem but sinmce I installed libs for seeing touch amarock won't see nanos it says " Media Device: could not find iTunesDB on device mounted at /media/IPOD. Attempt to initialise your iPod?"  Surely this will delete everything on it (in effect)?

---

### Post by digital-daniel on 2010-08-04
I followed all the instructions above and still nothing.

Then I went to set up and I discovered that I didn't need to have use external My external SQL database ticked. I removed the tick  and all my music appeared in the collection. 

Daniel

---

