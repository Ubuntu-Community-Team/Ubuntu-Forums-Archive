---
title: "Motion: webcontrol_port working, streaming port not"
date: 2011-05-03
forum: General Help
---

### Post by wlraider70 on 2011-05-03
I've been hacking on motion for a while I ended up using

Motion trunk-r467 

Port localhost:8080 the control port is working i can change options.
The one cam i have streaming should be on 8081, but nothing seems to be there.

I've attached a picture that I found, its a mess...

I'm getting a log of stuff.
Any ideas?

```


May  3 14:43:00 hyrule motion: [1] - VIDEO_CAPTURE
May  3 14:43:00 hyrule motion: [1] - READWRITE
May  3 14:43:00 hyrule motion: [1] - STREAMING
May  3 14:43:00 hyrule motion: [1] v4l2_set_pix_format: Supported palettes:
May  3 14:43:00 hyrule motion: [1] 0: GRBG (GRBG)
May  3 14:43:00 hyrule motion: [1] v4l2_set_pix_format: 0 - GRBG (compressed : 0) (0x47425247)
May  3 14:43:00 hyrule motion: [1] v4l2_set_pix_format: Unable to find a compatible palette format.
May  3 14:43:00 hyrule motion: [1] v4l_start: Using VIDEO_PALETTE_YUV420P palette
May  3 14:43:00 hyrule motion: [1] vid_v4lx_start: Using V4L1
May  3 14:43:00 hyrule motion: [1] v4l_next: sync error in proc 1352:
May  3 14:43:01 hyrule motion: [1] v4l_next: mcapture error in proc 1352:
May  3 14:43:01 hyrule motion: [1] motion_loop: Video device fatal error - Closing video device
May  3 14:43:01 hyrule motion: [1] vid_close: Closing video device /dev/video0
May  3 14:43:10 hyrule motion: [1] motion_loop: Retrying until successful connection with camera
May  3 14:43:10 hyrule motion: [1] v4l2_get_capability: #012------------------------#012cap.driver: "STV06xx"#012cap.card: "Camera"#012cap.bus_info: "usb-0000:00:02.0-1"#012cap.capabilities=0x05000001#012------------------------
May  3 14:43:10 hyrule motion: [1] - VIDEO_CAPTURE
May  3 14:43:10 hyrule motion: [1] - READWRITE
May  3 14:43:10 hyrule motion: [1] - STREAMING
May  3 14:43:10 hyrule motion: [1] v4l2_set_pix_format: Supported palettes:
May  3 14:43:10 hyrule motion: [1] 0: GRBG (GRBG)
May  3 14:43:10 hyrule motion: [1] v4l2_set_pix_format: 0 - GRBG (compressed : 0) (0x47425247)
May  3 14:43:10 hyrule motion: [1] v4l2_set_pix_format: Unable to find a compatible palette format.
May  3 14:43:10 hyrule motion: [1] v4l_start: Using VIDEO_PALETTE_YUV420P palette
May  3 14:43:10 hyrule motion: [1] vid_v4lx_start: Using V4L1
May  3 14:43:10 hyrule motion: [1] v4l_next: sync error in proc 1352:
May  3 14:43:11 hyrule motion: [1] v4l_next: mcapture error in proc 1352:
May  3 14:43:11 hyrule motion: [1] motion_loop: Video device fatal error - Closing video device
May  3 14:43:11 hyrule motion: [1] vid_close: Closing video device /dev/video0
May  3 14:43:20 hyrule motion: [1] motion_loop: Retrying until successful connection with camera
May  3 14:43:20 hyrule motion: [1] v4l2_get_capability: #012------------------------#012cap.driver: "STV06xx"#012cap.card: "Camera"#012cap.bus_info: "usb-0000:00:02.0-1"#012cap.capabilities=0x05000001#012------------------------
May  3 14:43:20 hyrule motion: [1] - VIDEO_CAPTURE
May  3 14:43:20 hyrule motion: [1] - READWRITE
May  3 14:43:20 hyrule motion: [1] - STREAMING
May  3 14:43:20 hyrule motion: [1] v4l2_set_pix_format: Supported palettes:
May  3 14:43:20 hyrule motion: [1] 0: GRBG (GRBG)
May  3 14:43:20 hyrule motion: [1] v4l2_set_pix_format: 0 - GRBG (compressed : 0) (0x47425247)
May  3 14:43:20 hyrule motion: [1] v4l2_set_pix_format: Unable to find a compatible palette format.
May  3 14:43:20 hyrule motion: [1] v4l_start: Using VIDEO_PALETTE_YUV420P palette
May  3 14:43:20 hyrule motion: [1] vid_v4lx_start: Using V4L1
May  3 14:43:20 hyrule motion: [1] event_newfile: File of type 1 saved to: /usr/local/apache2/htdocs/cam1/03-20110503144320-00.jpg
May  3 14:43:20 hyrule motion: [1] v4l_next: sync error in proc 1352:
May  3 14:43:21 hyrule motion: [1] v4l_next: mcapture error in proc 1352:
May  3 14:43:21 hyrule motion: [1] motion_loop: Video device fatal error - Closing video device
May  3 14:43:21 hyrule motion: [1] vid_close: Closing video device /dev/video0


```

---

### Post by no2498 on 2011-05-04
have you ever had your cam working like in cheese 

to do this motion must be off

open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

### Post by wlraider70 on 2011-05-04
ill try that and report. I don't have a gui on the box will cheese work. Motion says in its documentation that it will.

---

### Post by jvin248 on 2011-06-19
gstreamer-properties works with both /dev/video0 and /dev/video1 devices (usb logitech cameras).
cheese works with one (didn't see how to change from one to the other camera)

Motion doesn't see either on the web link.
gray screen with 'unable to open video device'

---

