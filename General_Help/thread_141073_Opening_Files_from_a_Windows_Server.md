---
title: "Opening Files from a Windows Server"
date: 2006-03-07
forum: General Help
---

### Post by ronmarley1 on 2006-03-07
Here's a good one...
I have a couple volumes from one of our Win2K3 file server mounted.  Previously, I could open files directly from the mounts.  Now, when I dbl. click on a file (for example, a Word document), I get the first error message below.  If I double click on an image (like a jpg), I get the second error message.  The stragne part is, if I COPY a file from the Win server to my laptop, I can open the file without any problems.  I was able to open files previously.  In the mean time, I loaded OOo 2.0.1 and a few other apps.  I did not notice the errors until today, and it's been a few days since I've tried to open files from the Win server.  I know I've made a few changes, but it's been a few days, and I'd hate to have to uninstall a bunch of stuff to get it to work again.  If anyone has ideas, that'd be great!

EDIT: Even stranger; I can open PDF, avi, mp3 and mpg files without problems.  Could it be something with OOo?

---

### Post by schilcha on 2006-03-07
Have you tried to actually *mount* the win-share, rather than use nautilus' "Connect to server". It seems that some apps cannot access remote files via the smb protocoll.

Please correct me, if my diagnosis was wrong, but the first screenshot seems to me just like that problem.

Good Luck!

---

### Post by siefkencp on 2006-03-07
I recently begain having a similar problem and thought it was realted to Dapper...

Attached is the screenshot..

Thanks for any thoughts--- :-|

---

### Post by ronmarley1 on 2006-03-07
[QUOTE=schilcha]Have you tried to actually *mount* the win-share, rather than use nautilus' "Connect to server". It seems that some apps cannot access remote files via the smb protocoll.

Please correct me, if my diagnosis was wrong, but the first screenshot seems to me just like that problem.

Good Luck![/QUOTE]

Hi schilcha,
Thanks for the reply.  I'm gonna try that tomorrow at work and see what happens.  I'll let you know...

---

### Post by pete on 2006-03-07
The apps can understand the smb protocol just fine.  The problem is that you have navigated to the share via Nautilus, but the apps in question don't understand how to get there because it's not mounted in the file system.

Either "mount -t smbfs //<server>/<sharename> /<path_to_mountpoint>" or adding an entry to /etc/fstab for the network share should clear this problem up for you.

---

### Post by jbennett on 2006-03-07
If I wanted to mount an windows share by adding an entry to /etc/fstab, what would the entry look like?

Thanks for any help.

---

### Post by pete on 2006-03-07
Try adding this line to the end of /etc/fstab:

//<servername>/<sharename>   /<path_to_mountpoint>   smbfs   username=<network_username>,password=<network_password>   0   0

Then run "sudo mount -a" to mount all the stuff in fstab.  If it doesn't work, it's possible that that the 2k3 box has smb signing turned on (that's the default in 2k3), in which case, try changing "smbfs" above to "cifs".

Mind you, I've been muddling my way through roughly this same problem for the last few days, so that might not be the best way to do it, but it got it working for me :)

---

### Post by siefkencp on 2006-03-08
So is my problem un-related?

---

### Post by schilcha on 2006-03-08
[QUOTE=siefkencp]So is my problem un-related?[/QUOTE]
What did you do whe you got the error-message shown in your previous post?

---

### Post by siefkencp on 2006-03-08
[QUOTE=schilcha]What did you do whe you got the error-message shown in your previous post?[/QUOTE]

I simply tried to connect to a server through the gnome.... i tried browsing the network and get a similar error. I was looking for the SMB server install (in synaptic) but I haven't found it yet (so at least I can share files with ease).

---

### Post by schilcha on 2006-03-08
siefkencp!

The only way for me to produce that error message was to add a type into the protocoll-spec (insead of smb://server/share, I used smob://server/share). I don't really have a clue, why nautilus seems to be unaware of the smb-protocol your situation. 

Have a look at the samba-related packages you've installed (search for "samba" in the package-*names* -- otherwise you'll get tons of results). On my system, I've only installed samba-common, which is enough to connect to windows- or other samba-servers. 

If you want to share your data with other windows-machines, you'll probably need the package "samba". There is a gui to configure shared directories: System -> Administration -> Shared Folders. When I open it, I'm asked how I want to share folders (samba/nfs). Choose samba (or nfs, if you prefer) and all required packages will be installed.

---

### Post by ronmarley1 on 2006-03-08
Hi Everybody,
Thanks for the replies.  Unfortunately, I can't even mount the Windows share.  I followed the instructions at the Wiki ([http://www.ubuntuguide.org/#mountunmountnetworkfolders](http://www.ubuntuguide.org/#mountunmountnetworkfolders)) and entered this into the terminal: 
```
sudo mkdir /media/siriushome
```
This created the folder siriushome in the media folder.
I then entered  ```
sudo mount //10.1.0.10/Home/rgoodwin /media/siriushome/ -o username=rgoodwin,password=mypassword
```
into the terminal and got
```
10822: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
```
The server I want to connect to is called "sirius" and th IP address is 10.1.0.10.  The folder I want to connect to is /Home/rgoodwin.  This is on a Win2K Server box.  Thanks in advance for any suggestions!

---

### Post by schilcha on 2006-03-08
[QUOTE=ronmarley1]
The server I want to connect to is called "sirius" and th IP address is 10.1.0.10.  The folder I want to connect to is /Home/rgoodwin.[/QUOTE]

(smb)mount does not expect the remote path of the shared directory, but rather the share-name. I'm not really familiar with windows, but for printers, there's an option that's called something like "Share printer as...". The same thing exists for directories. That's the name you have to use in your mount-command instead of "/Home/rgoodwin".

Unfortunately, windows-people love to use spaces in names. In this case you'll probably need to prepend each space with a backslash.

---

### Post by ronmarley1 on 2006-03-08
[QUOTE=schilcha](smb)mount does not expect the remote path of the shared directory, but rather the share-name. I'm not really familiar with windows, but for printers, there's an option that's called something like "Share printer as...". The same thing exists for directories. That's the name you have to use in your mount-command instead of "/Home/rgoodwin".

Unfortunately, windows-people love to use spaces in names. In this case you'll probably need to prepend each space with a backslash.[/QUOTE]

Hi schilcha,
Thanks for your numerous replies.  I tried just connecting to the share name "Home" and that does not work either.  At this point, I'll just copy files from the Nautilus-Connect to Server icon to my laptop, edit the files, and then copy them back.  I just can't get mount to work.  Oh well, I'm not gonna play anymore.

---

### Post by pete on 2006-03-08
On the Windows side, you'd need to go to to the Sharing tab in the Properties for the rgoodwin folder you want to share, which will allow you to name the share whatever you want.  

I'd recommend something w/out spaces, so as to avoid the problem that schilcha brought up.

---

### Post by siefkencp on 2006-03-08
This could be a Dapper problem... I made no changes to the packages installed when the problem started but since then I have added a few... both from universe and Ubuntu... I may need to consolidate or perhaps some how I have a dependent related issue...

Either way, no problem I can still Xfer files samba just seems to be dead...

---

### Post by ronmarley1 on 2006-03-08
Hey now!
I got it working.  Here's what I had to enter in the terminal
```
sudo mount //10.1.0.10/home -t cifs /media/Home_on_Sirius -o username=rgoodwin,password=mypassword
```
The key was the *-t cifs*. 
Thanks so much EVERYBODY!
Woo hoo!

---

### Post by ronmarley1 on 2006-03-08
In a related note, I created this post on editing fstab and having the mounts at boot.
[http://www.ubuntuforums.org/showthread.php?t=141496](http://www.ubuntuforums.org/showthread.php?t=141496)

---

