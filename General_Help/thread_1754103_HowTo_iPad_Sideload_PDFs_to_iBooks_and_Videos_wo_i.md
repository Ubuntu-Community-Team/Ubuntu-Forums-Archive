---
title: "HowTo: iPad: Sideload PDFs to iBooks and Videos w/o iTunes (or Wine/VBox)"
date: 2011-05-09
forum: General Help
---

### Post by barrmulio on 2011-05-09
In my quest to try and minimize my use of my virtual w7, I uncovered how to sideload PDFs to iBooks on Natty.  

Since I've leeched off so much of the knowledge in these forums for the last few years I thought I could contribute something.

This method should work on older distro's but I haven't had a chance to see how/if the ipad will mount. This was tested with an iPad2 on natty x64.

First, install libimobiledevice2
```
$ sudo apt-get install libimobiledevice2
```

_PDFs on iBooks_
1. Plug the iPad to the usb port on your computer
2. Let it mount, under Devices you will see Documents and XXXX'd iPad (whatever you called it during initial setup).  Click on your iPad folder.
3. Go to the Books folder
4. Copy the PDF to the root of the Books folder, e.g. filename.pdf
5. Open Books.plist (located in the Books folder) in gedit
6. Between the <array> tags, you will find several <dict> entries for ebooks and pdfs already sideloaded.  Copy one, changing the filename to your pdf filename, or use the entry below, substituting "pdf_filename" for the name of your file
```
<dict>
	<key>Name</key><string>pdf_filename</string>
	<key>Has Artwork</key><true/>
	<key>Path</key><string>pdf_filename.pdf</string>
</dict>
```
7. Fully close out of iBooks (tap home twice and click red button) if opened, and you should see your PDF under Collections-->PDFs

_Uploading Videos Using OPlayer_
I don't work for OPlayer, but found it the easiest to use since  VLC isn't available anymore
1. Download OPlayerHD [Lite]
2. Plug the iPad to the usb port on your computer
3. Let it mount, under Devices you will see Documents and XXXX'd iPad (whatever you called it during initial setup).  Click on Documents folder.
4. Click on OPlayerHD [Lite]
5. Click on Documents
6. Copy over any files - so far all my avis and mkv files have played flawlessly w/o needing to convert in handbrake beforehand

--------------
I hope this helps someone...if there are any questions feel free to PM me or post and I'll do my best to help

---

### Post by haradeep on 2011-06-20
Hi,

It helped me. thanks.
With out below one it works. Is it a new one.


One question
<key>Persistent ID</key><string>E3125AD2AF3433CF</string>
what is Persistent ID?

below is my code.


```

<dict>
			<key>Name</key><string>OOPS IN PHP</string>
			<key>Persistent ID</key><string>E3125AD2AF3433CF</string>
			<key>Has Artwork</key><false/>
			<key>Path</key><string>oop_in_php_tutorial_for_killerphp.com.pdf</string>
		</dict>
```

---

### Post by tcoffee on 2012-01-16
This worked for me as written in transferring PDFs to iBooks on the iPod touch. Thanks for the tip!

---

