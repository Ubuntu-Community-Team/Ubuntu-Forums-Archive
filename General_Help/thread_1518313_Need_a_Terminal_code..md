---
title: "Need a Terminal code."
date: 2010-06-26
forum: General Help
---

### Post by warfacegod on 2010-06-26
If it's possible (I assume that it is. There is little that can't be done with a Terminal.), I would like to set up a code, script, what ever the hell it's called. What I would like to have happen is this: I need it to collect information on all files in a folder and it's sub-folders and export that info to an .odt file. I need it to list the Artist, Album, and Song Title of all mp3s within that folder. There are many other non-mp3 files in the folder as well and those need to be ignored.

How do I go about doing this?

I know a few "tricks" with the Terminal but, for the sake of argument, let's all assume I'm a newb.:shock: (I'm not.)

---

### Post by warfacegod on 2010-06-26
And yes, I have heard of the man pages.

---

### Post by flanagan on 2010-06-26
How about something like:```
find . -type f -name "*.mp3" -printf "mp3info %p \n" | bash
```
 If need be, install mp3info using Synaptic. If you really need a .odt file, I suppose you could redirect the above output to a file, open it in OpenOffice.org's Word Processor, and save it as a .odt.

---

### Post by AlphaLexman on 2010-06-26
I found a nautilus-python script I posted at this thread: [http://ubuntuforums.org/showthread.php?t=1278985](http://ubuntuforums.org/showthread.php?t=1278985) that possibly could be modified to redirect the output to an .odt format. [Although it might be easier to output to a CSV format and import into OOo.]

---

### Post by warfacegod on 2010-06-26
> **flanagan said:**
> How about something like:```
find . -type f -name "*.mp3" -printf "mp3info %p \n" | bash
```
 If need be, install mp3info using Synaptic. If you really need a .odt file, I suppose you could redirect the above output to a file, open it in OpenOffice.org's Word Processor, and save it as a .odt.

Unmodified, the code gave me this:

```
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Bobby: No such file or directory
Error opening MP3: Caldwell/Come: No such file or directory
Error opening MP3: Rain: No such file or directory
Error opening MP3: or: No such file or directory
Error opening MP3: Come: No such file or directory
Error opening MP3: Shine/The: No such file or directory
Error opening MP3: Best: No such file or directory
Error opening MP3: Is: No such file or directory
Error opening MP3: Yet: No such file or directory
Error opening MP3: to: No such file or directory
Error opening MP3: Come.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Bobby: No such file or directory
Error opening MP3: Caldwell/Come: No such file or directory
Error opening MP3: Rain: No such file or directory
Error opening MP3: or: No such file or directory
Error opening MP3: Come: No such file or directory
Error opening MP3: Shine/Beyond: No such file or directory
Error opening MP3: the: No such file or directory
Error opening MP3: Sea.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Rhapsody/Rain: No such file or directory
Error opening MP3: of: No such file or directory
Error opening MP3: a: No such file or directory
Error opening MP3: Thousand: No such file or directory
Error opening MP3: Flames/Rain: No such file or directory
Error opening MP3: of: No such file or directory
Error opening MP3: a: No such file or directory
Error opening MP3: Thousand: No such file or directory
Error opening MP3: Flames.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Rhapsody/Dawn: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Victory/Holy: No such file or directory
Error opening MP3: Thunderforce.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Rhapsody/Dawn: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Victory/The: No such file or directory
Error opening MP3: Village: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Dwarves.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Rhapsody/Dawn: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Victory/Dawn: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Victory.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/Got: No such file or directory
Error opening MP3: the: No such file or directory
Error opening MP3: Time.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/In: No such file or directory
Error opening MP3: My: No such file or directory
Error opening MP3: World.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/Keep: No such file or directory
Error opening MP3: It: No such file or directory
Error opening MP3: in: No such file or directory
Error opening MP3: the: No such file or directory
Error opening MP3: Family.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/Belly: No such file or directory
Error opening MP3: of: No such file or directory
Error opening MP3: the: No such file or directory
Error opening MP3: Beast.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/Gridlock.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/Blood.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/H8: No such file or directory
Error opening MP3: Red.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/Time.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Persistence: No such file or directory
Error opening MP3: Of: No such file or directory
Error opening MP3: Time/Discharge.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Anthrax/Among: No such file or directory
Error opening MP3: the: No such file or directory
Error opening MP3: Living/Among: No such file or directory
Error opening MP3: the: No such file or directory
Error opening MP3: Living.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/Somnus/Gateway: No such file or directory
Error opening MP3: to: No such file or directory
Error opening MP3: Hell_: No such file or directory
Error opening MP3: A: No such file or directory
Error opening MP3: Tribute: No such file or directory
Error opening MP3: to: No such file or directory
Error opening MP3: Slayer/Seasons: No such file or directory
Error opening MP3: in: No such file or directory
Error opening MP3: the: No such file or directory
Error opening MP3: Abyss.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/In: No such file or directory
Error opening MP3: Extremo/Mein: No such file or directory
Error opening MP3: Rasend: No such file or directory
Error opening MP3: Herz/Spielmann.mp3: No such file or directory
Error opening MP3: ./War: No such file or directory
Error opening MP3: Cloud/In: No such file or directory
Error opening MP3: Extremo/Mein: No such file or directory
Error opening MP3: Rasend: No such file or directory
Error opening MP3: Herz/Poc: No such file or directory
Error opening MP3: Vecem.mp3: No such file or directory
bash: line 20: syntax error near unexpected token `('
bash: line 20: `mp3info ./War Cloud/In Extremo/Mein Rasend Herz/Liam (Gälische Version).mp3 '

```

It's a start.

---

### Post by warfacegod on 2010-06-26
> **AlphaLexman said:**
> I found a nautilus-python script I posted at this thread: [http://ubuntuforums.org/showthread.php?t=1278985](http://ubuntuforums.org/showthread.php?t=1278985) that possibly could be modified to redirect the output to an .odt format. [Although it might be easier to output to a CSV format and import into OOo.]

That script is way too complicated for me to even pretend I could output it in any format.

Thanks for replying, both of you.

---

### Post by AlphaLexman on 2010-06-26
You have spaces in your filenames... Try putting quotes around '%p'

---

### Post by warfacegod on 2010-06-26
> **AlphaLexman said:**
> You have spaces in your filenames... Try putting quotes around '%p'

Okay, that got me closer.

```
File: ./War Cloud/Bobby Caldwell/Come Rain or Come Shine/The Best Is Yet to Come.mp3
Title:   The Best Is Yet to Come        Track: 
Artist:  Bobby Caldwell
Album:   Come Rain or Come Shine        Year:  
Comment:                                Genre: Jazz [8]

File: ./War Cloud/Bobby Caldwell/Come Rain or Come Shine/Beyond the Sea.mp3
Title:   Beyond the Sea                 Track: 
Artist:  Bobby Caldwell
Album:   Come Rain or Come Shine        Year:  
Comment:                                Genre: Jazz [8]

File: ./War Cloud/Rhapsody/Rain of a Thousand Flames/Rain of a Thousand Flames.mp3
Title:   Rain of a Thousand Flames      Track: 1
Artist:  Rhapsody
Album:   Rain of a Thousand Flames      Year:  
Comment:                                Genre:  [255]

File: ./War Cloud/Rhapsody/Dawn Of Victory/Holy Thunderforce.mp3
Title:   Holy Thunderforce              Track: 7
Artist:  Rhapsody
Album:   Dawn Of Victory                Year:  
Comment:                                Genre:  [255]

File: ./War Cloud/Rhapsody/Dawn Of Victory/The Village Of Dwarves.mp3
Title:   The Village Of Dwarves         Track: 4
Artist:  Rhapsody
Album:   Dawn Of Victory                Year:  
Comment:                                Genre:  [255]

File: ./War Cloud/Rhapsody/Dawn Of Victory/Dawn Of Victory.mp3
Title:   Dawn Of Victory                Track: 2
Artist:  Rhapsody
Album:   Dawn Of Victory                Year:  
Comment:                                Genre:  [255]

File: ./War Cloud/Anthrax/Persistence Of Time/Got the Time.mp3
Title:   Got the Time                   Track: 8
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Persistence Of Time/In My World.mp3
Title:   In My World                    Track: 4
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Persistence Of Time/Keep It in the Family.mp3
Title:   Keep It in the Family          Track: 3
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Persistence Of Time/Belly of the Beast.mp3
Title:   Belly of the Beast             Track: 7
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Persistence Of Time/Gridlock.mp3
Title:   Gridlock                       Track: 5
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Persistence Of Time/Blood.mp3
Title:   Blood                          Track: 2
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Persistence Of Time/H8 Red.mp3
Title:   H8 Red                         Track: 9
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Persistence Of Time/Time.mp3
Title:   Time                           Track: 1
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Persistence Of Time/Discharge.mp3
Title:   Discharge                      Track: 11
Artist:  Anthrax
Album:   Persistence Of Time            Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Anthrax/Among the Living/Among the Living.mp3
Title:   Among the Living               Track: 1
Artist:  Anthrax
Album:   Among the Living               Year:  
Comment:                                Genre: Heavy Metal [137]

File: ./War Cloud/Somnus/Gateway to Hell_ A Tribute to Slayer/Seasons in the Abyss.mp3
Title:   Seasons in the Abyss           Track: 13
Artist:  Somnus
Album:   Gateway to Hell: A Tribute to  Year:  1999
Comment:                                Genre:  [255]

File: ./War Cloud/In Extremo/Mein Rasend Herz/Spielmann.mp3
Title:   Spielmann                      Track: 12
Artist:  In Extremo
Album:   Mein Rasend Herz               Year:  2008
Comment:                                Genre:  [255]

File: ./War Cloud/In Extremo/Mein Rasend Herz/Poc Vecem.mp3
Title:   Poc Vecem                      Track: 11
Artist:  In Extremo
Album:   Mein Rasend Herz               Year:  2005
Comment:                                Genre:  [255]

File: ./War Cloud/In Extremo/Mein Rasend Herz/Liam (Gälische Version).mp3
Title:   Liam (G&#65533;lische Version)        Track: 8
Artist:  In Extremo
Album:   Mein Rasend Herz               Year:  2005
Comment:                                Genre:  [255]

File: ./War Cloud/In Extremo/Mein Rasend Herz/Nur Ihr Allein.mp3
Title:   Nur Ihr Allein                 Track: 4
Artist:  In Extremo
Album:   Mein Rasend Herz               Year:  2005
Comment:                                Genre:  [255]

File: ./War Cloud/In Extremo/Sünder Ohne Zügel/Vollmond.mp3
Title:   Vollmond                       Track: 6
Artist:  In Extremo
Album:   S&#65533;nder Ohne Z&#65533;gel              Year:  2002
Comment:                                Genre:  [255]

Error opening MP3: ./War Cloud/Reverend Horton Heat/Its: No such file or directory
Error opening MP3: Martini: No such file or directory
Error opening MP3: Time/Its Martini Time.mp3: No such file or directory
File: ./War Cloud/Lake Of Tears/Forever Autumn/Come Night I Reign.mp3
Title:   Come Night I Reign             Track: 7
Artist:  Lake Of Tears
Album:   Forever Autumn                 Year:  
Comment:                                Genre:  [255]

File: ./War Cloud/Lake Of Tears/Forever Autumn/Forever Autumn.mp3
Title:   Forever Autumn                 Track: 3
Artist:  Lake Of Tears
Album:   Forever Autumn                 Year:  
Comment:                                Genre:  [255]

bash: line 27: syntax error near unexpected token `('
bash: line 27: `mp3info './War Cloud/Amorphis/Elegy/My Kantele (Acoustic Reprise).mp3' '
```

Is there a way to have it display only Artist, Title, and Album. All of the other info is useless to me (for this particular situation anyway). It also seems to be missing about 1700 files.

---

### Post by warfacegod on 2010-06-26
Perhaps a different approach. Is it possible to get the Amarok 1.4 scanner to output to text?

---

### Post by AlphaLexman on 2010-06-26
Good idea. 

Kid3-qt [in repo's] can export all mp3 id3 v1 &/or v2 info to a csv file. You could import that file into a spreadsheet, delete the columns you don't need, and go from there!

# Sometimes the command line IS harder.

---

### Post by warfacegod on 2010-06-26
> **AlphaLexman said:**
> Good idea. 

Kid3-qt [in repo's] can export all mp3 id3 v1 &/or v2 info to a csv file. You could import that file into a spreadsheet, delete the columns you don't need, and go from there!

# Sometimes the command line IS harder.

All right, I'm missing something here. I told it to Export to a CVS format and I got a blank document. Create Playlist did nothing at all.

---

### Post by AlphaLexman on 2010-06-26
> **warfacegod said:**
> All right, I'm missing something here. I told it to Export to a CVS format and I got a blank document. Create Playlist did nothing at all.

Is your goal to create a playlist or to create an .odt file?

If you want a playlist almost EVERY music player can do that for you!

---

### Post by warfacegod on 2010-06-26
> **AlphaLexman said:**
> Is your goal to create a playlist or to create an .odt file?

If you want a playlist almost EVERY music player can do that for you!

.odt file. I just thought I'd see if I could copy and paste the info out of a playlist file when I got a blank document. Ignore the whole playlist thing.

---

### Post by AlphaLexman on 2010-06-26
In Kid3-qt make sure you "Select all" [Ctrl-a] before exporting or create playlist.

---

### Post by warfacegod on 2010-06-26
So I made some progress. It will list one song. I already tried to Select All and got a blank. Incidentally it's listed as ALT+A but the way everyone is used to, Ctrl+A, also works.

When open a folder all the way to the song and highlight the song, it will list it. If I do it with two different folders and songs, it only lists the first one highlighted.

And some songs aren't listing at all, singly or not. I assume this means I have no tags for these.

---

### Post by AlphaLexman on 2010-06-26
> **warfacegod said:**
> So I made some progress. It will list one song. I already tried to Select All and got a blank. Incidentally it's listed as ALT+A but the way everyone is used to, Ctrl+A, also works.

Make sure you have your sub-directories expanded and selected. Kid3-qt will not automatically select sub-dirs unless they are expanded [by the plus sign]

---

### Post by warfacegod on 2010-06-26
That's what I figured. Open several hundred sub-directories by hand. Curses.

---

### Post by Leppie on 2010-06-26
had a look at the python script.
eliminated everything except for title, album and artist
i'm not a python expert, but there doesn't really seem to be a routine sourcing sub folders.
well, you can always give it a try ;)

```
#!/usr/bin/python

# this script can be installed to the user account by running the following commands:

# sudo apt-get install python-nautilus python-mutagen python-pyexiv2
# mkdir ~/.nautilus/python-extensions (if it doesn't exist already)
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
        )

    def update_file_info(self, file):
        if file.get_uri_scheme() != 'file':
            return

        filename = urllib.unquote(file.get_uri()[7:])
        
        # mpeg ID3 handling
        if file.is_mime_type('audio/mpeg'):
            try:
                audio = EasyID3(filename)   # [SabreWolfy] some files have no ID3 tag
            except:
                # file.add_string_attribute('title', "[No ID3 Tag]")
                # file.add_string_attribute('album', "[No ID3 Tag]")
                # file.add_string_attribute('artist', "[No ID3 Tag]")
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


        else:
            file.add_string_attribute('title', '')
            file.add_string_attribute('album', '')
            file.add_string_attribute('artist', '')
        
        self.get_columns()
```

---

### Post by ufleisch on 2010-06-27
> **warfacegod said:**
> That's what I figured. Open several hundred sub-directories by hand. Curses.

No need to curse. You can use *Filter*, then *All* to open all subdirectories automatically, or even better, use the latest version of Kid3 (1.4), which has improved playlist support and can export a playlist will all tracks from all subdirectories.

---

