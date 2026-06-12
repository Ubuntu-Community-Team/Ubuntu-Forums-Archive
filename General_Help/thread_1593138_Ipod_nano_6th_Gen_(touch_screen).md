---
title: "Ipod nano 6th Gen (touch screen)"
date: 2010-10-11
forum: General Help
---

### Post by lowebb on 2010-10-11
Quite surprisingly there is nothing out there about support for the 6th generation nano (with touch screen).

I'm not a big fan of itunes and less of having to hook through VirtualBox to load music. RythmBox only seems to support up to 5th gen. 

Has anyone got this working natively in Ubuntu? Feel free to share a HOWTO

Thanks

---

### Post by dino99 on 2010-10-11
look at the latest posts: [http://ubuntuforums.org/showthread.php?t=833361](http://ubuntuforums.org/showthread.php?t=833361)

---

### Post by lowebb on 2010-10-11
> **dino99 said:**
> look at the latest posts: [http://ubuntuforums.org/showthread.php?t=833361](http://ubuntuforums.org/showthread.php?t=833361)

That links a thread

HOWTO: Use your iPhone or iPod Touch as a touchpad

????

---

### Post by lowebb on 2010-10-11
Excellent....

---

### Post by choman on 2010-11-23
@lowebb

Did you get your 6th Gen nano working with ubuntu?

Please share


NOTE:  Where I am at.  I can see the file system fine, rythmbox appears to put music there.  But the device doesn't know the tunes are there.  ideviceinfo returns the following error:

      usbmuxd_get_device_list: error opening   
      No device found, is it plugged in?

---

### Post by ahnise on 2010-12-06
same problem here . . Cant even get itunes working in vbox. Hope this gets supported soon. Silly me to buy ipod not supported by ubuntu.

---

### Post by ahnise on 2010-12-06
@lowebb. Did you get itunes working in vbox. Tried it with XP and Windows & Ultimate and no luck. Just freezes up. Only option for me is to reboot in dual boot Windows ..

---

### Post by ahnise on 2010-12-16
I got it working using media monkey under XP on virtual box.

---

### Post by mac9416 on 2010-12-25
I got a 6th generation touch Nano for Christmas, so I started looking for ways to use it with Ubuntu. Unfortunately, the folks who write libgpod [say]("http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTimPsMqVEr6Zh5-KtQAbwqATjc1G0dxdshD3ez2v%40mail.gmail.com&forum_name=gtkpod-devel"):

> For now, the nano6g uses the same hash for the music database as the
iphone4 and the ipod touch 4, which unfortunately means someone needs
to reverse engineer this hash before the nano6g can be fully
supported. And reverse engineering this is pretty hard :-/

Doesn't sound too hopeful. I'd suggest [donating]("http://sourceforge.net/project/project_donations.php?group_id=67873") a few dollars to the GTKPod project to support the effort.

---

### Post by zpzpzp on 2011-01-29
Are there any updates on how to use this ipod in Ubuntu?

Thanks.

---

### Post by formatBCE on 2011-03-18
Still no updates, as I see...
Interesting, how many people actually using virtual OS for this task? And why it is still stuck...

---

### Post by JohannDoe on 2011-03-19
> **mac9416 said:**
> I got a 6th generation touch Nano for Christmas, so I started looking for ways to use it with Ubuntu. Unfortunately, the folks who write libgpod [say]("http://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTimPsMqVEr6Zh5-KtQAbwqATjc1G0dxdshD3ez2v%40mail.gmail.com&forum_name=gtkpod-devel"):
[I]
For now, the nano6g uses the same hash for the music database as the
iphone4 and the ipod touch 4, which unfortunately means someone needs
to reverse engineer this hash before the nano6g can be fully
supported. And reverse engineering this is pretty hard :-/ 			 		[/I]


Doesn't sound too hopeful. I'd suggest [donating]("http://sourceforge.net/project/project_donations.php?group_id=67873") a few dollars to the GTKPod project to support the effort.

If its the same hash as the iphone4 and touch, has anybody tried iFuse ? Seems to be the thing for syncing touchs and iphones, or so I'm told. Haven't (yet) tried it myself - I'm still too much of a n00b to be going into uncharted territory and nothing I've seen so far talks about iFuse with nano6g, only touchs and iphones.

I concur with the libgpod folks in that it would seem to be a database issue rather than a connectivity issue -  best as I can tell, both Rhythmbox and Banshee ARE actually moving the songs to my nano6g except just not updating the database so it knows they're there. If I open the nano through gtkpod it tells me "extended attributes not shown". which tells me its seeing something but doesn't know how to handle it.

---

### Post by msenn on 2011-06-11
FYI:  Newest Ubuntu release (11.04) and Rhythmbox (0.13.3) and my iPod Nano 6th gen is working like a champ!

---

### Post by arealityfarbetween on 2011-06-30
For transfer of music to the device? I was v. hopeful when I saw your post but still a no go.

I can read the itunes db and copy music back to the pc (albeit with a metadata warning) but can't add any songs to the device-when attempting to write the change to the iPod database gtkpod shows an error about an "unsupported checksum", had the same problem with rhythmbox on 11.04 although the error message did not appear...

The 6th gen nano in question is using v1.1 of the iPod firmware. Anyone else had any luck with this?

---

### Post by wvu_ravens_fan on 2011-07-21
I have been using VBox with XP VM, instead of installing Itunes I have been using Media Monkey.  Works great.

Apple is more evil then Windows.

---

### Post by Brejcha on 2012-01-20
Just saw that the iPhone 4s and ipad 2 have been jailbroken. Will this possibly mean that the ipod nano 6g will get some love from Linux

---

### Post by fictivetoast on 2012-03-04
> **Brejcha said:**
> Just saw that the iPhone 4s and ipad 2 have been jailbroken. Will this possibly mean that the ipod nano 6g will get some love from Linux

I certainly hope so, I'm sick of dual booting just for the sake of loading music onto my nano 6g...

---

### Post by apochry on 2012-03-04
I am using the dev release of Clementine music player to manage the music on my iPod (nano, 3rd gen.). The stable release is not working for me. Not sure if it will work with 6th gen iPods,but you can give it a try.

Clementine's dev. repo:
```
ppa:me-davidsansome/clementine-dev
```

Hope this helps.

Regards,
Christo

---

### Post by 80aless on 2012-05-07
I sync my ipod with spotify

---

### Post by Robertsonv on 2012-05-28
> **apochry said:**
> I am using the dev release of Clementine music player to manage the music on my iPod (nano, 3rd gen.). The stable release is not working for me. Not sure if it will work with 6th gen iPods,but you can give it a try.


I can play files from my ipod nano 6th with clementine, 
but when i try to copy music to it it says:
" Unsupported checksum type"

---

