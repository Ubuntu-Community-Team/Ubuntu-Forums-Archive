---
title: "Help Renaming Video Files"
date: 2011-08-04
forum: General Help
---

### Post by dwlima on 2011-08-04
I have hundreds of MTS and AVI files since 2000 and would like to rename them in the following manner based on the date created: DD-MMM-YYYY HH.MM.SS_X; where X begins at 1 and increments by 1 if there are dublicate date/time stamped videos.

Ex: 19-Nov-2002 08.12.30.avi, 19-Nov-2002 08:13:30_1 and 19-Nov-2002 08:13:30_2

Someone previously wrote the following script for me, and it works great for photos. It uses EXIV2 to get the image date created info. I have  tried to understand the script, but am struggling. The video files I have can use the date modified since I have not modified them since I filmed them.

Any help would be hugely appreciated.


#!/usr/bin/env python

import os
import stat
import pyexiv2
import time

directory = '/home/david/Desktop/test'

# For every file in the directory
for filename in os.listdir(directory):
    filepath = '%s/%s' % (directory, filename)

    # If it's not a file, ignore it
    if not os.path.isfile(filepath):
        continue
        
    # Get creation time. If it cannot, it will be "Unknown"
    try:
        metadata = pyexiv2.ImageMetadata(filepath)
        metadata.read()
        tag = metadata['Exif.Image.DateTime']
        creationTime = time.strptime(tag.raw_value, '%Y:%m:%d %H:%M:%S')
        creationTime = time.strftime('%d-%b-%Y %H.%M.%S', creationTime)
    except Exception, e:
        creationTime = 'Unknown'
        print 'ERROR: %s has no exif creation time' % filename
    

    # Get file extension. eg. file.jpg -> jpg
    extension = '.'.join(filename.split('.')[1:])

    # Get filename
    newFilename = '%s/%s.%s' % (directory, creationTime, extension)

    # Check if it already exists
    if os.path.exists(newFilename):
        i = 1
        while (os.path.exists(newFilename)):
            newFilename = '%s/%s_%s.%s' % (directory, creationTime, i, extension)
            i += 1
    print newFilename
    #os.rename(filepath, newFilename)

---

### Post by dwlima on 2011-08-04
I finally figured it out:

#!/usr/bin/env python

import os
import stat
import datetime

directory = '/home/david/Desktop/Test'

# For every file in the directory
for filename in os.listdir(directory):
    filepath = '%s/%s' % (directory, filename)

    # If it's not a file, ignore it
    if not os.path.isfile(filepath):
        continue
        
    # Get unix creation time
    unixCreation = os.stat(filepath).st_mtime
    
    # Convert to string. eg 1311602304 -> 26-Jul-2011
    dateStr = datetime.date.fromtimestamp(unixCreation).strftime('%d-%b-%Y')
    timeStr = datetime.datetime.fromtimestamp(unixCreation).strftime('%H.%M.%S')

    # Get file extension. eg. file.jpg -> jpg
    extension = '.'.join(filename.split('.')[1:])

    # Get filename
    newFilename = '%s/%s %s.%s' % (directory, dateStr, timeStr, extension)

    # Check if it already exists
    i = 0
    while (os.path.exists(newFilename)):
        newFilename = '%s/%s %s_%s.%s' % (directory, timeStr, dateStr, i, extension)
        i += 1
    
    #print '"%s" -> "%s"' % (filepath, newFilename)
    os.rename(filepath, newFilename)

---

