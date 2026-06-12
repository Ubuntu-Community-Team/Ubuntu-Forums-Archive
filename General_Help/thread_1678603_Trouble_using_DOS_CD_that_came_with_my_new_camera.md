---
title: "Trouble using DOS CD that came with my new camera"
date: 2011-01-30
forum: General Help
---

### Post by wanderingarticfox on 2011-01-30
I just got a new Olympus FE-47 and the CD is in DOS as a PDF. I have not been able to figure out what program in 10.10 will open and auto run it. It does not auto run on start-up so I would appreciate any help. THX.

---

### Post by SaintDanBert on 2011-01-30
If you browse the CD and see "PDF files" what you have is a document
-- most likely the end-user manual -- for the camera.

insert the media into your optical drive.  You should get the choice to open the folder. Alternately, Copy the PDF onto a flash-drive or similar.

When you connect the flash-drive to linux, double-click on the PDF file.
A "default" reader should open revealing the document contents.
There are numerous pdf-reader packages -- including LibreOffice and OpenOffice -- that will show you the PDF contents if a default is not available.

Other contents on the CD are likely drivers for antique editions of MS-Windows(tm) or Apple Mac(tm). If you can use a USB cable and connect your camera to a workstation, you might not require specific drivers. Linux does a great job of usb storage accesses out of the box. If you want to use your camera as a web camera over usb, that might require some research to discover configuration details, but it just might work out-of-the box.

Cheers,
~~~ 0;-Dan

---

### Post by hawthornso23 on 2011-01-30
You may not need it. Mostly these days what is on those CDs is not essential for using the hardware. You'll find things like optional photo editing software and so on. Ubuntu has its own those software to do these things and already has drivers that will recognise most hardware.

My camera worked out of the box without the need to install anything. So try plugging it in and tell us what happens. If it doesn't work then ask for help in getting it working. This probably won't involve trying to run DOS software but will involve finding and installing the linux equivalents to do the same job.

---

### Post by SaintDanBert on 2011-01-31
> **hawthornso23 said:**
> 
...
This probably won't involve trying to run DOS software but will involve finding and installing the linux equivalents to do the same job.

There is a package called **dosemu** designed to enable running MS-DOS(tm) applications on Linux if that is what you really need to do.
Just as there is a package called **wine** designed to enable running MS-Windows(tm) applications on Linux if you really need that.

I agree with [highlight]hawthornso23[/highlight] that the CD contents are likely un-necessary ... except for the camera documents as PDF.
Open a terminal window and try this:
```

prompt$ #=== watch the system logs in real time
prompt$ tail -f /var/log/messages

```

Now connect your camera by USB cable and turn the camera on.
Everything (well almost) that the system does when it sees the USB device activate will appear in the log display.

If you are lucky, the system will recognize the on-camera storage as a external disk drive and ask you to decide how you want the contents displayed: open an application, open the drive folder, etc. **This is half your battle.**

The other half of your battle is using the camera as a web-cam or similar. Someone else here will need to walk you through that effort.
The log file contents will be important to that effort.

When you turn the camera off (still connected) the logs will display system efforts to unwrap the usb device. There might be additional details in those messages that will help getting the camera working.

Bonne chance,
~~~ 0;-Dan
will appear

---

### Post by wanderingarticfox on 2011-01-31
Hey, great info and suggestions. I did manage to download the User Manuel from the Olympus web-site. I plan to pick up an SD/SDHC card on Friday so I'll get to the plug and play and report back this weekend):P

---

### Post by SaintDanBert on 2011-01-31
> **wanderingarticfox said:**
> ... I plan to pick up an SD/SDHC card on Friday so I'll get to the plug and play and report back this weekend):P

I expect that Linux will see your camera+SDHC as if it were any other USB-connected drive or flash-media.

Oh, there is a connection
Here is your "device"
Dialog: what do you want me to do?
  Nothing?
  Open with XXX application?
  Open with [browse for application]?
  ...

Enjoy,
~~~ 0;-Dan

---

### Post by wanderingarticfox on 2011-02-03
I just picked up an SD/SDHC class 4 8 GB Sandisk card today so I will get back at this on Sat. an report. By the by Office man had this card for 20 buck thru the 5th for $20, what a deal!!!!!!!!!!!!!):P

---

### Post by wanderingarticfox on 2011-02-21
Yepper, Thx everyone was correct, I guess I just cannot get used to the power of Ubuntu:)

---

### Post by SaintDanBert on 2011-02-21
> **wanderingarticfox said:**
> Yepper, Thx everyone was correct, I guess I just cannot get used to the power of Ubuntu:)

Just a note -- If your laptop has a built-in media card reader for SD etc, there are known troubles with suspend-to {disk or ram}. If you have problems with suspend, you will need to unmount or eject the media before you request suspend-to-XXX.

Another note -- Should you have the SD card troubles, there is a way to automate the unmount. PM for the details.

Cheers,
~~~ 0;-Dan

---

### Post by wanderingarticfox on 2011-02-21
Desktop only, no card reader.

---

