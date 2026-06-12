---
title: "ubuntu + Calibre + Kindle + error messgaes"
date: 2011-01-01
forum: General Help
---

### Post by Speedbum9 on 2011-01-01
running calibre with my kindle has been graet, however in the last week when i try and send the papers i like ot the kindle i get the following error message

[Errno 30] Read-only file system: '/media/Kindle/documents/News/The Irish Times (Friday, December 31, 2010) - calibre.mobi'

Traceback (most recent call last):
File "/usr/lib/calibre/calibre/gui2/device.py", line 56, in run
self.result = self.func(*self.args, **self.kwargs)
File "/usr/lib/calibre/calibre/gui2/device.py", line 233, in _upload_books
metadata=metadata, end_session=False)
File "/usr/lib/calibre/calibre/devices/usbms/driver.py", line 109, in upload_books
self.put_file(infile, filepath, replace_file=True)
File "/usr/lib/calibre/calibre/devices/usbms/cli.py", line 53, in put_file
with open(path, 'wb') as dest:
IOError: [Errno 30] Read-only file system: '/media/Kindle/documents/News/The Irish Times (Friday, December 31, 2010) - calibre.mobi'

can anyone help

---

### Post by markMDW on 2011-01-01
I also have a Kindle with Calibre and Ubuntu.  Although I haven't run into any errors, this check I found might turn out to be useful:

When plugging your Kindle into your computer via USB, it shows up as a  drive and shuts down the device's operating system.  The screen will  tell you to "eject" the Kindle from your computer in order to use it and  charge the battery through the USB cable.   At this point do you "eject" your Kindle or leave it in it's current status?  Regardless, if you are "unmounting" it ..or "ejecting" it perhaps the device's operating system becomes active and locks the media into "read only".  Here's the link where i found that information..
[http://iamyouruser.blogspot.com/2009/03/ubuntu-eject-kindle.html](http://iamyouruser.blogspot.com/2009/03/ubuntu-eject-kindle.html)

Someone with a solid idea of what's happening her should follow up and post a more correct response.  Until then I figured you'd want to know folks are looking into the matter

---

### Post by Speedbum9 on 2011-01-02
i've tried all the following on another forum, if this helps anyone at all

[http://www.urban75.net/vbulletin/threads/340655-ubuntu-Calibre-Kindle-error-messgaes](http://www.urban75.net/vbulletin/threads/340655-ubuntu-Calibre-Kindle-error-messgaes)

---

