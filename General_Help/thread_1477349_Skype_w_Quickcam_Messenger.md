---
title: "Skype w/ Quickcam Messenger"
date: 2010-05-08
forum: General Help
---

### Post by sripplinger on 2010-05-08
I tried installing Skype when I had Jaunty.  I now have Lucid and have the same issues.

My webcam is a Logitech Quickcam Messenger.  I can see it using cheese or kopete.  In Skype I apparently have a detected video source named "Camera", but when I try clicking the test button nothing happens.  I have also tried loading skype with```
bin - c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
```but results are the same.  What now?

---

### Post by meho_r on 2010-05-08
This worked for me:

1. Rename skype in /usr/bin to skype.real:
```

sudo mv /usr/bin/skype /usr/bin/skype.real

```

2. Create a new skype file in /usr/bin:
```

sudo gedit /usr/bin/skype

```

3. Paste inside the opened file these lines:
```

#!/bin/sh 

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so  /usr/bin/skype.real "$@"

```

4. Save the file and make it executable:
```

sudo chmod +x /usr/bin/skype

```

P.S. Log out once, just in case. And don't forget to turn on the camera before starting Skype ;)

---

### Post by dodle on 2010-07-07
I see that this thread is a couple months old, but I am having the exact same problem.  The above solution did not work for me.  The only difference from the OP is that I am using Ubuntu not Kubuntu.  Has anyone figured out a solution for this?  According to the wiki, [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams), the Logitech Quickcam Messenger should work with some "fiddling", but does not say what "fiddling" needs to be done.  It says the driver is "gspca", but I do not see it in the repos.  Is it pre-installed?  The webcam works great with Cheese, but not at all with Skype.

---

### Post by energybeing on 2010-07-07
What worked for me is do everything the same as he said other than when you open skype with gedit, use this code instead
```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real
```

---

### Post by sripplinger on 2010-07-07
I actually ended up having to purchase a more modern webcam.  I got a Rosewill one for about $20 and it's working fine.

---

### Post by dodle on 2010-07-08
> **energybeing said:**
> What worked for me is do everything the same as he said other than when you open skype with gedit, use this code instead
```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real
```

No success :(.

---

### Post by wgarcia on 2010-09-10
I also have a Logitetch Quickcam Messanger, and the solution suggested in #4 worked for me. 

There is no need to change the name of skype to skype.real and to create a new file called "skype". THere is already a file called "skype-wrapper" in /usr/bin which you can edit and add "export XLIB_SKIP_ARGB_VISUALS=1" there. Skype-wrapper ends up looking as:

#!/bin/sh

if [ ! -e ~/.Skype/shared.xml ]; then
  mkdir -p ~/.Skype
  cp /usr/share/skype/shared.xml ~/.Skype/shared.xml
fi

export XLIB_SKIP_ARGB_VISUALS=1

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype "$@"


The advantage of doing it like this is that you don't have to touch the menu as it already points to "skype-wrapper".

---

### Post by Wolf-Ekkehard on 2011-02-15
Thanks wgarcia!  If you are running a 64 bit OS, you have to change to
```

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype "$@"

```

i.e. pointing to the lib32 libraries for skype.

I have an additional favor to ask: You all obviously got the Quickcam Messenger working under 10.10.  Where and how did you get the drivers?  

For me it didn't "just work" when I plugged the camera into the USB port (no drivers built into the kernel?).  I had the camera working on a previous 32-bit machine that I had running for years, and I recall that I had used the qc-usb-messenger-1.x driver from Christian Magnusson.  Is that still the preferred method to get a driver, or is there something else/better?

Any additional insight would be highly appreciated!!!

Edit:  The drivers were there, but I couldn't get the Quickcam Messenger to work in my 64 bit system with reasonable effort, so I just picked up a Logitech HD Webcam C310 for less than thirty bucks.  I should have done that a long time ago - the image quality is so much better, and the camera portion of it works out of the box without loading special drivers or the need of a wrapper around skype for any reason.

---

