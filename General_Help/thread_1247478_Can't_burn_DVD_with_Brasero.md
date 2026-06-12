---
title: "Can't burn DVD with Brasero"
date: 2009-08-23
forum: General Help
---

### Post by PoopyTheJ on 2009-08-23
When I try to burn this DVD using brasero it fails saying the image cannot be created, I'm attaching the relevan sections of the log file below, anyone have any ideas what's going on here and/or how to fix it? I'd really rather use ubutnu to burn but this is annoying as hell....

```
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_SOH4YU
	-exclude-list
	/tmp/brasero_tmp_7NH4YU
	-V
	Data disc (23 Aug 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/media/disk/Media/Programs/Petch/Pictures/Spector%20Euro%204%20002.jpg' and '/media/disk/Media/Programs/Petch/Pictures/Spector%20Euro%204%20002.jpg' have the same Rock Ridge name 'Spector%20Euro%204%20002.jpg'.
BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/media/disk/Media/Programs/Petch/Pictures/MS5%202.jpg' and '/media/disk/Media/Programs/Petch/Pictures/MS5%202.jpg' have the same Rock Ridge name 'MS5%202.jpg'.
BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/media/disk/Media/Programs/Petch/Pictures/Body%20front%20800.jpg' and '/media/disk/Media/Programs/Petch/Pictures/Body%20front%20800.jpg' have the same Rock Ridge name 'Body%20front%20800.jpg'.
BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/media/disk/Media/Programs/Petch/Pictures/Sadowsky%20RV4%2059B.jpg' and '/media/disk/Media/Programs/Petch/Pictures/Sadowsky%20RV4%2059B.jpg' have the same Rock Ridge name 'Sadowsky%20RV4%2059B.jpg'.
BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/media/disk/Media/Programs/Petch/Pictures/MV5%202.jpg' and '/media/disk/Media/Programs/Petch/Pictures/MV5%202.jpg' have the same Rock Ridge name 'MV5%202.jpg'.
BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/media/disk/Media/Programs/Petch/Pictures/Stick%20joy%202.jpg' and '/media/disk/Media/Programs/Petch/Pictures/Stick%20joy%202.jpg' have the same Rock Ridge name 'Stick%20joy%202.jpg'.
BraseroGenisoimage stderr: Unable to sort directory Petch/Pictures
BraseroGenisoimage called brasero_job_error
BraseroGenisoimage finished with an error
BraseroGenisoimage asked to stop because of an error
	error		= 13
	message	= "An image could not be created"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
Session error : An image could not be created (brasero_burn_record burn.c:2599)

```

---

### Post by cor2y on 2009-08-24
I would recommend you switch to k3b (less headaches) but if you still wish to use brasero disable the md5checksum plugin and then try again, i thought that bug was fixed a while back but i guess it has returned or maybe its new.

---

### Post by sahabcse on 2009-08-24
try K3b

---

### Post by PoopyTheJ on 2009-08-27
Thanks sorry took me forever to respond, how do I disable the Md5 plugin thingy?

---

### Post by sahabcse on 2009-08-28
Hi

Just skip the MD5 check. it just starts automatically, but you
do not have to wait for it to finish

---

