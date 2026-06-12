---
title: "Trouble Shooting 11.04/  Calibre / Sony E Reader / Device Mounting as Read Only"
date: 2011-11-13
forum: General Help
---

### Post by stevennlv on 2011-11-13
I have an old Dell 1501 w/ 11.04. It works perfectly with the e reader.

I'm trying to get away from the old hardware. I have a shiny new box. Too new for 11.04 (lots and lots of driver issues).

So, my new box has 7 as the host and 11.04 running in VMware player.

I try to keep 7 off the net as much as possible. The reader will work there. But I want it to work in the VM.

The reader is connecting to the VM. Calibre can see it. But, calibre cannot write to the reader b/c it is being mounted as read only.

This is the error message I am getting from calibre when I try to "Send to Device" :

 p, li { white-space: pre-wrap; }  [Errno 13] Permission denied: u'/media/usb1/.metadata.calibre'
 
 Traceback (most recent call last):
   File "/usr/lib/calibre/calibre/gui2/device.py", line 64, in run
     self.result = self.func(*self.args, **self.kwargs)
   File "/usr/lib/calibre/calibre/gui2/device.py", line 307, in _books
     mainlist = self.device.books(oncard=None, end_session=False)
   File "/usr/lib/calibre/calibre/devices/usbms/driver.py", line 164, in books
     self.sync_booklists((bl, None, None))
   File "/usr/lib/calibre/calibre/devices/usbms/driver.py", line 305, in sync_booklists
     write_prefix(self._main_prefix, 0)
   File "/usr/lib/calibre/calibre/devices/usbms/driver.py", line 303, in write_prefix
     with open(self.normalize_path(os.path.join(prefix, self.METADATA_CACHE)), 'wb') as f:
 IOError: [Errno 13] Permission denied: u'/media/usb1/.metadata.calibre'
 

I have been trouble shooting for hours just to get this far (at first the VM wouldn't see the reader at all) and I'm out of ideas. Once you start getting away from point and click and in to the guts I'm over my head.

Please note: I set calibre up the same way on the 1501 and the VM. It works on the 1501. Also, I have usbmount installed in the VM because w/o it I could not "see" usb devices to mount them manually. (I looked everywhere I could think of.) For reasons that are beyond me some usb devices mount as read only and others as read / write. I have lots of different types of usb sticks and a couple of different mp3 players some mount as r/o some as r/w? 

Any help would be greatly appreciated.

Thankx

---

