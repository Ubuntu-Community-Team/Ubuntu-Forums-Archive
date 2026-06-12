---
title: "Artist information and...COPY AND PASTE..."
date: 2009-09-30
forum: General Help
---

### Post by thegutterpoet on 2009-09-30
Is there a way for making the 'artist' information, and even 'album title' of music files, show up in the column titles in Folder Views??? As windows does naturally...

Also...When I try to select a large number of files, I dont have the option of selecting a certain amount of my choosing...Its either select one file in a list, or select ALL files...again, can this be remedied? reverted back to the windows routine, which is more suitable to my needs...

Any help is greatly appreciated...and i am running 9.04.

---

### Post by _Narcisse_ on 2009-09-30
Hey

Well, I don't know about the "Artist" information displayed in the file browser (that would be great), but for your second question, if I get it correctly, you can do as you would do in Windows to add files to your selection by holding the Ctrl key and selecting them. Is it what you meant ?

---

### Post by thegutterpoet on 2009-09-30
No mate...I meant, click the left mouse button and drag the cursor over a list of files to make a selection which sticks when you release the left mouse button.

---

### Post by AlphaLexman on 2009-09-30
Yeah, there IS a way... (I did it! - screenshot - nautilus)

But, I forgot the link for the instructions...:(

will post back if I find it.

---

### Post by thegutterpoet on 2009-09-30
thats what im after, mate...please try to remember where you found such gold dust...

---

### Post by AlphaLexman on 2009-09-30
Found it, Just needed a little coffee :)


```
#!/usr/bin/python

# this script can installed to the user account by running the following commands:

# sudo apt-get install python-nautilus python-mutagen python-pyexiv2
# mkdir ~/.nautilus/python-extensions
# cp bsc-v2.py ~/.nautilus/python-extensions
# chmod a+x ~/.nautilus/python-extensions/bsc-v2.py

# alternatively, you may be able to place the script in:
# /usr/lib/nautilus/extensions-2.0/python/

# change log:
# jmdsdf: version 2 adds extra ID3 and EXIF tag support
# jmdsdf: added better error handling for ID3 tags, added mp3 length support, distinguished
#         between exif image size and true image size
 
import os
import urllib
import nautilus
# for id3 support
from mutagen.easyid3 import EasyID3
from mutagen.mp3 import MPEGInfo
from mutagen.mp3 import MP3
# for exif support
import pyexiv2

# for reading dimensions
import Image


class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
	def __init__(self):
		pass

	def get_columns(self):
		return (
			# id3 support
			nautilus.Column("NautilusPython::title_column",
				"title",
				"Title",
				"Song title"),
			nautilus.Column("NautilusPython::album_column",
				"album",
				"Album",
				"Album"),
			nautilus.Column("NautilusPython::artist_column",
				"artist",
				"Artist",
				"Artist"),
			nautilus.Column("NautilusPython::tracknumber_column",
				"tracknumber",
				"Track",
				"Track number"),
			nautilus.Column("NautilusPython::genre_column",
				"genre",
				"Genre",
				"Genre"),
			nautilus.Column("NautilusPython::date_column",
				"date",
				"Date",
				"Date"),
			nautilus.Column("NautilusPython::bitrate_column",
				"bitrate",
				"Bitrate",
				"Audio Bitrate in kilo bits per second"),
			nautilus.Column("NautilusPython::length_column",
				"length",
				"Length",
				"Length of audio"),
			# exif support
			nautilus.Column("NautilusPython::exif_datetime_original_column",
				"exif_datetime_original",
				"EXIF Dateshot ",
				"Get the photo capture date from EXIF data"),
			nautilus.Column("NautilusPython::exif_software_column",
				"exif_software",
				"EXIF Software",
				"EXIF - software used to save image"),
			nautilus.Column("NautilusPython::exif_flash_column",
				"exif_flash",
				"EXIF flash",
				"EXIF - flash mode"),
			nautilus.Column("NautilusPython::exif_pixeldimensions_column",
				"exif_pixeldimensions",
				"EXIF Image Size",
				"EXIF Image size - pixel dimensions"),
			nautilus.Column("NautilusPython::pixeldimensions_column",
				"pixeldimensions",
				"Image Size",
				"Image size - pixel dimensions"),
		)

	def update_file_info(self, file):
		if file.get_uri_scheme() != 'file':
			return

		filename = urllib.unquote(file.get_uri()[7:])
		
		# mpeg ID3 handling
		if file.is_mime_type('audio/mpeg'):
			# [SabreWolfy] now we know it's an MP3 file with or without an ID3 tag
			# [SabreWolfy] but the following method works in both cases
			length = MP3(filename).info.length
			# [SabreWolfy] added consistent formatting of times in format hh:mm:ss
			# [SabreWolfy[ to allow for correct column sorting by length
			if length>3600:
				mp3length = "%02i:%02i:%02i" % ((int(length/3600)), (int(length/60%60)), (int(length%60)))
			else:
				mp3length = "00:%02i:%02i" % ((int(length/60%60)), int(length%60))
			file.add_string_attribute('length', mp3length)

			try:
				audio = EasyID3(filename)   # [SabreWolfy] some files have no ID3 tag
			except:
				# file.add_string_attribute('title', "[No ID3 Tag]")
				# file.add_string_attribute('album', "[No ID3 Tag]")
				# file.add_string_attribute('artist', "[No ID3 Tag]")
				# file.add_string_attribute('tracknumber', "[No ID3 Tag]")
				# file.add_string_attribute('genre', "[No ID3 Tag]")
				# file.add_string_attribute('date', "[No ID3 Tag]")
				NoID3 = True   # [SabreWolfy] dummy statement

			# sometimes the audio variable will not have one of these items defined, that's why
			# there is this long try / except attempt
			try:
				file.add_string_attribute('title', audio["title"][0])
			except:
				file.add_string_attribute('title', "[n/a]")
			try:
				file.add_string_attribute('album', audio["album"][0])
			except:
				file.add_string_attribute('album', "[n/a]")
			try:
				file.add_string_attribute('artist', audio["artist"][0])
			except:
				file.add_string_attribute('artist', "[n/a]")
			try:
				file.add_string_attribute('tracknumber', audio["tracknumber"][0])
			except:
				file.add_string_attribute('tracknumber', "[n/a]")
			try:
				file.add_string_attribute('genre', audio["genre"][0])
			except:
				file.add_string_attribute('genre', "[n/a]")
			try:
				file.add_string_attribute('date', audio["date"][0])
			except:
				file.add_string_attribute('date', "[n/a]")

			try:
				mpfile = open (filename)
				mpinfo = MPEGInfo (mpfile)
				file.add_string_attribute('bitrate', str(mpinfo.bitrate/1000) + " Kbps")
			except:
				file.add_string_attribute('bitrate', "[n/a]")


		else:
			file.add_string_attribute('title', '')
			file.add_string_attribute('album', '')
			file.add_string_attribute('artist', '')
			file.add_string_attribute('tracknumber', '')
			file.add_string_attribute('genre', '')
			file.add_string_attribute('date', '')
			file.add_string_attribute('bitrate', '')
			file.add_string_attribute('length', '')
		
		# jpeg EXIF handling (also try running it on other image types, if only for the image size)
		if file.is_mime_type('image/jpeg') or file.is_mime_type('image/png') or file.is_mime_type('image/gif') or file.is_mime_type('image/bmp'):
			try:
				img = pyexiv2.Image(filename)
				img.readMetadata()
				file.add_string_attribute('exif_datetime_original',str(img['Exif.Photo.DateTimeOriginal']))
				file.add_string_attribute('exif_software',str(img['Exif.Image.Software']))
				file.add_string_attribute('exif_flash',str(img['Exif.Photo.Flash']))
				file.add_string_attribute('exif_pixeldimensions',str(img['Exif.Photo.PixelXDimension'])+'x'+str(img['Exif.Photo.PixelYDimension']))
			except:
				# no exif data?
				file.add_string_attribute('exif_datetime_original',"")
				file.add_string_attribute('exif_software',"")
				file.add_string_attribute('exif_flash',"")
				file.add_string_attribute('exif_pixeldimensions',"")
			# try read image info directly
			try:
				im = Image.open(filename)
				file.add_string_attribute('pixeldimensions',str(im.size[0])+'x'+str(im.size[1]))
			except:
				file.add_string_attribute('pixeldimensions',"[image read error]")
		else:
			file.add_string_attribute('exif_datetime_original', '')
			file.add_string_attribute('exif_software', '')
			file.add_string_attribute('exif_flash', '')
			file.add_string_attribute('exif_pixeldimensions', '')
			file.add_string_attribute('pixeldimensions', '')

		self.get_columns() 
	

```

---

### Post by _Narcisse_ on 2009-09-30
Hey, I think [this thread]("http://ubuntuforums.org/showthread.php?t=878683") is what you're looking for. At least for the "artist" column.
I don't know how to reproduce Windows behavior for selecting files in lists though.
Sorry I didn't get what you meant the first time. 

Hope this helps. :)

---

### Post by Giblet5 on 2009-09-30
> **AlphaLexman said:**
> Found it, Just needed a little coffee :)

That's a very nice hack.

Great find, thanks!

---

### Post by thegutterpoet on 2009-10-01
Thanks for the attempts to help...I ran the commands, but got stuck here:>

**mkdir: cannot create directory `/home/raphael/.nautilus/python-extensions': File exists**

---

### Post by thegutterpoet on 2009-10-02
Could someone please help me to work out what to type into the terminal to get the artist information showing in the List View?

I tried some of the commands listed above, installed the python packages, but then got stumped...as I am moving a large amount of mixed up files from Windows to my Ubuntu Music folder, they are appearing in a mass mess, and to sort them takes so fkin long...as I know its possible to get artists, as a column, i simply must get this show on the road...it will literally save me HOURS...

---

### Post by thegutterpoet on 2009-10-04
Still waiting and hoping for some more accurate help on this matter...as my ubuntu doesnt seem to like the codes suggested above...which i was sticking in the terminal...

PLEASE HELP

---

