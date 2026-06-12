---
title: "ehci samples error while running"
date: 2011-03-18
forum: General Help
---

### Post by niveditha on 2011-03-18
Hi,
i am a final year BE student. i am working on the ehci-0.6 library for tracking the the face in fedora 13 in vmware. i am able to compile the code but couldnot run the sample programs.i am facing the same program as posted by u.The error s as follows
 After I compile the program
cd ehci-0.6
./configure
make
I am able to do the above with out any errors. Later when try running samples
I am getting the below errors
cd samples 
make
./simple2d

(<unknown>:5940): GStreamer-CRITICAL **:
Trying to dispose element appsink1, but it is in READY instead of the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.
This problem may also be caused by a refcounting bug in the
application or some element.


(<unknown>:5940): GStreamer-CRITICAL **:
Trying to dispose element ffmpegcsp1, but it is in READY instead of the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.
This problem may also be caused by a refcounting bug in the
application or some element.



OpenCV Error: Unspecified error (unicap: failed to get info for device
) in CvCapture_Unicap::initDevice, file /builddir/build/BUILD/OpenCV-2.0.0/src/highgui/cvcap_unicap.cpp, line 139
terminate called after throwing an instance of 'cv::Exception'
Aborted (core dumped)



and but ven tried using  
./samples/simple2d 
the error i am facing is "couldnot initialise tha capturing"
can u please suggest me to overcome this kind of error.
blank window opens and goes on showing the error mentioned above and ends ven given ctrl + c.
the expected output to open a window and display the capture the person present in front of the webcam and print d coordinates of the face captured


If you need further more details I can provide you regarding the project and error.
Thanking you
niveditha

---

