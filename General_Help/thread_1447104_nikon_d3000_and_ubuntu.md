---
title: "nikon d3000 and ubuntu"
date: 2010-04-04
forum: General Help
---

### Post by oleink on 2010-04-04
Hey,
I have a nikon d3000 and when i plugged it into the usb port it recognized a device but said it could not find the camera.  I'm not entirely sure what I should do...  Help greatly appreciated!

---

### Post by oleink on 2010-04-09
thanks for your responses haha.:KS

---

### Post by The Thunder Chimp on 2010-04-09
I have a Nikon D200. I'll check it out. Let you know if it works.

---

### Post by oleink on 2010-04-09
Ok thanks!

---

### Post by The Thunder Chimp on 2010-04-09
It's out of batteries. I'll have to charge it first. But from what I can see on the camera, you might be able to hook it up by changing the camera mode. (This is a 2005 model by the way). If possible, you might want to take the memory card out and put it in the computer (just saying, even though you probably thought of that). So I'll charge it and get back to you.:)

---

### Post by oleink on 2010-04-09
I just figured out a way that worked.  I shoot in raw (since jpeg on the d3000 is kind of bad compared to their other cameras sadly.)  Instead of using the software to extract the pictures I can use rawstudio or set it to be viewed as a folder.  Thanks

PS I need to upgrade to like the d5000.  Raw photos take too much space and jpeg conversion takes too much time haha.  The d5000 is now at the price I got my camera for and its quality is very very very close to the d90.  For hundred less that is a good camera.  Cheers!

---

### Post by The Thunder Chimp on 2010-04-09
The USB cable could be important too. Try to use the one that came with the camera. But from what I've read, you've solved the problem right?

---

### Post by The Thunder Chimp on 2010-04-09
> **oleink said:**
> PS I need to upgrade to like the d5000.  Raw photos take too much space and jpeg conversion takes too much time haha.  The d5000 is now at the price I got my camera for and its quality is very very very close to the d90.  For hundred less that is a good camera.  Cheers!

What about a larger card?

---

### Post by oleink on 2010-04-09
The upgrade wouldn't be for the amount of space the pictures take up on the card but on my computer's hard drive.  If it were just the card I'd gladly just upgrade that.

PS yep solved it thanks for your help!

---

### Post by The Thunder Chimp on 2010-04-11
> **oleink said:**
> The upgrade wouldn't be for the amount of space the pictures take up on the card but on my computer's hard drive.  If it were just the card I'd gladly just upgrade that.

What about purchasing an external hard drive? Or what about you shoot your pictures in RAW, and then use a picture manager (such as the gimp), to compress them at the level of quality you desire? I'm just saying that there is a load if inexpensive alternatives to the solution you have in mind. Then again, if you wish for a new camera just for the sake of a new camera, then by all means my friend, go for it!

---

### Post by thunderdan on 2010-05-24
I seem to have a similar problem. I have a D3000 and when I plug it in with the USB, it doesn't pop up on my desktop like a mass storage device. But it did once. I don't know what the difference is between the time it worked and all the other times that it doesn't work. I'm using Lucid. lsusb -v shows this:
```
Bus 001 Device 015: ID 04b0:0424 Nikon Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04b0 Nikon Corp.
  idProduct          0x0424 
  bcdDevice            1.00
  iManufacturer           1 NIKON
  iProduct                2 NIKON DSC D3000
  iSerial                 3 000003341829
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         6 Imaging
      bInterfaceSubClass      1 Still Image Capture
      bInterfaceProtocol      1 Picture Transfer Protocol (PIMA 15470)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               9
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```
It's kind of perplexing to me. I tried using F-Spot to import the photos, and I clicked the import button. The "Import source" drop-down menu shows "Nikon DSC D3000 (PTP mode)" and I choose it, then I get the message "Error connecting to camera, Received error 'Could not lock the device' while connecting to camera."

I tried using Rawstudio as suggested above, but I usually don't shoot in RAW, and Rawstudio can't get to the directory on the camera's memory card anyway, because it's not showing up as a mass storage device.

I have tried three USB cables. I have duplicated the results described above on a separate computer, also running Lucid. Other cameras I connect with a USB cable show up as mass storage devices on the desktop.

Now if I had to guess, I think there might be something significant in that "PTP mode," but I'm not sure.

I saw this thread: [http://ubuntuforums.org/showthread.php?p=2279356&mode=linear#post2279356](http://ubuntuforums.org/showthread.php?p=2279356&mode=linear#post2279356) but the D3000 does not seem to have a menu item to switch from PTP to USB mode. Also, I tried this:

```
daniel@daniel-desktop:~$ gksudo f-spot
** No session dbus found. Starting one **
[Info  01:12:37.030] Initializing DBus
[Info  01:12:37.226] Initializing Mono.Addins
[Info  01:12:37.451] Starting new FSpot server (f-spot 0.6.1.5)
[Info  01:12:38.468] Starting BeagleService
[Info  01:12:38.493] Hack for gnome-settings-daemon engaged

(f-spot:4444): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
item ImportCommand+SourceItem
Error Lock: LibGPhoto2.GPhotoException: Could not lock the device
  at LibGPhoto2.Error.CheckError (ErrorCode error) [0x00000] 
  at LibGPhoto2.Camera.Init (LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.InitializeCamera () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
cleanup context

(f-spot:4444): Gdk-WARNING **: losing last reference to undestroyed window

[Info  01:12:54.737] Exiting
cleanup context
cleanup context

```

So I seem to have run into a brick wall. Any ideas or suggestions are greatly appreciated.

Thanks,

---

### Post by BobvanderPoel on 2010-05-24
This is a "ME TOO". Exact same problem!

And, no it's not the USB cable.

And, no it's not the camera mode (can't change it on the D3000).

And, YES, this worked perfectly before I "upgraded" to lucid. Previously ubunutu karmic worked just dandy.

I have no idea ... but I'm wondering if this is a group permission problem???? 

Someone must have an answer.

BTW, pulling the card from the camera and reading that in a card reader works just fine. Just that the camera can't be read (it is seen) in PTP mode.

---

### Post by thunderdan on 2010-05-24
> **BobvanderPoel said:**
> This is a "ME TOO". Exact same problem!

And, no it's not the USB cable.

And, no it's not the camera mode (can't change it on the D3000).

And, YES, this worked perfectly before I "upgraded" to lucid. Previously ubunutu karmic worked just dandy.

I have no idea ... but I'm wondering if this is a group permission problem???? 

Someone must have an answer.

BTW, pulling the card from the camera and reading that in a card reader works just fine. Just that the camera can't be read (it is seen) in PTP mode.

I might have found a work-around. If I restart my computer and then attach the camera via USB cable, I am able to transfer photos with F-Spot. But if the computer has been running for a little while, and I have started other programs, it becomes unable to transfer. So you might try restarting and transferring before running any other programs. It's kind of a hassle, but I'm happy to just be able to transfer the photos. Does that work for you?

---

### Post by BobvanderPoel on 2010-05-24
No that doesn't work. But, I do have a partial solution. And, it makes no sense.

Using digikam (I've not tried with fspot, but it's probably the same) I can do perfect importing under the xfce and kde4 desktops. Perfect! No problems.

But, logging out and going back to gnome I get the same error.

Anyone?

---

### Post by BobvanderPoel on 2010-05-24
No that doesn't work. But, I do have a partial solution. And, it makes no sense.

Using digikam (I've not tried with fspot, but it's probably the same) I can do perfect importing under the xfce and kde4 desktops. Perfect! No problems.

But, logging out and going back to gnome I get the same error.

Just had an idea ... I'd removed the startup application "HAL" from my system->prefs->startup-apps. So, re-enabled, logged out and tried again. Nope, that isn't it either.

Anyone?

---

### Post by BobvanderPoel on 2010-05-24
Okay, this is really quite silly. 

Just logged out of my gnome session and started up xfce again. Note: I did not reboot the computer or X. And, I have compiz running in both the gnome and xfce sessions (not that that should be effecting things).

Under xfce digikam, fspot and gfphotofs all work just fine. 

Under gnome none work.

---

### Post by BobvanderPoel on 2010-05-25
Okay ... got half a solution.

It appears that when the camera in plugged in gnome "helpfully" mounts the camera as a usb device. If you bring up Nautilus you'll see the camera as a "place". Clicking on that you can un-mount the camera. Now, digikam, etc will work fine.

The half I don't see (I'm old and it's late) is how to prevent the auto-mount in the future. Ideas?

---

### Post by BobvanderPoel on 2010-05-26
I tired natalius->edit->peferences->media and set all the options to "do nothing". Tired the camera again, same problem ... still mounting. Log out/in. No better.

Gconf -> apps->nautalus->prefs->media-automount <uncheck>

Log out/in and now it works.

Gawd, way too complicated. I think something is broken in gnome (but KDE4 has some many bugs, etc. I'll stick with it ...). Why does newer, better, etc mean "things which worked just fine now are broken"?

If someone has a simpler solution, please let me know!

---

### Post by joopie18 on 2011-08-30
Worked for me on 10.04:

1. unmount the camera. 
2. start digikam. 

import pictures.
sweet

---

