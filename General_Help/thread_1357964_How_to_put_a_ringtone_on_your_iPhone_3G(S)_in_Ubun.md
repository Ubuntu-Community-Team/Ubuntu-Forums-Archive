---
title: "How to put a ringtone on your iPhone 3G(S) in Ubuntu"
date: 2009-12-17
forum: General Help
---

### Post by patrickballeux on 2009-12-17
Hi,

I found a way in Ubuntu (9.10) to put ringtones on my iPhone 3GS... It's a bit complex to do it manually, but it's possible

1 - Mount your iPhone as a regular USB media storage (See [http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html"))

2 - Once your iPhone is mounted, get any MP3 and transcode it into mp4 format. Put the extention as .m4r

Using gstreamer from the command line:

> gst-launch filesrc location=test.mp3 ! decodebin ! audioconvert ! faac ! filesink location=test.m4r


Take a note that Gstreamer will give you the length in nanosec...

3 - Locate the file Ringtones.plist
4 - Make a backup of Ringtones.plist just in case...
5 - Edit the file using any text editor
6 - Open /media/iphone/iTines_Control/iTunes/Ringtones.plist
7 - Add this block for your mp3 file:

> <key>TEST.m4r</key>
<dict>
<key>GUID</key><string>07D44991A45EA9F3</string>
<key>Name</key><string>Test</string>
<key>Total Time</key><integer>118000</integer>
</dict>


Note that "Total Time" is the lenght in milliseconds of your mp3. Also, you will have to generate a randon GUID (Put any numbers you want)...

8 - Copy your mp3 renamed as TEST.m4r in the folder: /media/iphone/iTines_Control/Ringtones


And there you have a new custom ringtone for your iPhone. You do not need to jailbreak your iPhone using the tools mentionned in the webpage. But if it is, simply put the files using the SSH server if you want.

As I said, this is a bit geekie, but it works. I will have to think about making that automated using a script or an application.

---

### Post by grammarian on 2010-06-05
Hi,

I've been trying to follow your instructions but have not had much luck. Exactly where do I insert the code? My current Ringtones.plist file looks like this:

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>Ringtones</key>
	<dict>
	</dict>
</dict>
</plist>

```

Your help would be greatly appreciated.

Thanks

---

### Post by patrickballeux on 2010-07-25
Darn, seems that with the iOS4 upgrade, it does not work anymore,,,

---

### Post by Ben Leedham on 2010-07-26
I have done it on IOS4 upgrade on a 3GS using this guide.

[http://everydaylht.com/howtos/desktop/create-ringtones-for-your-iphone-using-linux/](http://everydaylht.com/howtos/desktop/create-ringtones-for-your-iphone-using-linux/)

You have to make sure that the milliseconds are correct, and have to restart the phone to pick it up but it works a treat. The guide is good.

---

### Post by patrickballeux on 2010-12-19
> **Ben Leedham said:**
> I have done it on IOS4 upgrade on a 3GS using this guide.

[http://everydaylht.com/howtos/desktop/create-ringtones-for-your-iphone-using-linux/](http://everydaylht.com/howtos/desktop/create-ringtones-for-your-iphone-using-linux/)

You have to make sure that the milliseconds are correct, and have to restart the phone to pick it up but it works a treat. The guide is good.

It seems that the sound length does not matter.  I acctually remove the complete tag and it worked anyway.

```
<key>TEST.m4r</key>
<dict>
<key>GUID</key><string>07D44991A45EA9F3</string>
<key>Name</key><string>Test</string>
<key>Total Time</key><integer>0</integer>
</dict> 
```

This is with IOS4.2, no jailbreak...

1 - Transcode the mp3 using ffmpeg (ffmpeg -i TEST.mp3 test.m4a)
2 - Copy the file to ~/.gvfs/Your iPhone/iTunes_Control/Ringtones/TEST.m4r
3 - Edit the file Ringtones.plist as mentionned without the lenght
4 - Reboot your iPhone (Don't know why, but it seems to update itself)

---

### Post by patrickballeux on 2010-12-19
Okay, I just make some more tests, and here is a script that will do the trick...

1 - Make sure that you have the folder Ringtones in your iPhone (~/.gvfs/Your iPhone/iTunes_Control/Ringtones)
2 - Put all your m4r files (mp3 converted to m4a, then renamed m4r) in the Ringtones folder
3 - On your desktop, create a script named updateRingtones.sh with this content:

```

#!/bin/bash
let index=0
rm ../iTunes/Ringtones.plist
echo "<?xml version=\"1.0\" encoding=\"UTF-8\"?>">../iTunes/Ringtones.plist
echo "<!DOCTYPE plist PUBLIC \"-//Apple Computer//DTD PLIST 1.0//EN\" \"http://www.apple.com/DTDs/PropertyList-1.0.dtd\">">>../iTunes/Ringtones.plist
echo "<plist version=\"1.0\">">>../iTunes/Ringtones.plist
echo "<dict>">>../iTunes/Ringtones.plist
echo "<key>Ringtones</key>">>../iTunes/Ringtones.plist
echo "	<dict>">>../iTunes/Ringtones.plist

for m4r in *.m4r;do
	let index=$index+1
	echo "		<key>$m4r</key>">>../iTunes/Ringtones.plist
	echo "		<dict>">>../iTunes/Ringtones.plist
	echo "		<key>GUID</key><string>000000000000000$index</string>">>../iTunes/Ringtones.plist
	n=$(echo $m4r | cut -d '.' -f1)
	echo "		<key>Name</key><string>$n</string>">>../iTunes/Ringtones.plist
	echo "		<key>Total Time</key><integer>0</integer>">>../iTunes/Ringtones.plist
	echo "		</dict>">>../iTunes/Ringtones.plist
done

echo "	</dict>">>../iTunes/Ringtones.plist
echo "</dict>">>../iTunes/Ringtones.plist
echo "</plist>">>../iTunes/Ringtones.plist

```

4 - Make that file "Runnable"
5 - Copy the script in your Ringtones folders
6 - Make a backup of ~/.gvfs/Your Phone/iTunes_Control/iTunes/Ringtones.plist (just in case)
7 - Simply execute the script from the Ringtones folders.  The plist will be updated automatically.
8 - Optionnal, update the names of your titles in your plist file
9 - IMPORTANT: Reboot your iPhone, seems to be needed so the iPhone will update it's internal content
10 - Enjoy your new ringtones!

Note: The script only support up to 9 ringtones as I use an index from 1 to 9...  It would be easy to fix this to support more so the GUID would be created in the right format.

But, it's a start!

---

### Post by pramsay13 on 2011-01-10
A special thanks to Patrick for the script file.
Finally, I couldn't get them working for a while, but it was because my Ringtone folder was in the iPhone root folder so I just moved it to the iTunes_Control folder and everything was perfect.
:)

---

### Post by yuanfangcan on 2011-07-03
The instruction here worked perfect for my iphone 3GS. 
I just have one question.  How to enhance the quality of the output ringtones?  Seems the quality of the ringtones are lower than the original mp3.

---

