---
title: "Could not display &quot;network:///&quot;. Nautilus cannot handle &quot;network&quot; locations."
date: 2009-09-29
forum: General Help
---

### Post by millstone on 2009-09-29
Hello, I was about to transfer some files to another computer on my home network, however it required me to go through root nautilus fileviewer ```
gksudo nautilus
``` because of permission reasons as always.It's worked in the past because I was on 8.04, Now I'm on 9.04 and I get this error when trying to access the local home network. 

Could not display "network:///". Nautilus cannot handle "network" locations.

Also, when I try to type in the SMB address of a local computer on my home network I receive this error:

Example: I type in smb://192.168.1.102
Could not find "/home/(USERNAME)/smb:/192.168.1.102".
Please check the spelling and try again.

That is insane, I did not specify it to my home folder. So I went up to "/" directory and received the same error. 

I have searched through google and came up with similar problems but no answers. Is their any one who knows of a way to get around this?
Any help much appreciated. :)

EDIT: "libgnomevfs2-extra" did not work, like other forums stated that it would.
EDIT: I didn't have    "smbfs" installed. I'm downloading it now to see if it fixes it.
EDIT: installing smbfs didn't work.

---

### Post by Commander_Keen on 2009-09-29
Question.
  What kind of files are you xfering from 1 pc to the other, if you need to use gksudo nautilus?
  Why can't you just use the normal windows exlorer thingy to transfer data from 1 pc to 2 pc?

---

### Post by grturner on 2009-09-29
i've always preferred to add a line in /etc/fstab for mounting the specific samba share to a local directory. then all you have to do is sudo mount that directory and then you can treat it as a local directory and copy paste to it.

---

### Post by millstone on 2009-09-29
commander_keen: Because sometimes I run into permissions errors.
grturner: Thanks, I will do that.

---

### Post by doccali on 2009-10-31
installing gvfs-backends fixed it for me

---

### Post by Derpderp on 2009-11-26
I have a _fresh_ install of 9.10 and this problem still persists. None of the suggestions in this thread have proven useful.

---

### Post by tomwaters on 2010-01-08
> **doccali said:**
> installing gvfs-backends fixed it for me

OUTSTANDING!

That sure fixed it for me too! I am running the server version and manually installed the gui btw.

I also tried....
mv /usr/local /usr/local.old
mkdir /usr/local
and some other things on the web, but this was the missing piece.:D

---

### Post by KillerKellerjr on 2010-01-14
installing gvfs-backends fixed it for me too.  If you have this issue just do the following:

```
sudo apt-get install gvfs-backends
```

---

### Post by blimbo on 2010-01-24
I have this problem on 9.04, although a few weeks back everything was fine. gvfs-backends is already installed, I tried re-installing it but no joy :-(

---

### Post by blimbo on 2010-01-26
Ok I fixed this, using synaptic I completely removed gvfs (and therefore gvfs-backends, nautilus, ubuntu-desktop and some other stuff) before reinstalling it all. Worked after that :)

---

### Post by dentarthurdent on 2010-03-20
> **KillerKellerjr said:**
> installing gvfs-backends fixed it for me too.  If you have this issue just do the following:

```
sudo apt-get install gvfs-backends
```

awesome, this totally fixed the problem for me since upgrading to 10.04, thanks!

---

### Post by Nikusha on 2010-03-24
installing gvfs-backends also fixes for lucid!

---

### Post by artships on 2010-04-10
I have a 32bit karmic install.  Network:/// and sftp:/// don't work.  Removing gvfs, including gvfs-backends, and reinstalling didn't help.  Removing nautilus and re-installing didn't help, either.  It's just a couple of weeks until Lucid.  I can wait.

---

### Post by dcstar on 2010-04-10
> **artships said:**
> I have a 32bit karmic install.  Network:/// and sftp:/// don't work.  Removing gvfs, including gvfs-backends, and reinstalling didn't help.  Removing nautilus and re-installing didn't help, either.  It's just a couple of weeks until Lucid.  I can wait.

Use this launcher command:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

### Post by vishnujyothi on 2010-05-18
> **KillerKellerjr said:**
> installing gvfs-backends fixed it for me too.  If you have this issue just do the following:

```
sudo apt-get install gvfs-backends
```

Yes! It worked for Me also..Thanks dude...U rock

Its for u ::popcorn:

:guitar:

---

### Post by sreeramanathan on 2010-07-17
thanks dcstar. the launcher command does the trick !!!

---

### Post by Stephen Shellard on 2010-08-07
Just to update this and say that the solution worked for me within Lucid Lynx.

---

### Post by cpare on 2010-09-03
Thanks for this post - It also resolved my problem!
```
sudo apt-get install gvfs-backends
```

---

### Post by Ibertech on 2010-09-08
Just to let you know i had this problem and installing gvfs-backends sorted things out for me, many thanks

---

### Post by RichardUK on 2010-10-12
> **doccali said:**
> installing gvfs-backends fixed it for me

Sorry to necro an old thread but just wanted to say thanks. :) I 'broke' nautilus and your tip got it working again. Ta. :)

This was on 10.4 and I uninstalled the wrong thing, noob error on my part. :( Working again, thanks. :P

---

### Post by clancyhood on 2010-11-06
Woohoo I typed in apt-get install gvfs-backends and married a supermodel.  Oh and Nautilus works now too! thanks :)

---

### Post by pavelchjen on 2010-11-30
I am on Ubuntu 10.10 Maverick 32bit.
Had same issue. Reinstall of gvfs and gvfs-backends did not help.
Fixed it by compiling from original source gvfs package.
Now SSH smb:// and network:/// are works fine from nautilus.

---

### Post by juicyoner on 2011-02-02
sudo apt-get install samba" fixed it for me

---

### Post by islandBilly on 2011-02-04
> **juicyoner said:**
> sudo apt-get install samba" fixed it for me

Ok, I don't want to be a curmugeon, but my network ting was working fine in nautilus, until today! This is ubuntu 10.10 - so what happened? There was a system update today that I installed, but I don't think it involved nautilus. How'd it get broke? I guess I can do some of those installs to fix it, but it makes me mad to think it was working before...

In my case, I used synaptic to install samba, which didn't help, and then installed gvfs-backend, which did. It seems to be fine now. Maybe it takes both...

---

### Post by clockworkpc on 2011-03-15
Did the same.  Worked for me :)

---

### Post by herbie643 on 2011-05-27
I know it's over a year later but,  you guys are great.   Fixed the problem for so fast and easy.. I got a bit overzealous with removing stuff.

---

### Post by darren123web on 2011-05-31
Moved to own post

---

### Post by darren123web on 2011-05-31
Moved to own post

---

### Post by doriandeluca on 2011-10-03
> **KillerKellerjr said:**
> installing gvfs-backends fixed it for me too. If you have this issue just do the following:
 
```
sudo apt-get install gvfs-backends
```
 
This resolved the issue for me, as well.  Version 10.04. 
 
Thanks much!

---

### Post by kbrowne1 on 2011-11-24
Me too! Thanks.

---

### Post by Bazon on 2011-11-24
this can also happen when your DNS replaces 404 by search pages, many commercial Providers do so. 
you can either switch this off by your Provider or you can use another DNS like Googles 8.8.8.8

---

### Post by compubomb on 2011-12-24
> **Bazon said:**
> this can also happen when your DNS replaces 404 by search pages, many commercial Providers do so. 
you can either switch this off by your Provider or you can use another DNS like Googles 8.8.8.8

dude, you totally rock my world. This fixed all my smb issues in ubuntu. i hate timewarner for this. damn them. They are just greedy so they want to redirect all your dns traffic to their recommended websites. ^_^

---

### Post by tk0 on 2012-01-03
> **compubomb said:**
> dude, you totally rock my world. This fixed all my smb issues in ubuntu. i hate timewarner for this. damn them. They are just greedy so they want to redirect all your dns traffic to their recommended websites. ^_^

how did you do that, im on the same crappy isp...

---

### Post by AnoPoli on 2012-07-28
> **tk0 said:**
> how did you do that, im on the same crappy isp...

Change your DNS manually (instead of DHCP) to one (OR MORE) of those:
208.67.220.220 (OpenDNS)
208.67.222.222 (OpenDNS)
8.8.8.8 (Google DNS)
8.8.4.4 (Google DNS)
You may change it on your router (web interface...)
or through network manager.

---

### Post by Pronker on 2012-08-22
> **doccali said:**
> installing gvfs-backends fixed it for me

Worked for me as well even (on Arch).

---

