---
title: "&quot;Unable to mount location, Failed to retrieve share list from server&quot; Update caused?"
date: 2011-07-04
forum: General Help
---

### Post by ubuntu1sttimer on 2011-07-04
This is a common problem but with a new twist. Have not found anything about it on the forums.

I have had a Dlink 323 network file server for some time. After first getting it going, it has worked fine on both my Ubuntu computers and my Windows machines including a dual boot Ubuntu machine / Vista box. Recently, a problem has appeared that started at about the same time.  The Ubuntu machines give me the "Unable to mount location, Failed to retrieve share list from server" error message. The Windows machines still work fine. 

This message can be caused by a number of problems. I suspect that this time was caused by a update. The linux machines are 11.04 and 10.10. Wonder if anyone has run across this problem connected to an update and if so, what the fix was?  Otherwise, any ideas where I might start?

---

### Post by ubuntu1sttimer on 2011-07-09
Has anyone else had this problem and was a fix found?

As I have multiple computers and only Ubuntu machines doing this, there must be others.

---

### Post by kidknapp on 2011-07-14
I recently updated from 10.10 to 11.04 and am having a similar issue accessing a set of shared folders on my PC from one of my laptops. I get the same message. I had received this message before and could usually restart one or both of the computers and it would work fine. Its not doing me any good currently....:(

---

### Post by kidknapp on 2011-07-14
Are you still in Indiana? I am in B-town.

I guess I'll see if reinstalling samba helps....

---

### Post by ubuntu1sttimer on 2011-07-16
Sorry about the delay in replying. I have not found a solution. Compared to Windows, the way that Linux does access to remote drives and files via Samba is rather poor. I have had problems with it for years and have seen many others also fighting it. It is one of the reasons that I keep Windows machines available. I would like to do video editing with Linux but the files are kept on the file server. With the Linux problem, that limits relialable video editing to Windows.  

From the lack of replies to this thread, it appears that there are not many around that have worked with Ubuntu file sharring enough to be able to help us.  

Guess I will just keep doing my editing where I am.

---

### Post by Morbius1 on 2011-07-16
That error message is most likely not a samba problem but a network problem. Name services is the culprit I suspect. There's an easy way to determine if the problem is Samba though. Don't browse to the server, ask for it by ip address:
```
nautilus smb://192.168.0.100
```Change 192.168.0.100 to the ip address of the NAS device. If you connect then the Samba internals are working as it should.

---

### Post by ubuntu1sttimer on 2011-07-16
Thanks Morbius1, had not heard about that check. Tried it and it worked. Thus, I am able to eliminate Samba from the list of things that could be the problem.  

I use fixed IP addresses. The fixed address has not changed since is was working.

Would you happen to know how Ubuntu handles fixed IP's as related to file sharring? Is there a way to establish that fixed IP as a available shared drive and a way to establish a link to the drive so that will be available if the file storage drive is running. Also need have it appear after the server is started while Ubuntu is already up?  I don't usually leave it running unless I need to use it.

In the past it was there if it was running and not if it was not. Much like Windows. Made it very handy.

---

### Post by Morbius1 on 2011-07-17
The use of fixed ip address greatly simplifies your life. Here's a couple of options:

[1] Create a bookmark in Nautilus:

Once you do the "smb://192.168.0.100" thing in nautilus just select Bookmarks > Add Bookmark. This will create a link to the remote share on the left side panel of Nautilus much like a "mapped drive" does in Windows. You can even rename it at that point. You need to select that link to actually mount it though after a reboot.

[2] Use Gigolo to automount the remote share at login:

Take a look at this mini-howto: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

But instead of this section:
> Then you browse to the share using the Network Tab on gigolo
Then you bookmark the share by right clicking the share icon and select **"Create Bookmark"**
When you bookmark it select the **"Auto-connect"** optionDon't browse to the share. Go to Actions > Connect:

Service Type: Windows Share
Server: 192.168.0.100
Share: whatever-the-share-name-is

Then select Connect. Then you can follow the rest of the How to by creating a bookmark and then selecting auto-connect.

Gigolo will start probing the lan at login and wait for the remote share to be available before it mounts.

---

