---
title: "Two-way sync between HTPC and windows laptop"
date: 2011-01-28
forum: General Help
---

### Post by el_Paraguayo on 2011-01-28
Not sure if this is the right forum for this question so Mods, please feel free to move as appropriate.
 
I am building an HTPC based on Mythbuntu and will also have a laptop running Windows.
 
I need some software that will provide two-way syncing between these machines:
 
**1) Sync folders from HTPC to the laptop**
 
As the laptop is new, all the media content I want to have on the laptop (music and photos) will be on the HTPC.
 
**2) Backing up content from laptop to HTPC**
 
New content (purchased music and photos) is likely to be added on the laptop initially so I'd therefore like to sync (instantly/automatically if possible) this back to the HTPC to make it available there as well.
 
Does anyone know of any good software to do this?
 
I'd originally been thinking of DropBox but, as I understand it, you have to use a DropBox folder however, on the HTPC, music and photos will be on different drives and it seems that putting symlinks inside the DropBox folder is not recommended.
 
[This post]("http://ubuntuforums.org/showthread.php?t=1675409") also talks about using Ubuntu One. I think there's a Windows beta version available but does this sync between machines on a local network as I thought it was a cloud storage solution and I'm not looking to upload any content to the internet at this stage.
 
Any comments/questions appreciated.

---

### Post by prshah on 2011-01-28
> **el_Paraguayo said:**
> 
**1) Sync folders from HTPC to the laptop**
**2) Backing up content from laptop to HTPC**


The best way to do this would be to use rsync. However, rsync (especially if you want to run it over the Internet) is a little technical. What is your tech comfort level? Accordingly I can post suitable examples.

if you cannot wait and are comfortable with Linux, please see the manual page for rsync```
man rsync
```

---

### Post by el_Paraguayo on 2011-01-28
Thanks prshah.
 
I'm still fairly new to Linux (just one old machine running mythbuntu) but I'm very keen to learn stuff and I'm not put off by terminal stuff.
 
Any examples you've got would be great.
 
I assume rsync has an equivalent client that will run on the windows laptop?

---

### Post by jhayes on 2011-01-28
is the htpc running some flavor of linux?
if yes, is it running an ssh server?
and is the lappy running windows?
assuming all 3 are yes, start here. 
[http://fak3r.com/2006/08/10/howto-passwordless-ssh-logins/](http://fak3r.com/2006/08/10/howto-passwordless-ssh-logins/)
easy password-less ssh login. 
then setup the rsync server (may be optional, i use it ..)
[http://a1979shakedown.wordpress.com/2009/01/19/set-up-an-rsync-server-in-ubuntu-for-file-syncing-between-machines/](http://a1979shakedown.wordpress.com/2009/01/19/set-up-an-rsync-server-in-ubuntu-for-file-syncing-between-machines/)
then install cygwin on windows lappy. (if the laptop is linux, this is skipped (obviously) [http://www.cygwin.com/](http://www.cygwin.com/)  
then look over here 
[http://www.thegeekstuff.com/2010/09/rsync-command-examples/](http://www.thegeekstuff.com/2010/09/rsync-command-examples/)
that should get you going. if you need to do it over the internet, look up dyndns, get an account set up with them. not to much more work  :P

---

### Post by el_Paraguayo on 2011-02-02
Sorry for the slow reply - have been away for a few days.
 
All your assumptions were correct (HTPC = linux, SSH server = yes, laptop = windows).
 
Thanks very much for the links - rsync looks like it should do exactly what I need.

---

### Post by drewsus on 2011-02-02
[www.dropbox.com](www.dropbox.com)

I dont know exactly what you want to backup or how much, but I love this program

---

### Post by stalinvlad on 2011-02-03
Is there anyway to use samba on the myth box and oh robocopy or xcopy or what ever is in win 7 and slurp it across
Also as it will all be on a home network (assume 192.168.x.x address) is there any real need for ssh?
I mean windows has a telnet client built in

---

### Post by el_Paraguayo on 2011-02-04
The initial transfer of data from the HTPC to the laptop can probably be done using a Samba share (agree, there's probably no need for SSH at that stage).
 
There are then two probably scenarios to handle:
 
1) Media added to HTPC directly then needs to be synced onto laptop 
2) Media added to laptop needs to be synced back to HTPC.
 
The problem with 1 is that the laptop may or not be switched on at the time therefore when I switch on the laptop I'd like to be able to pull across any new media since the last sync.
 
2 should, in my opinion, be easier as the HTPC should be switched on. What I'm after then is a "watch folder" type system where any new media added to the laptop automatically backs up to the HTPC. (Ideally I'd like XBMC to refresh its library when new media is synced but that's for later...)

---

### Post by prshah on 2011-02-04
> **el_Paraguayo said:**
> The initial transfer of data from the HTPC to the laptop can probably be done using a Samba share (agree, there's probably no need for SSH at that stage).

1) Media added to HTPC directly then needs to be synced onto laptop 
2) Media added to laptop needs to be synced back to HTPC.
 
The problem with 1 is that the laptop may or not be switched on at the time therefore when I switch on the laptop I'd like to be able to pull across any new media since the last sync.
 
2 should, in my opinion, be easier as the HTPC should be switched on. What I'm after then is a "watch folder" type system where any new media added to the laptop automatically backs up to the HTPC. (Ideally I'd like XBMC to refresh its library when new media is synced but that's for later...)

Using rsync over Samba is slightly problematic. This is because of the way rsync works. rsync tries to transfer only the changed "bits/parts" of the files being synced, rather than the entire file itself (unless of course, the file does not exist on target). As a result, it sends a lot of little pieces of data over the network. Samba/SMB is very bad at handling a lot of small data pieces, and you will find network performance is impacted. SSH, while also being secure (as a bonus) does not have this issue.

rsync is very rapid because of this behaviour of sending only changed data.

[s]rsync will perform a two-way sync, so new data either on the laptop and/or the HTPC will be synced to the target device from the source device. If there is a conflict, the more recent file will be given preference (can be over-ridden).[/s] Sorry for this, rsync is unidirectional (backup/archival/mirroring); for bi-directional syncing, Unison is suggested.

The sync can be triggered either from the laptop or from the HTPC. If either device is not found, rsync will (silently, configurable) fail, without any ill-effects.

Please post back if you need more information.

---

### Post by el_Paraguayo on 2011-02-04
Thanks for the explanation. That makes sense.
 
As I'm trying to find a way of making this as easy as possible i.e. so if my wife downloads music on her own then it backs up without her having to do anything.
 
So I think my setup will be like this:
HTPC: rsync server
Windows laptop: client (looks like Deltacopy running as a service may work as it uses the rsync protocol - but don't know if the client runs as a service or whether it's just the server).
 
Unless anyone thinks the above won't work, let's leave it here and I'll report back once it's up and running.

---

### Post by prshah on 2011-02-05
> **el_Paraguayo said:**
>  
As I'm trying to find a way of making this as easy as possible i.e. so if my wife downloads music on her own then it backs up without her having to do anything.
 
So I think my setup will be like this:
HTPC: rsync server
Windows laptop: client (looks like Deltacopy running as a service may work as it uses the rsync protocol - but don't know if the client runs as a service or whether it's just the server).
 

OK a small correction with my eariler post; rsync is a backup/mirroring tool, it does not perform a two-way sync. To perform a two way sync with rsync, you have to run it twice, once from (eg) rsync server to client, and the second time from rsync client to server.

A true sync tool is unison, and is available in the repos, however, I have no experience with this tool. Maybe you could look into it.

---

