---
title: "Arduino on 64bit 9.10"
date: 2009-11-20
forum: General Help
---

### Post by acidblue on 2009-11-20
Has anyone been able to get the arduino IDE to work correctly under
64bit Ubuntu 9.10?

I can get the IDE to start and compile but i can't get it to upload.
The ftdi chip dosn't seem to be recognized.
I've done "ls /dev/ttyUSB*" and get "No such file or directory".

Also doing "dmesg | tail" dosn't even list it.
I'm using the Arduino-0017 version which is the latest.
This worked under 9.04, but stopped working when I upgraded.
When the IDE starts I get this error:
WARNING:  RXTX Version mismatch
	Jar version = RXTX-2.2pre1
	native lib Version = RXTX-2.2pre2

and when i try to upload i get this one:
java.io.IOException: Cannot run program "/home/rocko/arduino-0017/hardware/tools/avrdude": java.io.IOException: error=2, No such file or directory
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:459)
	at java.lang.Runtime.exec(Runtime.java:593)
	at java.lang.Runtime.exec(Runtime.java:466)
	at processing.app.debug.Uploader.executeUploadCommand(Uploader.java:126)
	at processing.app.debug.AvrdudeUploader.avrdude(AvrdudeUploader.java:171)
	at processing.app.debug.AvrdudeUploader.uploadViaBootloader(AvrdudeUploader.java:81)
	at processing.app.debug.AvrdudeUploader.uploadUsingPreferences(AvrdudeUploader.java:53)
	at processing.app.Sketch.upload(Sketch.java:1460)
	at processing.app.Sketch.exportApplet(Sketch.java:1427)
	at processing.app.Sketch.exportApplet(Sketch.java:1382)
	at processing.app.Editor$45.run(Editor.java:2165)
	at java.lang.Thread.run(Thread.java:619)

BTW this all works under my Winbloze HD.
so it's not the board.
Please help I really don't want to use Winbloze.

---

### Post by bsatzinger on 2010-01-06
For your* java.io.IOException: Cannot run program "/home/rocko/arduino-0017/hardware/tools/avrdude": java.io.IOException: error=2, No such file or directory* error, a solution is to:

install avrdude with
*sudo apt-get install avrdude*

Then navigate to ~/arduino/hardware/tools
Rename the avrdude file to something else (or delete it)

Create a link to the avrdude you installed with apt-get earlier
*ln -s  /usr/bin/avrdude avrdude*

This solved the problem for me on 9.10 64 bit (AMD)

---

### Post by acidblue on 2010-04-17
I upgraded to Arduino 0018 version of the IDE and it works fine:)

---

