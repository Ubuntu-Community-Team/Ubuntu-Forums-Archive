---
title: "Windows/Samba Share on 9.10 Fails to Accept Guest Access"
date: 2009-11-23
forum: General Help
---

### Post by jamesisin on 2009-11-23
I have built a new (to me) 9.10 machine to act as a music server.  Previously I was using an SMB share to do so.  However, on this machine when I create a share and include guest access my 8.10 desktop and 9.10 laptop are not able to connect to the share ("Unable to mount location: Failed to mount Windows share").

I am able to access the share with guest mode turned off (and using an authenticated user account).

What gives?

---

### Post by jacobs444 on 2009-11-23
nevermind, im dumb

---

### Post by jamesisin on 2009-11-23
> **jacobs444 said:**
> nevermind, im dumb

Well, thanks for stopping by...

---

### Post by jamesisin on 2009-11-24
Anybody?

---

### Post by zachjg on 2009-11-25
I'm also having the exact same issue. It started out where I couldn't even see the computer listed on the network. This was solved by restarting samba (apparently there was an issue where the nmbd daemon didn't start properly). But now anytime I try to allow guest access to a share, I get the "Unable to mount location: Failed to mount Windows share" error. I was stuck at this point until I read your post about not allowing guest access and sure enough it works now, but I still would prefer setting up guest access.

I have used this machine as a file server with previous versions of Ubuntu with no issues. Any help or insight is appreciated.

---

### Post by jamesisin on 2009-11-25
Hopefully we'll get someone who has a clue, because I don't.

---

### Post by jamesisin on 2009-11-25
I have some new information which I think points me in a specific direction.  Hopefully, I am a little closer to a solution.

I am able to attach to the share from Windows machines (Vista and SBS 2003) which are domain connected machines.  I have a workgroup XP machine that is not able to connect ("\\server\share is not accessible.  You might not have permissions...").  Since Vista and 2003 are able to connect while XP fails, it doesn't seem to be a version issue.  However, because the domain machines succeed and the workgroup machine fails I suspect that Ubuntu 9.10 is marshaling against workgroup access (not very "guest" friendly, but workable).

So, how can I alter my share to include the domain information that 9.10 is expecting?

smb://192.svr.ip.adr/SHARENAME/

I tried smb://DOMAIN;192.svr.ip.adr/SHARENAME/ to no avail...

Alternatively (and preferably), how do I tell Ubu to allow guests who are also guests to my local domain?

---

### Post by jamesisin on 2009-11-28
Anybody?

---

### Post by ermo on 2009-11-28
One easy (!) way to check if you have access, is to connect to the share from the machine that hosts the share.

Also, it might be helpful to investigate the 'log level' directive that you can supply to your samba configuration file (man smb.conf, search for 'log level').

Start a terminal and issue the command:

```

smbclient //<yourserver>/<yourshare>
ls

```

Smbclient logs you on to the server and lets you browse the available files with the 'ls' command (smbclient works pretty much like an old school ftp command line client if that means anything to you). If you increase the log level, you should be able to dig through the samba log files in /var/log/<something> and hopefully catch the error message (if any) there.

In any case, it might be a good idea to try to read the fine documentation over at [http://samba.org](http://samba.org)

Cheers

---

### Post by jamesisin on 2009-11-28
What follows is inaccurate; see my next post in this thread.




Access to the share fails ("Failed to mount Windows share") from the server (to itself) with guest access enabled.

Just to recap, if I turn off guest access and supply proper (local) credentials I am able to access the share.

It is only a problem when attempting to access the share from a non-domain account/machine (identified as Workgroup).

I am able to access the share using guest access from both an XP and an SBS 2003 domain-connected machine.

I am not able to access the share from an XP workgroup machine nor my 8.10 machine (nor the 9.10 server itself).

---

### Post by jamesisin on 2009-11-29
My previous assessment was slightly off.  What is in fact happening is that the Windows domain machines are sending credentials to the server which happen to match the server's credentials (I used the same username and password when I built the machine).  My non-domain XP machine has a different username (so it is sending different credentials).  If I include a username when using "Connect to Server..." I am prompted for a password (and, if these credentials are good, I am granted access).

So, it would appear that currently Guest access isn't.  Even with Guest access turned on, Ubuntu/Samba is still expecting valid credentials.

---

### Post by jamesisin on 2009-11-29
More clues...

I created a share on a 9.10 laptop, but this I created in the Public folder of the user.  This share allows guest access.

So I went back to the server and created a share in a Public folder and that too is allowing guest access.

So I created a share on both of those machines on the Desktop.  These also allow guest access.

It is only the share on the RAID which is denying guest access.  I looked at the permissions and they seem to match (both of the others): user create and delete, group access files, and others access files.  I see no parameters in the share that I might be able to change.

Does this lead us anywhere?

---

### Post by jamesisin on 2009-11-29
Sure enough, when you eliminate the impossible whatever is left (however absurd) is the solution.

I had to change the permissions on the /media/[RAID] folder.  This is what was inhibiting access at the lower level of /media/[RAID]/[share].

Hope that is helpful to those who follow.

Now I have to reboot and check to see if those permissions are sticky...

---

### Post by jamesisin on 2009-11-29
Mmm... sticky good.

Thanks to all who tried to help with this one.  Ciao.

---

