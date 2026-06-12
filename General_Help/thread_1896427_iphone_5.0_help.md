---
title: "iphone 5.0 help"
date: 2011-12-16
forum: General Help
---

### Post by danielahl137 on 2011-12-16
i have an iphone with ios 5 that wouldnt mount so i did some code in terminal an now it mounts. now i need help adding music. i have an ipod with 4.3 an it worked fine with that. so im guess my phone wont work due to 5.0, if anyone knows how to fix this let me know, i am using banshee.

---

### Post by roguejedi on 2011-12-17
if anyone has any advise, i'd appretiate it too. old ipod syncs just fine with rhythmbox. ipad just upgraded to ios5, not so lucky.

---

### Post by bshosey on 2011-12-20
Wile iphone is pluged in run these commands

sudo apt-get install libimobiledevice-utils

idevicepair unpair && idevicepair pair

---

### Post by txducker on 2011-12-22
So is there a confirmation that this works for adding music to the iPhone 4s?
I am able to mount and copy files to my iPhone 4s, but the phone does not add the mp3 files to its music database and the songs are not visible in the music application.
Banshee also does not recognize the phone.

---

### Post by rorschachwalter on 2012-02-02
Syncing and transferring is not currently supported for iOS 5.

Even non-oss apps such as MediaMonkey are having to resort to using iTunes' own libraries to manage iOS 5 devices.

Whatever you read online, do NOT listen to folks who tell you that syncing works. I've spoken to the developers, and they insist that iOS 5 is not supported. I've even shown them comments from people claiming that they can sync with iOS 5. Those people are likely confused (perhaps they're not running iOS 5?), or if it does work, it *shouldn't* work.

So, for now, wait until libgpod is updated to work with the new iOS 5.

EDIT: Most likely, Rhythmbox (and other players) will appear to be transferring music over to the device, but the files will never show up on the device. This is because libgpod is currently not able to update the device database properly. If you look on the device's filesystem, you'll see that the songs are actually copied over, but again, the database never gets updated, so those files are not accessible and do not appear on the device.

---

