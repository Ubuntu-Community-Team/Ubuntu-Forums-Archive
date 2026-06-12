---
title: "syncing /home directories accross computers"
date: 2010-02-12
forum: General Help
---

### Post by anandamide on 2010-02-12
Hi

I was wondering if anyone could point me in the direction of any howtos around this. 

I have 3 computers:

Desktop - Dendrite - Ubuntu 9.10
Laptop - Axon - Ubuntu 9.10
Netbook - Synapse - Eeebuntu 9.10

All with their own home drives. My media (music, films, photos etc) is kept on a separate (Vista) partition on my Desktop with symlinks from my home directory on Dendrite.

Ideally, I'd have the /home directory synced across all 3 computers. I had been toying with the idea of a networked /home kept on an external HD plugged into synapse, but not sure how this would work out with Axon out of the reach of the network. I have dyndns set up and can access the home network over ssh, but obviously that's impractical (I assume) for a home drive.

Thoughts? Ideas? Pointers? I'm comfortable playing around with fstab, nfs and the terminal, but still very much a beginner.

---

### Post by bab1 on 2010-02-12
> **anandamide said:**
> Hi

I was wondering if anyone could point me in the direction of any howtos around this. 

I have 3 computers:

Desktop - Dendrite - Ubuntu 9.10
Laptop - Axon - Ubuntu 9.10
Netbook - Synapse - Eeebuntu 9.10

All with their own home drives. My media (music, films, photos etc) is kept on a separate (Vista) partition on my Desktop with symlinks from my home directory on Dendrite.

Ideally, I'd have the /home directory synced across all 3 computers. I had been toying with the idea of a networked /home kept on an external HD plugged into synapse, but not sure how this would work out with Axon out of the reach of the network. I have dyndns set up and can access the home network over ssh, but obviously that's impractical (I assume) for a home drive.

Thoughts? Ideas? Pointers? I'm comfortable playing around with fstab, nfs and the terminal, but still very much a beginner.

Think many to one.  Have one home dir (on Synapse) and use NFS to export a common home dir to the others.  You could ssh in to Synapse when away.

Is there a downside?  Sure, Synapse must be up 24/7 as it is the NFS server for all.  I would think about transferring this to the desktop if you don't want to leave a laptop on all the time.

---

### Post by anandamide on 2010-02-12
Thanks for the reply - that would be an ideal set up, my only issue would be transfer speeds over SSH (Synapse already acts as an alarm clock and sound server, so no issues with it always being on). Also, if I'm at my parents' house and log in on Axon, how will Axon know to

a) look somewhere else for /home (i.e. xyz.dyndns: rather than synapse:/home )

b) know to open up an SSH link on log on

Or would I have to work with a separate /home directory when away from... um, home?

wrt to setting it up within the LAN, I presumably just set up an NFS share on Synapse then change Axon and Dendrite's fstab file to point /home to Synapse:/home. How would this work with the encryption I have set up, or would it all be taken care of by the system checking the permissions and ownerships of the directory?

---

### Post by bab1 on 2010-02-12
> **anandamide said:**
> Thanks for the reply - that would be an ideal set up, my only issue would be transfer speeds over SSH (Synapse already acts as an alarm clock and sound server, so no issues with it always being on). Also, if I'm at my parents' house and log in on Axon, how will Axon know to

a) look somewhere else for /home (i.e. xyz.dyndns: rather than synapse:/home )

b) know to open up an SSH link on log on

Or would I have to work with a separate /home directory when away from... um, home?

wrt to setting it up within the LAN, I presumably just set up an NFS share on Synapse then change Axon and Dendrite's fstab file to point /home to Synapse:/home. How would this work with the encryption I have set up, or would it all be taken care of by the system checking the permissions and ownerships of the directory?

The overhead that NFS adds to your network (home) is negligible.  At one time I managed a 300 node Sun Solaris network with NFS/NIS spread over 4 buildings.  I could log in anywhere on that network and my home directory was always the same.

SSh'ing into a specific host on the network was the same as being locally logged in to that host.  SSH provides an encrypted connection and a few services.  Essentially you have to forget about where you are relative to the physical equipment.  The notion of *there (e.g where you are)* is not a factor.

The basic concept is NFS for a common directory and files.  This requires some form of network wide user management such as NIS. 

As an all Linux network you can use NFS to *export a common partition* containing the home directory to a spot in your file system.  Remembering back I believe on Solaris it was /export/home  My home directory was under that. 

More important to this setup is management of the users.  You could, if you are ***very careful***, replicate the users on each host.  This is more that just username and pass.  You would have to coordinate the UID and GID plus all group memberships on all three hosts.  Then permissions and file ownership will be consistent.  The alternative is the implementation of  a centralized user database.

As you can see, a centralized system becomes useful when there are numerous users.  Here we think one to many.  One user database for user management on many hosts.  Here we have two centralized systems available; NIS or LDAP.  

NIS is relatively easy to setup and uses text files for configuration.  On the other hand LDAP is more scalable to huge entities and flexible in configuration.  The trade off is in the complexity in setting LDAP up correctly.  LDAP is extremely difficult to setup from scratch.

If you do not want to create a dedicated LDAP server by adding or converting a host, then I would forget about LDAP.

In a nutshell what you want is doable with some work on your part.  The initial design of what you want is most important.  Describe it fully in a report before making any changes to your system.

See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://www.google.com/search?hl=en&ei=Svh1S9znI4meswPg88jLCA&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CA8QBSgA&q=nfs+linux&spell=1")for NFS.

See [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://www.google.com/search?q=NIS+Linux&btnG=Go!")for NIS

---

### Post by anandamide on 2010-02-13
Brilliant - thanks for taking the time to reply.

I'll get to work :-)

---

### Post by fragos on 2010-02-13
I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the server there must be an /etc/exports with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

This allows the Desktop to access the home folder of the laptop. Prior to Ubuntu 8.04 you need to run "sudo exportfs -rv" for the system to read /etc/exports. New versions do this for you at boot.

On the Desktop create a folder to mount to. In my case I placed that folder in my home folder.

On the Desktop side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

I run Unison to perform the synchronization between my machines. Rather than sync all of /home I've placed a folder on the Desktop where all of my work in progress and critical data files are stored. I've also used Unison with a memory stick for a "sneaker net" approach. You might also check out Ubuntu One which has free 2GB web storage and more for a price. I gotten it to work for my Desktop but still need to experiment to see my Laptop can sync with the same Ubuntu One account. The nice thing about Ubuntu One is that it's automatic and runs in the background.

---

### Post by anandamide on 2010-02-14
Hmm - is there a problem with having an encrypted home directory?

I can NFS with /usr easily, and even to /home, but /home/philip gives 

```
exportfs: Warning: /home/philip does not support NFS export.
```

Samba has no trouble with this?

---

