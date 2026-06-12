---
title: "Nautilus crashes when network is cllicked."
date: 2010-01-30
forum: General Help
---

### Post by noelvh on 2010-01-30
Here is my issue. I am running 9.04.
I open the file manager (Nautilus) click the network to connect to my shares and the FM crashes.
out put from terminal
```
wncamp@ubuntu:~$ nautilus

(nautilus:4313): Gtk-WARNING **: Theme directory 32x32/emotexs of theme Aqua-Glade_PNG has no size field

** Message: Initializing gksu extension...
Initializing nautilus-open-terminal extension

(nautilus:4313): Gtk-WARNING **: Theme directory 32x32/emotexs of theme Aqua-Glade_PNG has no size field


** (nautilus:4313): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: unknown format for key 'public/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only

(nautilus:4313): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:4313): WARNING **: Got GFileInfo with NULL name in network:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:4313): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
wncamp@ubuntu:~$ clear

wncamp@ubuntu:~$ nautilus

(nautilus:4325): Gtk-WARNING **: Theme directory 32x32/emotexs of theme Aqua-Glade_PNG has no size field

** Message: Initializing gksu extension...
Initializing nautilus-open-terminal extension

(nautilus:4325): Gtk-WARNING **: Theme directory 32x32/emotexs of theme Aqua-Glade_PNG has no size field


** (nautilus:4325): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: unknown format for key 'public/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only

(nautilus:4325): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:4325): WARNING **: Got GFileInfo with NULL name in network:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:4325): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
wncamp@ubuntu:~$ 

```

I have researched this a bit and found it could be ubuntuone so I removed it, rebooted and no good.
I then read the terminal out put and looked at the gvfs backend reinstalled that. no good. 

Can some one help me out here?

Thanks in advance

Noel

---

### Post by noelvh on 2010-01-30
So far I have tried to reinstall samba, and the gvfs. I have found that the gvfs was a proble in the past. I did get some updates yesterday and not sure what was listed. I just clicked install. 

Noel

---

### Post by analogian on 2010-01-30
i have the same problem running jaunty 32 bit, only after upgrade yesterday that i seem to have problems- also nautilus crashes when i open the trash and doesn't seem to generate a .crash file

---

### Post by ipdeman on 2010-01-30
Same problem here. Also when computer is clicked. Running 64 bit 9.04. Started after updates yesterday.

---

### Post by analogian on 2010-01-30
this problem seems to be user based- no problems accessing trash/nautilus through another user account.... nautilus crashes and all desktop icons disappear after the following:
clicking on trash
selecting computer from nautilus browser
selecting network from nautilus browser

---

### Post by plastikkboy on 2010-01-30
i have the same problems with nautilus after friday's update on 9.04 x64. Nautilus segfault by clicking on Computer, Network and Samba shares.
I have gvfs and samba reinstalled but it don't work. Has anybody a solution?

---

### Post by JohnSearle on 2010-01-30
Same problem here. Running 9.04 32bit.

Just when I was about to back up my stuff and do a clean install to 9.10.

---

### Post by sipstar on 2010-01-31
Same problem here when trying to mount a ftp-share. After restarting Nautilus the share is still mounted but trying to access it crashed Nautilus again.

Same thing when trying to browse network.

---

### Post by hpis2cool on 2010-01-31
I have the exact same problem here! I think it started since yesterday's updates.

---

### Post by noelvh on 2010-01-31
What gets me is no one have offered and ideas. Don't get me wrong I understand that there might not be any one on the board who can help as it is the weekend. But it looks like a growing issue.

I have tried to reset my configs but deleting the .config folders, that did not help. Then I tried to log in as root but had the same issue. I have yet to create a new user but I really don't want a new userer on my system as I have only a small HD.

So if you are out there please help.

Noel

---

### Post by bpowell2005 on 2010-01-31
Exact same problem here...Nautilus crashes when Computer, Network, or Trash Can are clicked....running 64-bit 9.04; problem started today after running updates (hadn't updated in a couple of weeks).

Very frustrating, making my system unusable.

---

### Post by Ohrer on 2010-01-31
Same problem here, when I open network or trash, nautilus crashes and the desktop icons disappear. After that, if I run nautilus as root the desktop wallpaper changes to the default one. :confused:

---

### Post by plastikkboy on 2010-02-01
Has anybody solution?? I can't work now :(

---

### Post by elvisd on 2010-02-01
Same Problem here. Installed 9.04 updates and can't login anymore to windows or linux network shares.
```

Initializing nautilus-dropbox 0.6.1
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:16363): WARNING **: Unable to add monitor: Not supported
// ${1}
(nautilus:16363): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:16363): WARNING **: Got GFileInfo with NULL name in smb://user@server/e$/, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:16363): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```
on placeholder ${1} I have clicked the windows network share. I i select a linux network share the same thing happens.

Somebody knows how could we rollback to the situation before the update (downgrade).

---

### Post by plastikkboy on 2010-02-01
> **plastikkboy said:**
> Has anybody solution?? I can't work now :(

As temporary solution i have mount smb-shares with
```
sudo mount -t smbfs //computername/sharename /home/user/smbmount/sharename/
```

---

### Post by noelvh on 2010-02-01
> **plastikkboy said:**
> As temporary solution i have mount smb-shares with
```
sudo mount -t smbfs //computername/sharename /home/user/smbmount/sharename/
```

I got an error whit this mount. I am trying to mount an XP nsa drive and it is ntfs. DO you know how I can mount that one?

Thanks

Noel

---

### Post by noelvh on 2010-02-01
Never mind I had to install smbfs and add the user name and password.
So I got it.

Thanks

Noel

---

### Post by Polkan on 2010-02-01
The same problem.
Just try to downgrade glib packets, while issue isn't solved: 
$ sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
It helps me.

---

### Post by jdi2728 on 2010-02-01
Hi,

First post so be kind. I had the same problem nautilius crashed when i clicked computer. I rolled back smbclient and this downgraded samba-common and now it works again. Hope this helps.

---

### Post by hpis2cool on 2010-02-01
> **Polkan said:**
> The same problem.
Just try to downgrade glib packets, while issue isn't solved: 
$ sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
It helps me.

THANK YOU SOOOOOOOOOO MUCH!!!!!!!!!! I had tried to downgrade but I tried forcing the version to the previous one through Synaptic and it kept on telling me that it would have to remove a BUNCH of other applications for that.....AHHHHHHH IT WORKED!!!!!!!

Seriously, awesome. Now I'll just remember not to update that package.

---

### Post by noelvh on 2010-02-01
> **jdi2728 said:**
> Hi,

First post so be kind. I had the same problem nautilius crashed when i clicked computer. I rolled back smbclient and this downgraded samba-common and now it works again. Hope this helps.

Here is some kindness! How did you roll it back in as much as what was the command you used to do this please?

Noel.

---

### Post by jdi2728 on 2010-02-01
Hi,

This is how i did it.

1) synaptic package manager
2) in the top left of the window select file, go to history.
3) This will bring up a window of the dates of when you install upgrades etc
4) choose the date you upgraded
5) find smbclient
6) i then copied and pasted smbclient into the search bar and then selected package from top left of the window and used the force version option and selected the previous version of smbclient.
7) I then click apply 

Hope this helps

---

### Post by noelvh on 2010-02-01
> **jdi2728 said:**
> Hi,

This is how i did it.

1) synaptic package manager
2) in the top left of the window select file, go to history.
3) This will bring up a window of the dates of when you install upgrades etc
4) choose the date you upgraded
5) find smbclient
6) i then copied and pasted smbclient into the search bar and then selected package from top left of the window and used the force version option and selected the previous version of smbclient.
7) I then click apply 

Hope this helps

Great thanks.

Noel

---

### Post by Ohrer on 2010-02-01
> **Polkan said:**
> The same problem.
Just try to downgrade glib packets, while issue isn't solved: 
$ sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
It helps me.

when I do that, aptitude ask for deleting about 30 packages... is that normal?

---

### Post by plastikkboy on 2010-02-02
> **jdi2728 said:**
> Hi,

This is how i did it.

1) synaptic package manager
2) in the top left of the window select file, go to history.
3) This will bring up a window of the dates of when you install upgrades etc
4) choose the date you upgraded
5) find smbclient
6) i then copied and pasted smbclient into the search bar and then selected package from top left of the window and used the force version option and selected the previous version of smbclient.
7) I then click apply 

Hope this helps

:( I have downgrade smbclient, samba, samba-common and winbind. But problem still exist :(
Then i have downgrade glib packet with
```
$ sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
```
Also i have downgrade these packets
```
libsoup-gnome2.4-1 [2.28.1-2ubuntu1-ppa1~jaunty (now) -> 2.26.0-0ubuntu3
(jaunty-updates)]
libsoup2.4-1 [2.28.1-2ubuntu1-ppa1~jaunty (now) -> 2.26.0-0ubuntu3
(jaunty-updates)]

```
and delete these
```
exo-utils{u} libexo-0.3-0{u} libxfce4util4{u} libxfcegui4-4{u} 
  libxfconf-0-2{u} xfce4-panel{u} xfconf{u} 
```
Perfect! It works!! Then i have update samba. And it still work!! :)

---

### Post by raykroeker on 2010-02-02
My system also crashes whenever I click on "Computer" after the following updates:

bzr (2.0.3-1~bazaar1~jaunty) to 2.0.4-1~bazaar1~jaunty
bzr-doc (2.0.3-1~bazaar1~jaunty) to 2.0.4-1~bazaar1~jaunty
dhcp3-client (3.1.1-5ubuntu8.1) to 3.1.1-5ubuntu8.2
dhcp3-common (3.1.1-5ubuntu8.1) to 3.1.1-5ubuntu8.2
fuse-utils (2.7.4-1.1ubuntu4) to 2.7.4-1.1ubuntu4.0.9.04.1
libfuse2 (2.7.4-1.1ubuntu4) to 2.7.4-1.1ubuntu4.0.9.04.1
libglib2.0-0 (2.20.1-0ubuntu2.1) to 2.22.3-0ubuntu2-ppa2~jaunty
libglib2.0-data (2.20.1-0ubuntu2.1) to 2.22.3-0ubuntu2-ppa2~jaunty
libglib2.0-dev (2.20.1-0ubuntu2.1) to 2.22.3-0ubuntu2-ppa2~jaunty
libsmbclient (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3
libsoup-gnome2.4-1 (2.26.0-0ubuntu3) to 2.28.1-2ubuntu1-ppa1~jaunty
libsoup2.4-1 (2.26.0-0ubuntu3) to 2.28.1-2ubuntu1-ppa1~jaunty
libwbclient0 (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3
samba-common (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3
smbclient (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3
winbind (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3

I tend to follow this path 20-30 times a day to find files/resources on my computer/the network.

$ nautilus computer:///
Initializing nautilus-open-terminal extension
Initializing nautilus-dropbox 0.6.1

(nautilus:17310): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:17310): WARNING **: Got GFileInfo with NULL name in computer:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:17310): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

---

### Post by Kooster on 2010-02-03
COOOOOOOOLLLLLLL!!!!! That did the trick

---

### Post by noelvh on 2010-02-03
> **Polkan said:**
> The same problem.
Just try to downgrade glib packets, while issue isn't solved: 
$ sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
It helps me.

Well I have tried two of the two workarounds posted and yours worked well for me. The other was to roll back the smbclint and that did not work. 

I am not going to make this solved as it has not been, there have only been workarounds posted and I do want to thank those who have offered there help, even if some of the WOs did not work for every one.

Thanks

Noel

---

### Post by mathyou on 2010-02-04
Same problem on both my Jaunty machines. Also having problems with update manager...

---

### Post by Hammer89 on 2010-02-06
I'm having the same problem. Ubuntu 9.04, nautilus crashes any time I try to access anything network-related or if I try to access my trash folder.

Running:

```
sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
```

Worked for me. But this really isn't a good permanent solution...

---

### Post by blacklocist on 2010-02-07
This too worked for me!

```
sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
```

---

### Post by noelvh on 2010-02-08
Well its been over a week and there have not been any fixes other than some roll back to packages. I am hope full this might change soon. Any one else still having this issue? I have removed the glib's to an older version and have my libsmbclinet rolled back. It works but I have to now watch what I do when I update. I have set my update manager to poll me every 2 weeks, and I have to pick through the list before I can pull the trigger.

Well any way I am working fine, and this is not a rant (it better not be as this is still a great OS), just a poke to see if this is still out there.

Noel

---

### Post by robholmes on 2010-02-09
Any news on this? Has there been a bug report filed for this? This really needs to be fixed!

I love Ubuntu, but this bug has obviously slipped through the normally brilliant net.

---

### Post by kickwin on 2010-03-02
This worked for me too!

```
sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
```

---

### Post by 121Lazz on 2010-03-17
```
sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
```

working for me, too.

---

### Post by wyrless2002 on 2010-03-25
> **Polkan said:**
> The same problem.
Just try to downgrade glib packets, while issue isn't solved: 
$ sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
It helps me.

Thanks Polkan! This one fixed my problem.

---

### Post by 121Lazz on 2010-03-26
It would be nice to have a permanent solution...

---

### Post by Spike-X on 2010-04-10
```
sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
```

When I run this, I get the error message


```
sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1
```

I'm running Mint 8. What do I need to change to make this work for me? Every time I click on my desktop, Conky crashes, and it's driving me batty!

---

### Post by lidex on 2010-04-10
Try:
```
sudo apt-get install libglib2.0-0 libglib2.0-data
```

---

### Post by Spike-X on 2010-04-10
That gives me:

```
libglib2.0-0 is already the newest version.
libglib2.0-data is already the newest version.
```

Hrm...

---

### Post by jamal_khan on 2010-04-10
Last month I faced this problem . After an update nautilus crashed when clicking Computer , Trash , Network . I have tried by purge and reinstalling Nautilus 

```
$ sudo apt-get purge nautilus
$sudo apt-get install nautilus
```

After that one gave me a solution to remove whole ubuntu-desktop and reinstall it . I didn't checked it because my net connection was not enough to do so . You can try it ..

remove ubuntu desktop by 
```
$ sudo apt-get purge ubuntu-desktop
```
After that reinstalling it by 
```
$ sudo apt-get install ubuntu-desktop
```

---

### Post by lidex on 2010-04-11
> **Spike-X said:**
> That gives me:

```
libglib2.0-0 is already the newest version.
libglib2.0-data is already the newest version.
```

Hrm...

This was for nautilus crashing - conky a separate issue.

---

### Post by 121Lazz on 2010-04-30
Is there a way to fix this permanently?

---

### Post by lidex on 2010-04-30
> **121Lazz said:**
> Is there a way to fix this permanently?

Run nautilus from a terminal to see error message.

---

