---
title: "Using VLC player on iPhone with Ubuntu"
date: 2011-10-11
forum: General Help
---

### Post by unckybob on 2011-10-11
I just got this iPhone and I am a total iPhone nubie. All I want is to play video on it. Can someone please help? 

I have just installed the VLC player on my iPhone. When I select the app, it tells me I haven't any videos in my video library. It suggests that I: 

- Install OpenSSH via Cydia 
- Connect using your favorite SFTP client
- Browse to /var/mobile/Media 
- Upload your videos
- Close and reopen VLC 

This requires a network connection. It seems a little silly. 


I can connect my iPhone directly to my Ubuntu computer. When I do, I get two storage icons on my desktop: 

"Documents on Bob's iPhone", and 
"Bob's iPhone". 

The "Documents on Bob's iPhone" is empty. 

The "Bob's iPhone" contains a number of folders with subfolders: 

Books
DCIM 
Downloads
iTunes_Control
PhotoData
Photos
Podcasts
Purchases
Recordings
Safari
com.apple.dbaccess.lock
com.apple.itdbprep.postprocess.lock
com.apple.itunes.lock_sync
youtube-stderr
youtube-stdout

Isn't there some way I can copy a file onto this filesystem and then open the vlc player and run it on the copied file?

---

### Post by Agent Smith on 2011-10-11
After you have plugged your iPhone in, you should have "Documents on Bobs iPhone" shown. In there should be a VLC icon. Open it and there should be a folder shown. Drag your movies into this folder and they will appear on your iPhone when you open up the VLC app.
By the way files with ac3 sound encoding dont work very well.
Hope this helps.

---

### Post by unckybob on 2011-12-24
Unfortunately, there is no "VLC" folder in the location you mentioned. However, I have found that if I simply drag the video files to "Bob's iPhone" they show up when I open the VLC app. I have found that avi files seem to play the best although with some files portions of the sounds don't come through. Like background noise to the video you can hear, but the dialog doesn't come through.

---

