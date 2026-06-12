---
title: "Redirect Serial Port communication non intrusively"
date: 2010-07-15
forum: General Help
---

### Post by kachofool on 2010-07-15
Hey all,

I'm trying to use a USB-to-Serial cable to talk to a device. No matter what I do, I can't get a response from the device -- I've used several programs, including coding my own test apps and nothing works, except for *one* program. I'm trying to figure out what I'm doing wrong... since I've used a bunch of programs to try this out I think it's the message or serial port settings that I'm screwing up.

I want to monitor the serial port to see exactly whats being transmitted both ways... but if I open up a serial port monitor applications (like cutecom, for example), that *one* program that works, doesn't work anymore (ie. I can't run them concurrently). Is there anyway I can just clone whats being sent to /dev/ttyUSB* to a logfile or something nonintrusively so that original program doesn't stop working?

---

### Post by kachofool on 2010-07-17
I wanted to follow up on this.

I'm using an FTDI USB->Serial converter. Here's the dmesg output when I connect the device (seems fine)

```

[ 3019.856077] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 3020.063217] ftdi_sio 4-1:1.0: FTDI USB Serial Device converter detected
[ 3020.063286] usb 4-1: Detected FT232RL
[ 3020.063292] usb 4-1: Number of endpoints 2
[ 3020.063298] usb 4-1: Endpoint 1 MaxPacketSize 64
[ 3020.063304] usb 4-1: Endpoint 2 MaxPacketSize 64
[ 3020.063309] usb 4-1: Setting MaxPacketSize 64
[ 3020.064425] usb 4-1: FTDI USB Serial Device converter now attached to ttyUSB0
```

To recap, I can't talk to my device at all. *If I open up a serial port monitor and try to send something to the device, I can't even see that I've sent the data.* However, if I use this other program (uses Java's serial port library) I can see what I'm sending the device.

At this point I'm at a loss. I saw this update in the linux kernel changelog

[I]
Author: Daniel Mack <daniel@caiaq.de>
Date:   Thu Jun 3 13:55:02 2010 +0200

    USB: ftdi_sio: fix DTR/RTS line modes
    
    commit 6a1a82df91fa0eb1cc76069a9efe5714d087eccd upstream.
    
    Call set_mctrl() and clear_mctrl() according to the flow control mode
    selected. This makes serial communication for FT232 connected devices
    work when CRTSCTS is not set.
    
    This fixes a regression introduced by 4175f3e31 ("tty_port: If we are
    opened non blocking we still need to raise the carrier"). This patch
    calls the low-level driver's dtr_rts() function which consequently sets
    TIOCM_DTR | TIOCM_RTS. A later call to set_termios() without CRTSCTS in
    cflags, however, does not reset these bits, and so data is not actually
    sent out on the serial wire.
    
    Signed-off-by: Daniel Mack <daniel@caiaq.de>
    Cc: Johan Hovold <jhovold@gmail.com>
    Cc: Alan Cox <alan@linux.intel.com>
    Signed-off-by: Greg Kroah-Hartman <gregkh@suse.de>

[/I]

So I tried updating the kernel (I'm on Lynx, now with the latest kernel from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). Everything went well, but I still have the same problem... I don't know if the problem was related to the kernel commit, or if updating to the new kernel even changed anything.

If anyone has any ideas or anything, please reply!

---

