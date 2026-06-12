---
title: "Is there an NFS GUI Tool"
date: 2010-05-06
forum: General Help
---

### Post by chewit on 2010-05-06
Is there an NFS GUI Tool in Ubuntu, like there is in fedora, they have system-config-nfs

Can not configure NFS from command line at all.

---

### Post by bamdad.khan on 2010-06-12
yeah, i'd like to know, too. gshare uses (s)ftp, and 'personal file sharing' (the default one) uses apache (?).

i think there should be a gui tool for administering every parto of the system, including services (how long has that been missing? since 8.10 or so..) and sharing/nfs exports. it would be nice to have something for graphically editing grub(2) too.

while some of these can be found after intensive googling (e.g 'bum' for services, which is really alpha-quality), it would be nice to have an official, supported one.

maybe that's just me, sorry for making this look like a rant; it isn't.

---

### Post by ggallozz on 2011-01-30
the question 's having a long life...

Would you have a look [here ]("http://brainstorm.ubuntu.com/idea/2982/")?

Contribute also with your ideas.

---

### Post by HermanAB on 2011-01-30
Howdy,

NFS configuration is incredibly simple.  Any attempt at making a GUI for it will make it more complicated.

You only need to set ONE line on each machine.  So do some Googling for a howto if you cannot figure it out from the man page.

[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

---

### Post by klasw on 2011-07-17
I don't agree that its easier to edit a /etc/exports, its always easy to print wrong in a textfile. If we want to make a user friendly OS and get more people to go over to Linux , we need good GUIs.

---

### Post by glococo on 2011-07-28
Sad but true. GUI should be more easy far far away.

For example, I was tired of searching how to share one SIMPLE folder with 2 PC, without having sharing permision problems.

One client user with ID 1001 and other client with 1000, different local groups/ID in each client pc.

Have to add in /etc/exports the following line:

/srv/x_folder      192.168.0.0/24(rw,async,no_subtree_check,all_squash,anonuid=1000,anongid=1000)

REVIEW:
How you pretend to say that share a single folder on UBUNTU is EASY without permision problems ????

Dont make me laugh. Its hard to debug why a user cannot access the file that other user writed.

Conclusion: Its easy to understand why sharing with sambaGUI is the preferred user choice. Sharing with NFS take too much time.

Sharing should be so easy like plugin a pendrive, printer, ...

Best regards!

---

### Post by Wrapperband-0 on 2012-10-05
I agree - this is CRAZY not being a GUI and in system set-up. Please tell me it is and I missed it!!!

Also, I have found (as a newbie)  - NFS sharing isn't even in the software centre ! 

This is suicidal madness, I have spent hours trying to get the poorly supported samba working. Thanks for having the latest version not work at all, then stuff up your system, (when you go back to samba 3) as well.

---

### Post by bamdad.khan on 2012-10-05
> **Wrapperband-0 said:**
> I agree - this is CRAZY not being a GUI and in system set-up. Please tell me it is and I missed it!!!

Also, I have found (as a newbie)  - NFS sharing isn't even in the software centre ! 

This is suicidal madness, I have spent hours trying to get the poorly supported samba working. Thanks for having the latest version not work at all, then stuff up your system, (when you go back to samba 3) as well.

i agree. it should be integrated into system settings, along with a proper gui to configure upstart services.

anyway, don't be so hard on them: while i think canonical should focus a bit more on usability and less on interface design, there really aren't any proper tools nowadays for these kinds of tasks.

the best you can get is webmin, which is actually pretty nice, although a gtk interface would be more preferable.

---

### Post by LewisTM on 2012-10-05
I agree Webmin covers NFS pretty well. It doesn't have a centralized module for NFS. Exports are in Networking/NFS Exports and Mounts are in  System/Disks and Network Filesystems.

I think the reason Canonical is not developing NFS sharing tools is that it focuses on the user. Unlike Samba, NFS cannot be setup at the user level. It has to be both exported and mounted as superuser. Ubuntu in not well equipped in GUI system setups. Notice it doesn't even offer a way to manage disk mounts without installing additional (free) software.

To get a userlevel NFS, ideally one would have to code both an NFS usershare system and add NFS support to GVFS. The Nautilus plugin [NFS-LAN]("http://nfs-lan.sevka.info/blog/nfs-lanfornautilus3x") is available but uses autofs so it is less intuitive; I haven't tested it. For KDE (Dolphin, Krusader) there is an NFS kioslave.

Cheers!

---

### Post by oldos2er on 2012-10-05
Old thread closed.

---

