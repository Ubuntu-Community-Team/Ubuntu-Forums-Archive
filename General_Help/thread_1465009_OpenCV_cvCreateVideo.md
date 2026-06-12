---
title: "OpenCV cvCreateVideo"
date: 2010-04-29
forum: General Help
---

### Post by Mecasickle on 2010-04-29
Hey Guys, Sorry, for disrespecting author's rights, but I just found some guy on the web had the same problem as I did. So I'll basically just Ctrl+C Ctrol+V what he posted. I also find the need to Re-posting it here, becuase apparently this guy posted this on a yahoo forum, and he never got an answer. So...

----
Hi,
I am a beginner of openCV and am reading the book "Learning OpenCV Computer
Vision with the OpenCV Library".
One of the first examples in the book is about how to write to an avi file.
I basicly completely copied the code from the book and there are problems about
cvCreateVideo:

OpenCV ERROR: Unsupported format or combination of formats (Could not deduce
output format from file extension)
in function cvCreateVideoWriter, cvcap_ffmpeg.cpp(528)
Terminating the application...
called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...

I tried many different codec:

CV_FOURCC('P','I','M','1') = MPEG-1 codec
CV_FOURCC('M','J','P','G') = motion-jpeg codec (does not work well)
CV_FOURCC('M', 'P', '4', '2') = MPEG-4.2 codec
CV_FOURCC('D', 'I', 'V', '3') = MPEG-4.3 codec
CV_FOURCC('D', 'I', 'V', 'X') = MPEG-4 codec
CV_FOURCC('U', '2', '6', '3') = H263 codec
CV_FOURCC('I', '2', '6', '3') = H263I codec
CV_FOURCC('F', 'L', 'V', '1') = FLV1 codec

none of them work.
Is the problem caused by my laptop, or is it caused by my code?

my code is here:

#include "opencv/cv.h"
#include "opencv/highgui.h"




int main( int argc, char** argv)
{
CvCapture* capture=0;
cvNamedWindow("window");
capture = cvCreateFileCapture( argv[1] );
if(!capture){
return -1;
}
IplImage *bgr_frame= cvQueryFrame(capture);
double fps = cvGetCaptureProperty(capture, CV_CAP_PROP_FPS);
CvSize size = cvSize( (int)cvGetCaptureProperty(capture,
CV_CAP_PROP_FRAME_WIDTH),(int)cvGetCaptureProperty(capture,
CV_CAP_PROP_FRAME_HEIGHT));
CvVideoWriter* writer =
cvCreateVideoWriter(argv[2],CV_FOURCC('M','J','P','G'),fps,size,1);
IplImage* logpolar_frame = cvCreateImage(size,IPL_DEPTH_8U,3);

while((bgr_frame=cvQueryFrame(capture))!= NULL){
cvLogPolar( bgr_frame,
logpolar_frame,cvPoint2D32f(bgr_frame->width/2,bgr_frame->height/2),40,CV_INTER_\
LINEAR+CV_WARP_FILL_OUTLIERS);
cvWriteFrame( writer, logpolar_frame);
cvShowImage("window",logpolar_frame);
cvWaitKey(20);
}
cvReleaseVideoWriter( &writer);
cvReleaseImage(&logpolar_frame);
cvReleaseCapture(&capture);
return(0);
}


Thank you very much!!

-----

I'm encountering the exact same problem , could you guys please help me!?

Thanks in advance, Peace.

---

### Post by Mecasickle on 2010-04-30
BUmp.

---

### Post by rCXer on 2010-05-01
Have you tried the [opencv mailing list](http://tech.groups.yahoo.com/group/OpenCV/messages)?  They might be able to help if you don't find help here.

---

