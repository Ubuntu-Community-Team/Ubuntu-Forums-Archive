---
title: "Video Capture device"
date: 2010-11-20
forum: General Help
---

### Post by doyleman on 2010-11-20
Does anyone know of a program that can capture video/audio through a USB Device (specifically: ENCORE USB Audio/Video Grabber ENMVG USB 2.0 Interface; [[http://www.newegg.com/Product/Product.aspx?Item=N82E16815153009&Tpk=Encore%20Video%20Grabber]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815153009&Tpk=Encore%20Video%20Grabber")]

Any and all help greatly appreciated. Thank you.

---

### Post by doyleman on 2010-11-21
Bump

---

### Post by doyleman on 2010-11-22
bump, again.

---

### Post by asmoore82 on 2010-11-22
That specific model that you link'd is not HDTV compatible.

This means that if Linux drivers are available, it will be a V4L (Video For Linux) or V4L2 device. Almost all Linux video players support this class of devices; and any format supported by vlc or mplayer; can be transcoded and saved to a new video file by vlc or mencoder.

tvtime is probably the best desktop app for viewing these devices but it cannot record.

Unless you really need analog inputs for digitizing old recordings,
I would recommend paying a little more for an HDTV compatible device like this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16815260023](http://www.newegg.com/Product/Product.aspx?Item=N82E16815260023) . These devices support the ATSC standard for free over-the-air HDTV broadcasts and the QAM standard for unencrypted digital cable. They are recognized in Linux as DVB (Digital Video Broadcast - a European Standard) devices. They are similarly supported by vlc/mplayer/mencoder.

me-tv is a great desktop app for viewing and recording HDTV.

The 500-pound gorilla that I haven't mentioned is of course MythTV.
MythTV is a full open-source DVR system with every feature under the sun. But it is not a Desktop-based App - it uses its own TV Remote friendly interface and runs under it's own sandboxed "mythtv" user account.

You may want to check out [http://linuxtv.org](http://linuxtv.org)

---

### Post by doyleman on 2010-11-22
thank you, asmoore. the device needs to read the red / yellow / white, because it isnt for tv, its for recording video games for Lets play, and to double the monitor as a tv screen.

I'm confused on what you mean v4l/2 drivers? I apologize. :(

---

### Post by doyleman on 2010-11-30
bump. are there no usb rca adapters that linux can read from?

---

### Post by no2498 on 2010-11-30
he needs help with s-video

---

### Post by doyleman on 2010-12-01
not s-video. rca.

here's the full details: a friend likes to play his PS2 and connect it to his computer monitor. he uses the linked device i gave in my first post, and some screen capture programs in Windows that lets him play.

He loves linux, too. Big reason for using windows is the fact it supports his device, easily. So we're wondering if there is an adapter similar to the one linked (rca to usb) that linux works with?

---

