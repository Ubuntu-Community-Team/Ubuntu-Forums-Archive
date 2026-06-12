---
title: "Unable to retrieve the local discovery mode"
date: 2010-01-20
forum: General Help
---

### Post by smuwanga on 2010-01-20
Dear Ubuntu Community, I have just switched to ubuntu 9.04, from openSuse. 

Am programming with bluetooth. I get the following error.
-------------------------------------------------------------------------------------------------------------------
[I]Can't initialize bluetooth: 
java.lang.RuntimeException: Unable to retrieve the local discovery mode.
    at com.intel.bluetooth.BluetoothStackBlueZ.nativeGetLocalDeviceDiscoverable(Native Method)
    at com.intel.bluetooth.BluetoothStackBlueZ.getLocalDeviceDiscoverable(BluetoothStackBlueZ.java:273)
    at com.intel.bluetooth.BluetoothStackBlueZ.setLocalDeviceDiscoverable(BluetoothStackBlueZ.java:287)
    at javax.bluetooth.LocalDevice.setDiscoverable(LocalDevice.java:206)[/I]
----------------------------------------------------------------------------------------------------------

Any work-around? 

Thanking you,
Simon.

---

### Post by amsterdamharu on 2010-01-20
Could this be a bluecove problem not specific to Ubuntu? It is for sure some Java setting if it used to work in opensuze.

[http://code.google.com/p/bluecove/issues/detail?id=59](http://code.google.com/p/bluecove/issues/detail?id=59)

"This fixed is applied to 2.1.1-SNAPSHOT.48 or later, Should be created on June 14 2009"

---

### Post by smuwanga on 2010-01-25
Thank you amsterdamharu .

I visited that link, and I had to download the snapshot jars. I placed then into the main path, thats by using export BLUE_COVE=/path/to/directory/with/snapshot jars
By the way, ensure that the directory doesn't have any other bluetooth jars. Otherwise there will be a conflict when loading the bluetooth libraries.

Also,
I added the individual snapshot jars to the build path of my project. This made the error to disappear completely.

Another issue pops up,
As soon as the phone's j2me application starts transferring data with the server(my laptop), the bluetooth icon on the laptop disappears, and the connection breaks. It used to work well with the opensuse linux.

Whats missing to get the bluetooth working very well?

Thanking you,
Simon.

---

### Post by amsterdamharu on 2010-01-25
I am wondering why it worked on openSuze, the link I posted can give some suggestions as to why it currently doesn't work:

"Works fine with bluez 3" So your jars are too new? That way you can use the older jar and see if that one runs more stable
Maybe the kernel is too new and an older one you used under openSuze might do a better job.


Is there any output from Java or the bluetooth applet? (maybe somewhere under /var/log/)

---

