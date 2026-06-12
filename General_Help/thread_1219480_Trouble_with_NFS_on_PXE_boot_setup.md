---
title: "Trouble with NFS on PXE boot setup"
date: 2009-07-21
forum: General Help
---

### Post by lumix on 2009-07-21
The kernel appears to start loading (I say "appears" because the pause key doesn't pause the screen), and then I get to a point where messages like

"Begin: Retrying nfs mount ..."

"Begin: Running /scripts/nfs-premount ..."

"Done."

"nfsmount: need a path"

show up repeatedly.  Then they end with:

"mount: mounting /dev on /root/dev failed: No such file or directory"

plus two more similar and finally:

"Target filesystem doesn't have /sbin/init."
"No init found. Try passing init=bootarg."

Then BusyBox.

The only departure from the HowTo is that instead of /nfsroot I have /storage/nfsroot exported, because I needed space for the client image and my 2nd drive mounted on /storage had it.  I did change references to /nfsroot to /storage/nfsroot though.

---

### Post by lumix on 2009-07-27
Any thoughts from anybody?

---

### Post by ComradeHaz on 2011-01-30
I am suffering from this issue having followed [this]("https://help.ubuntu.com/community/DisklessUbuntuHowto") vaguely, while also doing research elsewhere for anything that seemed different. I actually have a Debian server and trying to push out Ubuntu 10.10. I've now spent 14 hours trying to do this, so any help at all would be massively appreciated.

-Haz

Edit: I have filmed the console output now to catch what whizzes past and immediately before the errors thrown as described by lumix above, the following is outputted, the lines that look dubious to me, I have highlighted in red.
> Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...
[COLOR="Red"]mknod: invalid number '/srv/netboot/nfsroot'[/COLOR]
Begin: Running /scripts/nfs-top ...
[A bunch of stuff about my NIC I am pretty sure is unimportant including stating that it has registered udp, tcp and tcp backchannel transport modules, the link not being ready, then that it is and a display of the network info which is all correct]
[COLOR="Red"]rootserver: 10.0.0.1 rootpath:[/COLOR]
filename : pxelinux.0
Begin: Running /scripts/nfs-premount ...
Done.
nfsmount: need a path
_


---

### Post by sirtcp on 2011-11-24
i have been in the same situation and i finally manage to bypass this issue. 

it means that your NFS share parameters specified in pxelinux.cfg/<whatever> is wrong or the share is not accessable.

my problem was that i forgot to delete "$" sign from path and server name.

it was like 

append initrd=images/clonezilla/initrd.gz boot=live union=aufs netboot=nfs nfsroot=$10.X.X.2:$/exports/clone

change it to like this (notice the $ after nfsroot parameter)
append initrd=images/clonezilla/initrd.gz boot=live union=aufs netboot=nfs nfsroot=10.X.X.2:/exports/clone

now its working like a charm, i waisted my two days in building up PXE :(

i hope this help some one.

Thanks

MYK

---

### Post by deruberhanyok on 2012-10-19
I know this thread is nearly a year old, but I wanted to make this post as I was having problems similar to those listed here and just found the solution for my particular case - the solutions seem to be various as many different problems can cause similar errors.

My setup is a Windows Server 2008 R2 machine for DHCP, TFTP and NFS server. I'm trying to netboot the Ubuntu LiveCD image and I've tried both 10.04 (Lucid) and 12.04 (Precise).

My boot entries in the pxelinux.cfg/default file all seemed correct, and switching the order of them didn't seem to have any effect. One of the problems, I noticed, was that it doesn't seem able to find most of these files, or at least access them.

After trying every tutorial I could find, I went back to checking NFS settings on my server. Looking in the advanced properties for the share, I made sure I had "no server authentication" and "allow unmapped user access" checked. Under that, the "allow unmapped user UNIX access" option was checked.

On a whim, I changed this to the "allow anonymous access" option. I'm no longer getting these errors. This option may not work for everyone - I'm testing on a closed network - but it may be worth trying to see if it fixes your problem.

Of course, now I've run into a different problem, but it seems to be more NFS server settings I need to change.

So: if you're getting a similar error, check the permissions on your NFS share. All of the tutorials I've found assume a linux NFS server is being used, which I expect is why it is so hard to find information about these errors - following the tutorials would ensure the NFS server is configured correctly, and it doesn't help those of us with a Windows Server environment!

The following is a list of keywords and error messages that may help googlers find this post:

LiveCD PXEboot netboot live ubuntu precise lucix 12.04 10.04 "no init found try passing" "Unable to find a live filesystem on the network"

---

